# Usage

## Specifying a Server Home

CFConfig must determine the server(s) on which to operate, which will either be a web context or a server context. CFConfig will determine the server as follows:

1. By default, when the `to` or `from` parameters are not present, CFConfig will use the current working directory, assuming it is the web root for an Embedded Commandbox Server (see below)
2. You provide a file path to the server home by using the `to` and/or `from` parameters
3. You provide the name of a previously-started CommandBox server, using `to` and/or `from` parameters  (see [Commandbox Managing Servers](https://commandbox.ortusbooks.com/embedded-server/manage-servers))

### Lucee 4/5 Web Context

The folder containing the `lucee-web.xml.cfm` file. An example would be:

```
<webroot>C:/myapp/WEB-INF/lucee/

cfconfig export from=C:/myapp/WEB-INF/lucee/ to=myconfig.json
```

### Lucee 4/5 Server Context

Path to the `lucee-server` folder containing the `/context/lucee-server.xml` file. An example would be:

```
C:/lucee/tomcat/lucee-server/

cfconfig export from=C:/lucee/tomcat/lucee-server/ to=myconfig.json
```

### Adobe 9/10/11/2016/2018 CF home

The `cfusion` folder that contains the `lib/neo-runtime.xml` file. An example would be:

```
C:/ColdFusion11/cfusion/
```

### JSON File

Just provide the path to the JSON file. This is auto-detected if the path ends in `.JSON`. An example would be:

```
C:/path/to/myConfig.json
```

## Server Format (engine/version)

Every command with a `to` and/or `from` parameter also has a matching `toFormat and/or`fromFormat\` parameter. In most cases, you don't need to provide this. If you are pointing to an existing CommandBox server, or typical server installation, CFConfig will examine the files in the CF home to determine what engine and version it is. However, if you are writing files to an empty or non-existent directory, you'll need to tell CFConfig what format to write them in.

Format is specified as `engine@version` where:

* `engine` is the name of the CF engine
* `version` is a semantic version number representing the engine version

Possible engine values are:

* **luceeWeb** - Lucee web context
* **luceeServer** - Lucee server context (Default for Lucee servers)
* **adobe** - Adobe server
* **railoWeb** - Railo web Context
* **railoServer** - Railo server context

Here are some examples of server formats:

* adobe@10
* adobe@11.0.10
* luceeServer@5
* luceeWeb@4.5

### Embedded Commandbox Server

If you run CFConfig from the web root of a Commandbox embedded server, you do not need to specicy the `from` or `to` parameters to reference it, and CFConfig will automatically default to the `luceeServer` format, which operates on the server context. If you wish to interact with the web context (which has little distinction in a CommandBox server since there's only one web context per server) you will need to provide the explicit `luceeWeb` format by using either the `toFormat` or `fromFormat` parameters.

```
cfconfig show fromFormat=luceeWeb
```

This example assumes you are running CFConfig from the web root of an embedded server:

```
cfconfig import from=config_admin.json toFormat=luceeWeb
```

## ModCFML and Web Contexts

When using ModCFML is enabled, Lucee can have more than one web context. When using the `fromFormat` or `toFormat` of `luceeWeb`, you will be interacting with the Lucee web context associated with the default web root.  To interact with a specific Lucee web context, specify the web root in the format name like so:

```bash
cfconfig export fromFormat=luceeWeb-/path/to/webroot/site1 to=.cfconfig-web-site1.json
cfconfig export fromFormat=luceeWeb-/path/to/webroot/site2 to=.cfconfig-web-site2.json
```
