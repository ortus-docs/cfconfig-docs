# Server Stop

If you are keeping your CF configuration in source control via a local JSON file, you may wish for the JSON file to automatically "track" your CF engine's settings.  If so, enable this feature in a config setting like so:

```bash
config set modules.commandbox-cfconfig.exportOnStop=true
```