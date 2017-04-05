# Diff settings between servers

You can diff any two locations, meaning two servers, two JSON files, a server and a JSON file, etc, etc.

```
cfconfig diff server1 server2
cfconfig diff file1.json file2.json
cfconfig diff servername file.json
cfconfig diff from=path/to/servers1/home to=path/to/server2/home
```

You can even filter what config settings you see:
```
cfconfig diff to=serverName --all
cfconfig diff to=serverName --valuesDiffer --toOnly --fromOnly
```
