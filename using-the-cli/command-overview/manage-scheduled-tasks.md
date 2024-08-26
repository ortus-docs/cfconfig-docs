# Manage Scheduled Tasks

Scheduled tasks are supported for both Lucee Server and Adobe ColdFusion.  Both engines have some features which are not supported by the other.  Check the parameter descriptions in the command help for `cfconfig task save` for more info.

All CFConfig commands when run against a Lucee server will default to the `fromFormat` or `toFormat` to `luceeServer`.  These commands are a notable exception-- since scheduled tasks can only be imported into a Lucee web context, all commands in the `cfconfig task` namespace will default to the `luceeWeb` for Lucee servers.

## List all Scheduled Tasks

```
cfconfig task list
cfconfig task list from=serverName
cfconfig task list from=/path/to/server/home
```

To receive the data back as JSON, use the `--JSON` flag.

```
cfconfig task list --JSON
```

## Add or update a Scheduled Task

```
cfconfig task save myTask http://www.google.com Once 4/13/2018 "5:00 PM"
cfconfig task save task=myTask url=http://www.google.com interval=Once startDate=4/13/2018 startTime="5:00 PM" to=serverName
cfconfig task save task=myTask url=http://www.google.com interval=Once startDate=4/13/2018 startTime="5:00 PM" to=/path/to/server/home
```

## Delete a Scheduled Task

```
cfconfig task delete myTask
cfconfig task delete myTask serverName
cfconfig task delete myTask /path/to/server/home
```
