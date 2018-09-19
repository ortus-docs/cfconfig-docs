# API Overview

**Create a new JSON configuration file programmatically**

```javascript
JSONConfig = new path.to.JSONConfig()
    .setNullSupport( true );
    .setUseTimeServer( true );
    .setAdminPassword( 'myPass' );
    .addCFMapping( '/foo', '/bar' );
    .write();
```

**Read an existing JSON configuration file**

```javascript
JSONConfig = new path.to.JSONConfig()
    .read( 'test.json' );
```

**Read an existing Lucee 4 server configuration file**

```javascript
lucee4ServerConfig = new path.to.Lucee4ServerConfig()
    .setCFHomePath( expandPath( '/path/to/lucee-server' ) )
    .read();

writeDump( lucee4ServerConfig.getMemento() );
```

**Read an existing JSON config file and load into a Lucee 5 web context**

```javascript
JSONConfig = new path.to.JSONConfig()
    .read( expandPath( '.CFConfig.json' ) );

new path.to.Lucee4WebConfig()
    .setMemento( JSONConfig.getMemento() )        
    .write( expandPath( 'WEB-INF/lucee/' ) );
```

### Notes

The `JSONConfig` will read/write to a JSON file called `.CFConfig.json` by default in the home directory you specify. You can alternatively specify a full path to a JSON file to change the name.

The Lucee 4 and Lucee 5 _web_ components expect the `CFHomePath` to be the folder containing the `lucee-web.xml.cfm` file.  
An example would be:

```text
<webroot>/WEB-INF/lucee/
```

The Lucee 4 and Lucee 5 _server_ components expect the `CFHomePath` to be the `lucee-server` folder containing the `/context/lucee-server.xml` file.  
An example would be:

```text
/opt/lucee/lib/lucee-server/
```

The Adobe components expect the `CFHomePath` to be the `cfusion` folder that contains the `lib/neo-runtime.xml` file.  
An example would be:

```text
C:/ColdFusion11/cfusion/
```

The code in this library has only been tested on Lucee and likely doesn't work on Adobe ColdFusion. If anyone wants to make it compatible, feel free to try by beware of tons of use of the Elvis operator, reliance on sorted JSON structs, and some specific WDDX behavior.

