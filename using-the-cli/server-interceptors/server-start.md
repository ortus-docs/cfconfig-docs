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

_Note: CommandBox won't pick up new environment variables in Windows until you close and reopen the shell._

### `server.json` property

If there is a `CFConfigFile` property in your `server.json` file, it will be used.  It can contain an absolute path or a path that is relative to the `server.json` file.
```js
{
  "cfconfigfile" : "C:/path/to/myConfig.json",
  // or 
  "cfconfigfile" : "../workbench/myConfig.json"
}
```

### `.cfconfig.json` File in Webroot


If there is a file in the web root called `.cfconfig.json`, it will be used.  Note the file starts with a period (`.`).  This is so web servers like Apache won't service the file by default since it's "hidden".  Note this is the easiest approach, but probably the least secure.  We recommend it just for development purposes.
