# Overview

```
   ____ _____ ____             __ _       
  / ___|  ___/ ___|___  _ __  / _(_) __ _ 
 | |   | |_ | |   / _ \| '_ \| |_| |/ _` |
 | |___|  _|| |__| (_) | | | |  _| | (_| |
  \____|_|   \____\___/|_| |_|_| |_|\__, |
                                    |___/ 
```

CFConfig exists in two parts:

- A service layer for reading, writing, and storing configuration for all CF engines.
- A set of scriptable commands built on top of CommandBox CLI

## CFConfig Service Layer

The heart of CFConfig is a standalone module that provides a set of models and services for interacting with configuration files for all CF engines.  This library allows for reading, writing, storing, and diffing configuration. This is an underlying service layer meant to have other tools built on top of it.  

The CFConfig services do not require CommandBox, but can be used on its own and provides a nice, fluent API for managing configs.  They do not use RDS and don't need the server to be running. The services just needs access to the installation folder for a server to locate its config files.

### Features at a Glance

- Generic JSON storage of any CF engine's settings
- Engine-specific mappings for all major engines to convert their config to and from the generic JSON format
- Export config from a server as a backup
- Import config to a server to speed/automate setup
- Copy config from one server to another. Servers could be different engines– i.e. copy config from Adobe CF11 to Lucee 5.
- Merge config from multiple servers together. Ex: combine several Lucee web contexts into a single config (mappings, datasources, etc)

## CFConfig CLI

The CLI portion of CFConfig warps up the services layer into a CommandBox module that provides command line access to all the features above, but from your native OS shell, bash scripts, automations, or Docker/Vagrant/Heroku provisioners.  

The CFConfig CLI also has a deep integration with CommandBox servers making it very easy to manage their configuration.

### Features at a Glance

- Provides a native CLI tool for managing server configuration
- Scriptable for automated server setup
- Provides complete command help built in
- Tight integration with CommandBox servers





