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

All the same rules for engine format and version apply.

```
cfconfig transfer from=/path/to/.CFConfig.json to=/path/to/server/home toFormat=luceeServer@5.1
```

The version number can be left off `toFormat` and `fromFormat` when reading or writing to a CFConfig JSON file or a CommandBox server since we already know the
version.  If you don't specify a Lucee web or Server context, we default to server. Use a format of `luceeWeb` to switch.