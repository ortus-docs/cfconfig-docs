# Manage CF Mappings

There are three commands to manage CF mappings.

## List all CF Mappings

```bash
cfconfig cfmapping list
cfconfig cfmapping list from=serverName
cfconfig cfmapping list from=/path/to/server/home
```

To receive the data back as JSON, use the `--JSON` flag.

```text
cfconfig cfmapping list --JSON
```

## Edit an existing or create a new CF Mapping

Add a mew CF mapping or update an existing CF Mapping. Existing mappings will be matched based on the virtual path.

```text
cfconfig cfmapping save /foo C:/foo/bar
cfconfig cfmapping save virtual=/foo physical=C:/foo/bar to=serverName
cfconfig cfmapping save virtual=/foo physical=C:/foo/bar to=/path/to/server/home
```

## Delete a CF Mapping

Identify the mapping uniquely by the virtual path.

```text
cfconfig cfmapping delete /foo
cfconfig cfmapping delete /foo serverName
cfconfig cfmapping delete /foo /path/to/server/home
```

