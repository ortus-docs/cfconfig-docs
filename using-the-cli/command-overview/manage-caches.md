# Manage Caches

There are three commands to manage Lucee/Railo caches.

## List existing caches

```bash
# Lucee server context of the CommandBox server in the current directory
cfconfig cache list

# Lucee web context of the CommandBox server in the current directory
cfconfig cache list fromFormat=luceeWeb

# Target a CommandBox server by name
cfconfig cache list from=serverName

# Target an externally installed server
cfconfig cache list from=/path/to/server/home
```

To receive the data back as JSON, use the `--JSON` flag.

```text
cfconfig cache list --JSON
```

## Edit an existing or create a new cache

Add a new cache or update an existing cache. Existing caches will be matched based on the name. You can use a the `type` parameter as a shortcut for specifying the full Java class, which may change between versions.

```text
cfconfig cache save myCache RAM
cfconfig cache save name=myOtherCache type=EHCache
cfconfig cache save name=myCache type=EHCache  to=serverName
cfconfig cache save name=myCache type=RAM to=/path/to/server/home
```

Alternatively, specify the full class name.

```text
cfconfig cache save myCache lucee.runtime.cache.ram.RamCache
cfconfig cache save name=myCache class=lucee.runtime.cache.ram.RamCache to=serverName
cfconfig cache save name=myCache class=lucee.runtime.cache.ram.RamCache to=/path/to/server/home
```

If your cache provider expects custom properties, pass them as additional parameters to this command prefixed with the text `custom:`. This requires named parameters, of course.

```text
cfconfig cache save name=myCache type=RAM custom:timeToIdleSeconds=0 custom:timeToLiveSeconds=0
```

## Delete an existing cache

Identify the cache uniquely by the name.

```text
cfconfig cache delete myCache
cfconfig cache delete myCache serverName
cfconfig cache delete myCache /path/to/server/home
```

