# Usage

## Server Home

There are 3 ways that CFConfig will determine the server\(s\) you would like it to operate on. Each command has a `to` and/or `from` parameter to specify this.

1. The current working directory if it is the web root for a CommandBox server.
2. You provide the name of a previously-started CommandBox server
3. You provide a file path to the CF home of the server

### Lucee 4/5 web CF home

The folder containing the `lucee-web.xml.cfm` file. An example would be:

```text
<webroot>/WEB-INF/lucee/
```

### Lucee 4/5 server CF home

Path to be the `lucee-server` folder containing the `/context/lucee-server.xml` file. An example would be:

```text
/opt/lucee/lib/lucee-server/
```

### Adobe 9/10/11/2016/2018 CF home

The `cfusion` folder that contains the `lib/neo-runtime.xml` file. An example would be:

```text
C:/ColdFusion11/cfusion/
```

### JSON File

Just provide the path to the JSON file. This is auto-deteced if the path ends in `.JSON`. An example would be:

```text
C:/path/to/myConfig.json
```

## Server Format \(engine/version\)

Every command with a `to` and/or `from` parameter also has a matching `toFormat and/or`fromFormat\` parameter. In most cases, you don't need to provide this. If you are pointing to an existing CommandBox server, or typical server installation, CFConfig will examine the files in the CF home to determine what engine and version it is. However, if you are writing files to an empty or non-existent directory, you'll need to tell CFConfig what format to write them in.

Format is specified as `engine@version` where:

* `engine` is the name of the CF engine
* `version` is a semantic version number representing the engine version

Possible engine values are:

* **luceeWeb** - Lucee web context
* **luceeServer** - Lucee server context \(Default for Lucee servers\)
* **adobe** - Adobe server
* **railoWeb** - Railo web Context
* **railoServer** - Railo server context

Here are some examples of server formats:

* adobe@10
* adobe@11.0.10
* luceeServer@5
* luceeWeb@4.5

## Default format for Lucee

If you are interacting with a Lucee CommandBox server and don't provide a format, CommandBox will automatically default to the `luceeServer` format which operates on the server context. If you wish to interact with the web context \(which has little distinction in a CommandBox server since there's only one web context per server\) you will need to provide the explicit `luceeWeb` format.

```text
cfconfig show fromFormat=luceeWeb
```

