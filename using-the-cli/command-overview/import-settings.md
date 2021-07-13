# Import Settings

Import configuration to a server. If you don't specify a to, we look for a CommandBox server using the current working directory. Only rely on this if you have a single CommandBox server running in the current directory.

```text
cfconfig import myConfig.json
cfconfig import to=serverName from=myConfig.json
cfconfig import to=/path/to/server/home from=myConfig.json
```

All the same rules for engine format and version apply.

```text
cfconfig import from=/path/to/.CFConfig.json to=/path/to/server/home toFormat=luceeServer@5.1
```

The version number can be left off `toFormat` and `fromFormat` when reading or writing to a CFConfig JSON file or a CommandBox server since we already know the version. If you don't specify a Lucee web or Server context, we default to server. Use a format of `luceeWeb` to switch.

```text
cfconfig import from=myConfig.json toFormat=luceeWeb
```

### IncludeList and excludeList

You can customize what config settings are transferred with the includeList and excludeList params. If at least one include pattern is provided, ONLY matching settings will be included. Nested keys such as datasources.myDSN or mailservers\[1\] can be used. You may also use basic wildcards in your pattern. A single  _will match any number of chars inside a key name. A double \*_ will match any number of nested keys.

```bash
# Include all settings starting with "event"
cfconfig import from=.CFConfig.json includeList=event*
# Exclude all keys called "password" regardless of what struct they are in
cfconfig import from=.CFConfig.json excludeList=**.password
```

### Append flag

Use the append parameter to merge incoming data with any data already present. For example, if a server already has one datasource defined and you import a JSON file with 2 more unique datasources, the --append flag will not remove the pre-existing one.

```bash
cfconfig import from=.CFConfig.json includeList=datasources --append
```

