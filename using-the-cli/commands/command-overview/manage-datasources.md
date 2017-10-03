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

Add a mew datasource or update an existing datasource.  Existing datasources will be matched based on the name.
Valid dbdriver options are
- **MSSQL** -- SQL Server driver
- **MSSQL2** -- jTDS driver
- **PostgreSql**
- **Oracle**
- **Other** -- Custom JDBC URL
- **MySQL**

```
cfconfig datasource save myDS
cfconfig datasource save name=myDS to=serverName
cfconfig datasource save name=myDS to=/path/to/server/home
```



## Delete a datasource