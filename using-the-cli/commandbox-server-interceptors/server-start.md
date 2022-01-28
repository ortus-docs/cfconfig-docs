# Server Start

Every time a server starts, CFConfig will load configuration into your server by convention. For Lucee servers, settings go in the server context by default. Since each CommandBox Lucee server only has a single web context, the differentiation is mostly moot.

## Import from JSON file

CFConfig will attempt to locate a JSON file containing exported server configuration. If it finds a JSON file, it will import it into the starting server as it comes up.

Here are the locations CFConfig will look for a JSON file and the order it will look for them in. After CFConfig files a JSON file in one location, it stops looking.

### Environment Variable

If an environment variable exists with the name `CFConfigFile`, `CFConfigWeb`, or `CFConfigServer` it will be used as an absolute path to the JSON file or a relative path in relation to the web root.. An example of setting this in Windows would be:

```text
C:/> SETX cfconfigfile "C:/path/to/myConfig.json"
C:/> SETX cfconfigweb "C:/path/to/myConfig-web.json"
C:/> SETX cfconfigserver "C:/path/to/myConfig-server.json"
```

And on Unix...

```text
$> cfconfigfile=C:/path/to/myConfig.json
$> cfconfigweb=C:/path/to/myConfig-web.json
$> cfconfigserver=C:/path/to/myConfig-server.json
$> export cfconfigfile
$> export cfconfigweb
$> export cfconfigserver
```

_Note: CommandBox won't pick up new environment variables in Windows until you close and reopen the shell._

It's not necessary to use `cfconfigfile` and `cfconfigsever` at the same time since they do the same thing.  They are both provided for consistency.  If you use both, they will all be imported!

Technically, you can also use one of the following env vars to do the same thing since CommandBox supports a generic syntax to override any `server.json` property, but given the options above, it's not necessary to use these unless you want to or specifically want to override the settings in the `server.json`.

```bash
box_server_cfconfig_file=settings.json
box_server_cfconfig_web=settings.json
box_server_cfconfig_server=settings.json
```

### `server.json` properties

If there is a `CFConfig` property in your `server.json` file, it will be used to help control how your JSON configs are imported.  All JSON file paths can be absolute or relative paths from the folder the `server.json` lives in.

```javascript
"cfconfig" : {
   // Single JSON file to import into Adobe or the Lucee server context
   "file" : "path/to/file.json",
   // Same as "file" but for consistency with Lucee
   "server" : "path/to/file.json",
   // Will load into lucee/railo web context
   "web" : "path/to/file.json",
   // Import scheduled tasks as paused
   "pauseTasks" : true
},
// Backwards compat fallback
"CFConfigFile" : "path/to/file.json"
"CFConfigPauseTasks": true
```

Note, you would never need to use all the properties above at the same time.  The two top level ones are only supported for backwards compatibility.  For an Adobe server, or a Lucee server in which you only care about importing settings into the server context, you can just use `cfconfig.file` .  For a Lucee server in which you want to import settings into the server AND web context, you can use `cfconfig.server` and `cfconfig.web`.

## Multiple JSON files

Since there are several overlapping conventions, it's possible to have more than one JSON file.  For example, you could have a `cfconfigfile` environment variable set as well as a `cfconfig.file` key in your `server.json`.  In this case, BOTH JSON files will be imported.  When there are two more more JSON files being imported into the same web or server context, the first file will be an overwrite as usual and all subsequent files will be imported in "append" mode so they add to the settings in the previous file. 

### `.cfconfig.json` File in Webroot

if and ONLY IF no other settings \(env vars, or `server.json` properties\) are found to specify a JSON file to import, CFConfig will look for the following files in the web root by convention.

* `.cfconfig.json` - Use this for Adobe or for Lucee's server context
* `.cfconfig-web.json` Use this for the Lucee web context
* `.cfconfig-server.json` Use this for the Lucee server context \(same as `.cfconfig.json` \)

If the only convention file found for an Adobe server is `.cfconfig-web.json` or `.cfconfig-server.json`, it will still be used but just imported into Adobe's single context.

## Set Individual Settings

If you don't want to have a full JSON file, but just want to set some ad-hoc settings, you can do this via environment variables. These will load regardless of whether a JSON file was imported so it gives you a chance to override specifics like passwords. Environment variables are also perfect for cloud environments and Docker images.

### Variable names

When a server starts up, all environment variables will be looped over, and all the ones that start with `cfconfig_` will be used. The naming format is `cfconfig_xxx` where `xxx` is the name of a valid config item such as `adminPassword` or `requestTimeout`.

Here's an example of what setting that up on Windows might look like:

```text
C:/> SETX cfconfig_adminPassword "myCoolPass123"
```

And on Unix...

```text
$> cfconfig_adminPassword=myCoolPass123
$> export cfconfig_adminPassword
```

Now, every time a CommandBox server is started on this machine, that password will be loaded in, even if a previous JSON import had another password.

If you want to target the web context for your settings, you can use the syntax `cfconfig_web_xxx` like so:

```bash
cfconfig_web_adminPassword=myPass
```

## Admin Passwords on Lucee

As a safety precaution, any time an `adminPassword` setting is present in an auto-imported JSON file or a `cfconfig_adminPassword` environment variable is set on a Lucee server, the server start interceptor will set that password into the web context as well as the default server context. This is to prevent a production server getting deployed with no password on the web context.

This only applies to the auto server start interceptors documented on this page. if you manually run a `cfconfig import` or `cfconfig set` command, it's up to you to also set things like passwords into the server and web contexts.

## Production Password Protection

On both Lucee and Adobe servers, when the server profile is set to `production`, CFConfig will not allow your sever to start with an empty password or with the Adobe default password of `commandbox`.  If any of those scenarios are detection in a `production` profile, CFConfig will set a random password and output it in the verbose console logs for you to refer to later.

