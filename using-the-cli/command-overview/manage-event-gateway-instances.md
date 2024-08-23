# Manage Event Gateway Instances

Event Gateway Instances are currently only supported for Adobe ColdFusion. Please contact us if you'd like to sponsor this feature.

## List all Event Gateway Instances

```text
cfconfig eventgatewayinstance list
cfconfig eventgatewayinstance list from=serverName
cfconfig eventgatewayinstance list from=/path/to/server/home
```

To receive the data back as JSON, use the `--JSON` flag.

```text
cfconfig eventgatewayinstance list --JSON
```

## Add or update an Event Gateway Instance

```text
cfconfig eventgatewayinstance save myInstanceId myType "/path1/some.cfc,/path2/code.cfc"
cfconfig eventgatewayinstance save gatewayId=myInstanceId type=myType cfcPaths="/path1/some.cfc,/path2/code.cfc" configurationPath="path3" to=serverName
cfconfig eventgatewayinstance save gatewayId=myInstanceId type=myType cfcPaths="/path1/some.cfc,/path2/code.cfc" configurationPath="path3" to=/path/to/server/home
```

## Delete an Event Gateway Instance

```text
cfconfig eventgatewayinstance delete myInstanceId
cfconfig eventgatewayinstance delete myInstanceId serverName
cfconfig eventgatewayinstance delete myInstanceId /path/to/server/home
```

