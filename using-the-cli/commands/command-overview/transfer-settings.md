# Transfer Config between servers

Note the two servers do not need to be the same kind. CFConfig will translate the config for you.

```
cfconfig transfer server1 server2
cfconfig transfer from=/path/to/server1/install/home to=/path/to/server2/install/home fromFormat=adobe@11 toFormat=luceeServer@5
```
