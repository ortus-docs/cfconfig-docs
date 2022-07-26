# Getting Started Guide

To use CFConfig, you can install it into CommandBox easily like so.

```text
CommandBox> install commandbox-cfconfig
```

Now that you've got the tool installed you can dig into the command help to see where to go from there. Here's a quick overview of some of the commands. Run the built-in command help for more info on each one.

These commands will work on any CF engine and if you run them from the root of CommandBox server they will "just work" as it will "find" the server for you. To run these commands against another type of server, you'd need to specify a folder path for the "from" or "to" parameters that pointed to the server home directories.

## View a setting

```text
CommandBox> cfconfig show requestTimeout
```

## Set a setting

```text
CommandBox> cfconfig set requestTimeout=0,0,10,0
```

## View all settings for a server

```text
CommandBox> cfconfig show
```

## Add, list, and delete a CF Mapping

```text
CommandBox> cfconfig cfmapping save virtual=/foo physical=C:/bar
CommandBox> cfconfig cfmapping list
CommandBox> cfconfig cfmapping delete /foo
```

## Add, list and delete a datasource

```text
CommandBox> cfconfig datasource save name=myDSN dbdriver=mysql host=localhost port=3306 database=myDB username=brad password=foobar
CommandBox> cfconfig datasource list
CommandBox> cfconfig datasource delete myDSN
```

## Export all settings from a server

```text
CommandBox> cfconfig export .CFConfig.json
```

## Import settings into a server

```text
CommandBox> cfconfig import .CFConfig.json
```

## Transfer settings from one server to another

```text
CommandBox> cfconfig transfer from=oneServer to=anotherServer
```

## Diff all the settings between two servers

```text
CommandBox> cfconfig diff from=oneServer to=anotherServer
CommandBox> cfconfig diff to=anotherServerName
CommandBox> cfconfig diff to=anotherServerName --fromOnly
CommandBox> cfconfig diff to=anotherServerName --toOnly
CommandBox> cfconfig diff to=anotherServerName --valuesDiffer
```

