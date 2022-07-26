# Overview

```text
   ____ _____ ____             __ _       
  / ___|  ___/ ___|___  _ __  / _(_) __ _ 
 | |   | |_ | |   / _ \| '_ \| |_| |/ _` |
 | |___|  _|| |__| (_) | | | |  _| | (_| |
  \____|_|   \____\___/|_| |_|_| |_|\__, |
                                    |___/
```

## Overview

CFConfig gives you the ability to manage most every setting that shows up in the web administrator, but instead of logging into a web interface, you can mange it from the command line by hand or as part of a scripted server setup. You can seamless transfer config for all the following:

* CF Mappings
* Datasources
* Mail servers
* Request, session, or application timeouts
* Licensing information \(for Adobe\)
* Passwords

  -Template caching settings

  -Basically any settings in the web based administrator

### Use on any server

CFConfig will work on any CF server regardless of how it was installed. Since it interacts directly with the config files, the server doesn't need to be running. Heck, the server doesn't even need to be installed yet! CFConfig can be used to write out config files before you even start a CommandBox server for the first time.

But it's not just for CommandBox servers. All you need is the folder path to the CF home in your server installation and you can point the CFConfig library at it. This means CFConfig can be used for syncing config across existing servers, standing up docker containers, or provisioning Vagrant VMs.

### How does it work

CFConfig interfaces directly with the XML and property files used by your CF engine to store its configuration. It takes care of translating the config properly so you use the same commands regardless of what engine you're managing the config for. The tool will try hard to figure out the version of ColdFusion or Lucee that you have installed and there are hints you can give it as well. Both ACF and Lucee also have settings to monitor the config files for changes so you don't even need to restart the server to pick up your changes.

CFConfig exists in two parts:

* A service layer for reading, writing, and storing configuration for all CF engines.
* A set of scriptable commands built on top of CommandBox CLI

### CFConfig Service Layer

The heart of CFConfig is a standalone module that provides a set of models and services for interacting with configuration files for all CF engines. This library allows for reading, writing, storing, and diffing configuration. This is an underlying service layer meant to have other tools built on top of it.

The CFConfig services do not require CommandBox, but can be used on its own and provides a nice, fluent API for managing configs. They do not use RDS and don't need the server to be running. The services just needs access to the installation folder for a server to locate its config files.

#### Features at a Glance

* Generic JSON storage of any CF engine's settings
* Engine-specific mappings for all major engines to convert their config to and from the generic JSON format
* Export config from a server as a backup
* Import config to a server to speed/automate setup
* Copy config from one server to another. Servers could be different engines– i.e. copy config from Adobe CF11 to Lucee 5.
* Merge config from multiple servers together. Ex: combine several Lucee web contexts into a single config \(mappings, datasources, etc\)

### CFConfig CLI

The CLI portion of CFConfig warps up the services layer into a CommandBox module that provides command line access to all the features above, but from your native OS shell, bash scripts, automations, or Docker/Vagrant/Heroku provisioners.

The CFConfig CLI also has a deep integration with CommandBox servers making it very easy to manage their configuration.

#### Features at a Glance

* Provides a native CLI tool for managing server configuration
* Scriptable for automated server setup
* Provides complete command help built in
* Tight integration with CommandBox servers

