# Transfer Settings

Transfer configuration from one location/server to another. If you don't specify a from or to, we look for a CommandBox server using the current working directory. Only rely on this if you have a single CommandBox server running in the current directory. You must specify at least a `from` or a `to`.

Note the two servers do not need to be the same kind. CFConfig will translate the config for you.

```text
cfconfig transfer from=servername to=anotherServername
cfconfig transfer from=serverName
cfconfig transfer to=serverName
cfconfig transfer from=/path/to/server/home to=/path/to/another/server/home
cfconfig transfer from=/path/to/server/home
cfconfig transfer to=/path/to/server/home
```

All the same rules for engine format and version apply.

```text
cfconfig transfer from=/path/to/.CFConfig.json to=/path/to/server/home toFormat=luceeServer@5.1
```

The version number can be left off `toFormat` and `fromFormat` when reading or writing to a CFConfig JSON file or a CommandBox server since we already know the version. If you don't specify a Lucee web or Server context, we default to server. Use a format of `luceeWeb` to switch.

### IncludeList and excludeList

You can customize what config settings are transferred with the includeList and excludeList params. If at least one include pattern is provided, ONLY matching settings will be included. Nested keys such as datasources.myDSN or mailservers\[1\] can be used. You may also use basic wildcards in your pattern. A single  _will match any number of chars inside a key name. A double \*_ will match any number of nested keys.

```bash
# Include all settings starting with "event"
cfconfig transfer from=.CFConfig.json includeList=event*
# Exclude all keys called "password" regardless of what struct they are in
cfconfig transfer from=.CFConfig.json excludeList=**.password
```

### Append flag

Use the append parameter to merge incoming data with any data already present. For example, if a server already has one datasource defined and you import a JSON file with 2 more unique datasources, the --append flag will not remove the pre-existing one.

```bash
cfconfig transfer from=.CFConfig.json includeList=datasources --append
```

### JSON Expansion Replacements

If you usually replace sensitive or volatile information in a JSON export with env var expansions like `${DB_PASSWORD},` you can do this automatically my supplying one or more replace mappings. The key is a regular expression to match a key in the format of `datasources.myDSN.password` and the value is the name of the env var to use. The values will be written to a `.env` file in the current working directory. You can override this path with the `dotenvFile` param, or pass an empty string to disable it from being written.

```bash
cfconfig transfer to=.CFConfig.json replace:datasources\.myDSN\.password=DB_PASSWORD
```

As the value is a regular expression, you can use backreferences like `\1` in your env var to make them dynamic.  
This example would create env vars such as `DB_MYDSN_PASSWORD` where `MYDSN` is your actual datasource name.

```bash
cfconfig tranfser to=.CFConfig.json replace:datasources\.(.*)\.password=DB_\1_PASSWORD
```

Any valid regex is possible for some clever replacements. This example would create env vars such as `DB_MYDSN_PORT`, `DB_MYDSN_HOST`, and `DB_MDSN_DATABASE`

```bash
cfconfig tranfser to=.CFConfig.json replace:datasources\.(.*)\.(password|class|port|host|database)=DB_\1_\2 dotenvFile=../../settings.properties
```

To avoid having to pass these replacements every time you transfer your config, you can set then as a global setting for the `commandbox-cfconfig` module.

```bash
# Replace all mail server passwords with ${MAIL_PASSWORD}
config set modules.commandbox-cfconfig.JSONExpansions[mailServers.*.password]=MAIL_PASSWORD
# Dynamically replace with ${DB_MYDSN_password}, ${DB_MYDSN_CLASS}, ${DB_MYDSN_PORT}, etc
config set modules.commandbox-cfconfig.JSONExpansions[datasources\.(.*)\.(password|class|port|host|database)]=DB_\1_\2
# Use default env var name for all settings starting with "requestTimeout" and replace with ${REQUEST_TIMEOUT} and ${REQUEST_TIMEOUT_ENABLED}
config set modules.commandbox-cfconfig.JSONExpansions[requestTimeout.*]=
```

{% hint style="info" %}
Note, the `config set` syntax shown above require at least CommandBox 5.4.0
{% endhint %}

