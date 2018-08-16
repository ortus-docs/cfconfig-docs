# Server Start

Every time a server starts, CFConfig will load configuration into your server by convention. For Lucee servers, settings go in the server context by default. Since each CommandBox Lucee server only has a single web context, the differentiation is mostly moot.

## Import from JSON file

CFConfig will attempt to locate a JSON file containing exported server configuration. If it finds a JSON file, it will import it into the starting server as it comes up.

Here are the locations CFConfig will look for a JSON file and the order it will look for them in. After CFConfig files a JSON file in one location, it stops looking.

### Environment Variable

If an environment variable exists with the name `CFConfigFile`, it will be used as an absolute path to the JSON file. An example of setting this in Windows would be:

```text
C:/> SETX cfconfigfile "C:/path/to/myConfig.json"
```

And on Unix...

```text
$> cfconfigfile=C:/path/to/myConfig.json
$> export cfconfigfile
```

_Note: CommandBox won't pick up new environment variables in Windows until you close and reopen the shell._

### `server.json` property

If there is a `CFConfigFile` property in your `server.json` file, it will be used. It can contain an absolute path or a path that is relative to the `server.json` file.

```javascript
{
  "cfconfigfile" : "C:/path/to/myConfig.json",
  // or 
  "cfconfigfile" : "../workbench/myConfig.json"
}
```

### `.cfconfig.json` File in Webroot

If there is a file in the web root called `.cfconfig.json`, it will be used. Note the file starts with a period \(`.`\). This is so web servers like Apache won't service the file by default since it's "hidden". Note this is the easiest approach, but probably the least secure. We recommend it just for development purposes.

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

Note, this approach is only suitable for simple settings. If you want to add datasources, CF mappings, etc you'd need to use a full JSON file import.

## Admin Passwords on Lucee

As a safety precaution, any time an `adminPassword` setting is present in an auto-imported JSON file or a `cfconfig_adminPassword` environment variable is set on a Lucee server, the server start interceptor will set that password into the web context as well as the default server context. This is to prevent a production server getting deployed with no password on the web context.

This only applies to the auto server start interceptors documented on this page. if you manually run a `cfconfig import` or `cfconfig set` command, it's up to you to also set things like passwords into the server and web contexts.

