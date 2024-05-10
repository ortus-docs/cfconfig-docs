# Installation

The CFConfig CLI lives on ForgeBox and can be installed into CommandBox with the following command:

```
CommandBox> install commandbox-cfconfig
```

If you do not have CommandBox installed, have no fear! CommandBox is a single binary that will run on Mac, Linux, or Windows. Please visit our CommandBox docs and you'll have it installed in a jiffy.

[https://commandbox.ortusbooks.com/setup/installation](https://commandbox.ortusbooks.com/setup/installation)

## Requirements

The only requirement for the CFConfig CLI is [CommandBox](https://commandbox.ortusbooks.com/setup/installation) 3.6.0 or higher.

## Updating CFConfig

CFConfig is under active development and changing on a regular basis. To make sure you have the latest version installed, you can simply cd into the CFML home directory of your CommandBox install and use the regular package `update` command.  This will pull in minor and patch updates but not major version changes.

```
update --system
```

If you have a pre-release version of CFConfig or need to upgrade to a new major version, use this command:

```
install commandbox-cfconfig --force
```

