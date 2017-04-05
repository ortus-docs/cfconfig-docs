# CFConfig CLI Usage

## Specifying a server

There are 3 ways that CFConfig will determine the server(s) you would like it to operate on.  Each command has a `to` and/or `from` parameter to specify this.

1. The current working directory if it is the web root for a CommandBox server.
2. You provide the name of a previously-started CommandBox server
3) You provide a file path to the CF home of the server


### Lucee 4/5 web CF home
The folder containing the `lucee-web.xml.cfm` file.
An example would be:

```
<webroot>/WEB-INF/lucee/
```

### Lucee 4/5 server CF home
Path to be the `lucee-server` folder containing the `/context/lucee-server.xml` file.
An example would be:

```
/opt/lucee/lib/lucee-server/
```

### Adobe 9/10/11/2016 CF home
The `cfusion` folder that contains the `lib/neo-runtime.xml` file.
An example would be:

```
C:/ColdFusion11/cfusion/
```

## Specifying the server format (version)
