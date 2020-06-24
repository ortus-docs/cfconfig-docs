# Manage Event Gateway Configuration

Event Gateway Configurations are currently only supported for Adobe ColdFusion. Please contact us if you'd like to sponsor this feature.

## List all Event Gateway Configurations

```text
cfconfig eventgatewayconfig list
cfconfig eventgatewayconfig list from=serverName
cfconfig eventgatewayconfig list from=/path/to/server/home
```

To receive the data back as JSON, use the --JSON flag.

```text
cfconfig eventgatewayconfig list --JSON
```

## Add or update an Event Gateway Configuration

```text
cfconfig eventgatewayconfig save myType "description of gateway" "java.class" 30 true
cfconfig eventgatewayconfig save type=myType description="description of gateway" class="java.class" starttimeout=30 killontimeout=true to=serverName
cfconfig eventgatewayconfig save type=myType description="description of gateway" class="java.class" starttimeout=30 killontimeout=true to=/path/to/server/home
```

## Delete an Event Gateway Configuration

```text
cfconfig eventgatewayconfig delete myType
cfconfig eventgatewayconfig delete myType serverName
cfconfig eventgatewayconfig delete myType /path/to/server/home
```

