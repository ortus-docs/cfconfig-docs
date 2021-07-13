# Set/View Settings

## View all configuration

```bash
cfconfig show
cfconfig show serverName
cfconfig show /path/to/server/install/home
```

## View a specific configuration setting

```bash
cfconfig show requestTimeout
cfconfig show requestTimeout serverName
cfconfig show requestTimeout /path/to/server/install/home adobe@11
```

## Set a configuration setting

Note, this command requires named parameters.

```bash
cfconfig set adminPassword=commandbox
cfconfig set adminPassword=commandbox to=serverName
cfconfig set adminPassword=commandbox to=/path/to/server/install/home toFormat=adobe@11
```

You can actually use CFConfig set to manage the static contents of a JSON export. The JSON file is, after all, just another location you can read from or write to.

```bash
# Pull current config from server into JSON file
cfconfig export myConfig.json
# Edit JSON file directly
cfconfig set adminPassword=commandbox to=myConfig.json
```

### Using "deep" property names

The `cfconfig set` and `cfconfig show` commands work the same as `package set/show` in that you can use "deep" keys to access nested properties.

```bash
cfconfig show datasources.myDSN
cfconfig show mailServers[1].port
cfconfig set loggers.deploy.level=debug
cfconfig set datasources.myDSN.password=myPass
```

Keep in mind that examples such as the last line above can create invalid config if you don't already have a datasource called `myDSN`.  If you're needing to create new complex objects, or you're not sure if they will exist, use the other CFConfig namespaces like `cfconfig datasource save` which will ensure complete settings are saved.

