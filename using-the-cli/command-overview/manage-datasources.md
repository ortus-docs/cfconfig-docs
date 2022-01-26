# Manage Datasources

There are three commands to manage datasources.

## List all datasources

```text
cfconfig datasource list
cfconfig datasource list from=serverName
cfconfig datasource list from=/path/to/server/home
```

To receive the data back as JSON, use the `--JSON` flag.

```text
cfconfig datasource list --JSON
```

## Edit an existing or create a new datasource

Add a new datasource or update an existing datasource. Existing datasources will be matched based on the name. Valid dbdriver options are

* **MSSQL** -- SQL Server driver
* **MSSQL2** -- jTDS driver
* **PostgreSql**
* **Oracle**
* **Other** -- Custom JDBC URL
* **MySQL**

```text
cfconfig datasource save name=myDSN dbdriver=mysql host=localhost port=3306 database=myDB username=brad password=foobar
cfconfig datasource save name=myDS ... to=serverName
cfconfig datasource save name=myDS ... to=/path/to/server/home
```

## Delete a datasource

Identify the datasource uniquely by the name.

```text
cfconfig datasource delete foo
cfconfig datasource delete foo serverName
cfconfig datasource delete foo /path/to/server/home
```

