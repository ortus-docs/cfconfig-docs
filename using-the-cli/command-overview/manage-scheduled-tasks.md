# Manage Scheduled Tasks

## List all Scheduled Tasks

```text
cfconfig task list
cfconfig task list from=serverName
cfconfig task list from=/path/to/server/home
```

To receive the data back as JSON, use the --JSON flag.

```text
cfconfig task list --JSON
```

## Add or update a Scheduled Task

```text
cfconfig task save myTask http://www.google.com Once 4/13/2018 "5:00 PM"
cfconfig task save task=myTask url=http://www.google.com interval=Once startDate=4/13/2018 startTime="5:00 PM" to=serverName
cfconfig task save task=myTask url=http://www.google.com interval=Once startDate=4/13/2018 startTime="5:00 PM" to=/path/to/server/home
```

## Delete a Scheduled Task

```text
cfconfig task delete myTask
cfconfig task delete myTask serverName
cfconfig task delete myTask /path/to/server/home
```

