# Manage Lucee/Railo Caches

There are three commands to manage Lucee/Railo caches.

## Listing existing caches

List all caches for a server.

```bash
# Lucee server context of the CommandBox server in the current directory
cfconfig cache list

# Lucee web context of the CommandBox server in the current directory
cfconfig cache list fromFormat=luceeWeb

cfconfig cache list from=serverName

cfconfig cache list from==/path/to/server/home
```

To receive the data back as JSON, use the --JSON flag.
```
cfconfig cache list --JSON
```

## Updating or creating a cache

## Deleting an existing cache