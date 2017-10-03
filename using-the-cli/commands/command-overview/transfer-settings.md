# Transfer Config between servers

Transfer configuration from one location/server to another.  If you don't specify a from or to, we look for a CommandBox server using the current working directory.  Only rely on this if you have a single CommandBox server running in the current directory.  You must specify at least a `from` or a `to`.

Note the two servers do not need to be the same kind. CFConfig will translate the config for you.

```
cfconfig transfer from=servername to=anotherServername
cfconfig transfer from=serverName
cfconfig transfer to=serverName
cfconfig transfer from=/path/to/server/home to=/path/to/another/server/home
cfconfig transfer from=/path/to/server/home
cfconfig transfer to=/path/to/server/home
```

When transfering configuration to or from a generic CFConfig JSON file, use the full path to the JSON file:

```
cfconfig transfer from=/path/to/.cfconfig.json
cfconfig transfer to=/path/to/.cfconfig.json
```

For CommandBox servers, we'll get the engine/version out of CommandBox's metadata.  For non-CommandBox servers, you'll need to help me out by
specifying what kind of file format to use.
For the fromFormat and toFormat, use the name of the engine followed by @ and then the engine version like engine@version.
For lucee, specify the web or sever context.  Valid engines are "luceeWeb", "luceeServer", and "adobe".
For partial versions, the missing pieces will be interpreted as zeros.  Meaning adobe@11 is the same as adobe@11.0.0.
Examples are:
- adobe@11.0.11
- luceeWeb@5
- luceeServer@4.5

cfconfig transfer from=/path/to/.CFConfig.json to=/path/to/server/home toFormat=luceeServer@5.1

The version number can be left off toFormat and fromFormat when reading or writing to a CFConfig JSON file or a CommandBox server since we already know the
version.
If you don't specify a Lucee web or Server context, we default to server. Use a format of "luceeWeb" to switch.