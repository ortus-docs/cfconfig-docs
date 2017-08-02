# Server Start

Every time a server starts, CFConfig will load configuration into your server by convention. 

## Import from JSON file

CFConfig will attempt to locate a JSON file containing exported server configuration. If it finds a JSON file, it will import it into the starting server as it comes up.  

Here are the locations CFConfig will look for a JSON file and the order it will look for them in.  After CFConfig files a JSON file in one location, it stops looking.

### Environment Variable

If an environment variable exists with the name `CFConfigFile`, it will be used as an absolute path to the JSON file.  An example of setting this in Windows would be:

```
C:/> SETX cfconfigfile "C:/path/to/myConfig.json"
```

### server.json property

A `CFConfigFile` property in your `server.json` file that contains an absolute path or a path that is relative to the `server.json` file.

