# Component Overview

Here are the main components in the project

#### BaseConfig.cfc

This class represents the configuration of a CF engine. It is agnostic and doesn't contain any particular behavior for a specific engine.  
Not all the data it stores applies to every engine though. The `BaseConfig.cfc` is not capable of reading or writing the config, it merely holds the data in a generic manner. If you want to read or write to/from a specific engine's format, you'll need to create one of the engine-specific subclasses, all of which extend `BaseConfig.cfc`.

#### Engine-specific mappers

* **JSONConfig.cfc** - Engine-agnostic JSON format
* **Lucee4Server.cfc** - Lucee 4.x server context
* **Lucee4Web.cfc** - Lucee 4.x web context
* **Lucee5Server.cfc** - Lucee 5.x server context
* **Lucee5Web.cfc** - Lucee 5.x web context
* **Railo4Server.cfc** - Railo 4.x server context
* **Railo4Web.cfc** - Railo 4.x web context
* **Adobe9.cfc** - Adobe ColdFusion 9
* **Adobe10.cfc** - Adobe ColdFusion 10
* **Adobe11.cfc** - Adobe ColdFusion 11
* **Adobe2016.cfc** - Adobe Coldfusion 2016
* **Adobe2018.cfc** - Adobe Coldfusion 2018

### Usage

Each of the components above supports these public methods:

* `setCFHomePath()` - Points to the server home where the config files are to be read or written.
* `read( CFHomePath )` - Extract the config from the files found in the server home.  You can override `CFHomePath` here too.
* `write( CFHomePath )` - Write the config out to the files in the server home whether or not they already exist. You can override `CFHomePath` here too.
* `getMemento()` - Return all configuration in as a raw CFML data structure.  Useful for passing config values to another instance.
* `setMemento()` - Accept configuration as a raw CFML data structure.  Useful for accepting another instance's data.

Create an instance of the component that corresponds to the server that you'd like to read or write config settings from, or the `BaseConfig` class if you want to deal with the generic JSON-based config.

