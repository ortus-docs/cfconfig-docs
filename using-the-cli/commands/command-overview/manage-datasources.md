# Manage Datasources

There are three commands to manage datasources.

## List all datasources

List all datasources for a server.

```
cfconfig datasource list
cfconfig datasource list from=serverName
cfconfig datasource list from==/path/to/server/home
```

To receive the data back as JSON, use the --JSON flag.

```
cfconfig datasource list --JSON
```

## Edit an existing or create a new datasource

## Delete a datasource