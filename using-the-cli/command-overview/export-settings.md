# Export Settings

Export configuration from a server. If you don't specify a to, we look for a CommandBox server using the current working directory. Only rely on this if you have a single CommandBox server running in the current directory.

```text
cfconfig export myConfig.json
cfconfig export from=serverNameToExportFrom to=myconfig.json
cfconfig export from=/path/to/server/home to=myconfig.json
```

All the same rules for engine format and version apply.

```text
cfconfig export to=/path/to/.CFConfig.json from=/path/to/server/home fromFormat=luceeServer@5.1
```

The version number can be left off `toFormat` and `fromFormat` when reading or writing to a CFConfig JSON file or a CommandBox server since we already know the version. If you don't specify a Lucee web or Server context, we default to server. Use a format of "luceeWeb" to switch.

```text
cfconfig export to=myConfig.json fromFormat=luceeWeb
```

In some situations you might need to alter the data being imported such as with Scheduled Tasks that you might not want to run on the target server. Adding the `--pauseTasks` flag will import the scheduled tasks in the paused state.

