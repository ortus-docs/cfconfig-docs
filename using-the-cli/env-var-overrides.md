# Env Var Overrides

Every [Config Setting](../introduction/config-items.md) can be overridden by convention by creating environment variables in the shell where you run `box`.  This is idea for Docker containers or CI builds were you want to easily set one-off settings and not require an entire JSON file.  You set set these as actual environment variables or [Java system properties of the CLI](https://commandbox.ortusbooks.com/usage/execution#ad-hoc-java-properties-for-the-cli).   Env vars are loaded AFTER any `.cfconfig.json` files have been loaded by convention and will override any settings in the JSON.  They are not case sensitive.  

The var must start with the text `cfconfig_` and will be followed by the name of the setting.

```bash
cfconfig_adminPassword=myPass
```

For nested settings inside of a struct or array you can use underscores to represent dots.  Note the following will error if there is not already a datasource named `myDSN` in the server.

```bash
cfconfig_datasources_myDSN_password=myPass
```

The overrides are applied using the same mechanism that the `cfconfig set` command uses, which means you can also pass JSON directly for complex values.

```bash
# JSON which will be parsed
cfconfig_mailServers=[{"port":"25","smtp":"localhost2"}]
```

On OS's like Windows which allow for any manner of special characters, you can provide any string which would also be valid for the `config set` command. Ex:

```bash
# dot-delimited keys
cfconfig_datasources.myDSN.password=myPass
# array indexes too
cfconfig_mailServers[1].smtp=mail.server.com
```

When you provide JSON, the `append` flag will be set to true when adding the configuration to what's already in CommandBox.

Overridden env vars will **not** be written to any `.cfconfig.json` file and will be lost when box stops. They will also take precedence and override any explicit settings already set.

