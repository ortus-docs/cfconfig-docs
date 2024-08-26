# Manage Lucee Loggers

## List all Lucee Loggers

```text
cfconfig logger list
cfconfig logger list from=serverName
cfconfig logger list from=/path/to/server/home
```

To receive the data back as JSON, use the `--JSON` flag.

```text
cfconfig logger list --JSON
```

## Add or update a Lucee Logger

```text
cfconfig logger save name=application appender=resource appenderArguments:path={lucee-config}/logs/application.log
cfconfig logger save name=application appender=resource appenderArguments:path={lucee-config}/logs/application.log to=serverName
cfconfig logger save name=application appender=resource appenderArguments:path={lucee-config}/logs/application.log to=/path/to/server/home
```

## Delete a Lucee Logger

```text
cfconfig logger delete application
cfconfig logger delete application serverName
cfconfig logger delete application /path/to/server/home
```

