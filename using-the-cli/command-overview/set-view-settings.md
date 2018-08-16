# Set/View Settings

## View all configuration

```text
cfconfig show
cfconfig show serverName
cfconfig show /path/to/server/install/home
```

## View a specific configuration setting

```text
cfconfig show requestTimeout
cfconfig show requestTimeout serverName
cfconfig show requestTimeout /path/to/server/install/home adobe@11
```

## Set a configuration setting

Note, this command requires named parameters.

```text
cfconfig set adminPassword=commandbox
cfconfig set adminPassword=commandbox to=serverName
cfconfig set adminPassword=commandbox to=/path/to/server/install/home toFormat=adobe@11
```

You can actually use CFConfig set to manage the static contents of a JSON export. The JSON file is, after all, just another location you can read from or write to.

```text
# Pull current config from server into JSON file
cfconfig export myConfig.json
# Edit JSON file directly
cfconfig set adminPassword=commandbox to=myConfig.json
```

