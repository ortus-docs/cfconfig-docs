# Manage Mail Servers

There are three commands to manage Mail Servers.

## List existing mail servers

```text
cfconfig mailserver list
cfconfig mailserver list from=serverName
cfconfig mailserver list from==/path/to/server/home
```

To receive the data back as JSON, use the `--JSON` flag.

```text
cfconfig mailserver list --JSON
```

## Edit an existing or create a new mail server

Add a mew mail server or update an existing mail server. Existing mail servers will be matched based on the host name.

```text
cfconfig mailserver save smtp.server.com
cfconfig mailserver save smtp=smtp.server.com to=serverName
cfconfig mailserver save smtp=smtp.server.com to=/path/to/server/home
```

## Delete an existing mail server

Identify the mail server uniquely by the host name.

```text
cfconfig mailserver delete /foo
cfconfig mailserver delete /foo serverName
cfconfig mailserver delete /foo /path/to/server/home
```

