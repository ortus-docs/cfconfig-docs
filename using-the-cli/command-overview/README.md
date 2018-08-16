# Command Overview

Here's an overview of all the commands available to the CFConfig CLI. There are sub pages for each of these commands with additional details.

## Manage All Configs

### `cfconfig export`

Extracts all configuration from a server to a location of your choice.

### `cfconfig import`

Imports all configuration from a location of your choice into a server. Like `export`, but spelled different.

### `cfconfig transfer`

Moves all configuration from a location of your choice to another location of your choice. Like `import` and `export` but pronounced different.

### `cfconfig diff`

Shows a diff of every setting that's different between two servers or a server and a JSON file.

## Manage Individual Configs

### `cfconfig set`

Sets or overwrites a single setting on a server.

### `cfconfig show`

Views a single setting on a server.

## Manage Datasources

### `cfconfig datasource list`

List all datasources.

### `cfconfig datasource save`

Add or update a datasource by name

### `cfconfig datasource delete`

Remove a datasource by name.

## Manage CF Mappings

### `cfconfig cfmapping list`

List all CF mappings

### `cfconfig cfmapping save`

Add or update a CF mapping by virtual path.

### `cfconfig cfmapping delete`

Remove a CF mapping by virtual path.

## Manage Lucee/Railo Caches

### `cfconfig cache list`

List all caches in a Lucee/Railo server.

### `cfconfig cache save`

Add or update a cache by name.

### `cfconfig cache delete`

Remove a cache by name.

## Manage Mail Servers

### `cfconfig mailserver list`

List all mail servers on a server.

### `cfconfig mailserver save`

Add or update a mail server by host.

### `cfconfig mailserver delete`

Delete a mail server by host.

