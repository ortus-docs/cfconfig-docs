# Config Items

Here's the list of settings that CFConfig can manage

```js
// One of the strings "never", "once", "always"
name='inspectTemplate' type='string'
// Number of templates to cache
name='templateCacheSize' type='numeric'
// True/false
name='componentCacheEnabled' type='boolean'
// True/false
name='saveClassFiles' type='boolean'
// True/false
name='UDFTypeChecking' type='boolean'
// true/false
name='nullSupport' type='boolean'
// true/false
name='dotNotationUpperCase' type='boolean'
// true/false
name='suppressWhitespaceBeforecfargument' type='string'
// One of the strings "standard", "small", "strict"
name='scopeCascading' type='string'
// True/false
name='searchResultsets' type='boolean'
// Ex: en_US
name='thisLocale' type='string'
// Ex: America/Chicago
name='thisTimeZone' type='string'
// Ex: pool.ntp.org
name='timeServer' type='string'
// true/false
name='useTimeServer' type='boolean'
// Ex: windows-1252 (Lucee: Default character used to read templates (*.cfm and *.cfc files))
name='templateCharset' type='string'
// Ex: UTF-8 (Lucee: Default character set for output streams, form-, url-, and cgi scope variables and reading/writing the header)
name='webCharset' type='string'
// Ex: windows-1252 (Default character set for reading from/writing to various resources)
name='resourceCharset' type='string'
// One of the strings "cfml", "j2ee"
name='sessionType' type='string'
// True/false
name='mergeURLAndForm' type='boolean'
// True/false
name='applicationMangement' type='boolean'
// True/false
name='sessionMangement' type='boolean'
// True/false
name='clientManagement' type='boolean'
// True/false
name='domainCookies' type='boolean'
// True/false
name='clientCookies' type='boolean'
// Number of seconds
name='sessionCookieTimeout' type='numeric'
// True/false
name='sessionCookieHTTPOnly' type='boolean'
// True/false
name='sessionCookieSecure' type='boolean'
// True/false
name='sessionCookieDisableUpdate' type='boolean'
// One of the strings "classic", "modern"
name='localScopeMode' type='string'
// True/false
name='CGIReadOnly' type='string'
// Timespan Ex: 0,5,30,0
name='sessionTimeout' type='string'
// Timespan Ex: 0,5,30,0
name='applicationTimeout' type='string'
// Timespan Ex: 0,5,30,0
name='sessionMaximumTimeout' type='string'
// Timespan Ex: 0,5,30,0
name='applicationMaximumTimeout' type='string'
// One of the strings "none", "mixed", "modern", "classic"
name='applicationListener' type='string'
/* One of the strings
* "curr2root" - Current dir to web root (Lucee and Adobe [option 2])
* "curr" - Current dir only (Lucee only)
* "root" - Only in web root (Lucee only)
* "currorroot" - Current dir or web root (Lucee and Adobe [option 3])
* "curr2driveroot" - Current dir to drive root (Adobe only [option 1])
*/
name='applicationMode' type='string'
// Timespan Ex: 0,5,30,0
name='clientTimeout' type='string'
// One of the strings "memory", "file", "cookie", <cache-name>, <datasource-name>
name='sessionStorage' type='string'
// One of the strings "memory", "file", "cookie", <cache-name>, <datasource-name>
name='clientStorage' type='string'
// Timespan Ex: 0,5,30,0
name='requestTimeout' type='string'
// True/false
name='requestTimeoutEnabled' type='boolean'
// "none", "all" or a comma-delimited list with some combination of "cgi", "cookie", "form", "url".
name='scriptProtect' type='string'
// True/false
name='perAppSettingsEnabled' type='boolean'
// True/false
name='useUUIDForCFToken' type='boolean'
// True/false
name='requestTimeoutInURL' type='boolean'
// One of the strings "regular", "white-space", "white-space-pref"
name='whitespaceManagement' type='string'
// True/false
name='compression' type='boolean'
// True/false
name='supressContentForCFCRemoting' type='boolean'
// True/false
name='bufferTagBodyOutput' type='boolean'
// Key is datasource name, value is struct of properties
name='datasources' type='struct'
// Array of structs of properties. Mail servers are uniquely identified by host
name='mailServers' type='array'
// Encoding to use for mail. Ex: UTF-8
name='mailDefaultEncoding' type='string'
// True/false enable mail spooling
name='mailSpoolEnable' type='boolean'
// Number of seconds for interval
name='mailSpoolInterval' type='numeric'
// Number of seconds to wait for mail server response
name='mailConnectionTimeout' type='numeric'
// True/false to allow downloading attachments for undelivered emails
name='mailDownloadUndeliveredAttachments' type='numeric'
// Sign messages with cert
name='mailSignMesssage' type='boolean'
// Path to keystore
name='mailSignKeystore' type='string'
// Password to the keystore
name='mailSignKeystorePassword' type='string'
// Alias of the key with which the certificcate and private key is stored in keystore. The supported type is JKS (java key store) and pkcs12.
name='mailSignKeyAlias' type='string'
// Password with which the private key is stored.
name='mailSignKeyPassword' type='string'
// Key is virtual path, value is struct of properties
name='CFMappings' type='struct'
// True/false
name='errorStatusCode' type='boolean'
// True/false
name='disableInternalCFJavaComponents' type='boolean'
// True/false
name='secureJSON' type='boolean'
// A string representing the JSON prefx like "//"
name='secureJSONPrefix' type='string'
// Number of KB for buffer size (1024)
name='maxOutputBufferSize' type='numeric'
// True/false
name='inMemoryFileSystemEnabled' type='boolean'
// Number of MB for in memory file system
name='inMemoryFileSystemLimit' type='numeric'
// Number of MB for in memory application file system
name='inMemoryFileSystemAppLimit' type='numeric'
// True/false
name='watchConfigFilesForChangesEnabled' type='boolean'
// Number of seconds
name='watchConfigFilesForChangesInterval' type='numeric'
// List of file extensions. Ex: "xml,properties"
name='watchConfigFilesForChangesExtensions' type='string'
// True/false
name='allowExtraAttributesInAttrColl' type='boolean'
// True/false
name='disallowUnamedAppScope' type='boolean'
// True/false
name='allowApplicationVarsInServletContext' type='boolean'
// Number of minutes
name='CFaaSGeneratedFilesExpiryTime' type='numeric'
// Absolute path to store index files for ORM search.
name='ORMSearchIndexDirectory' type='string'
// default path (relative to the web root) to the directory containing the cfform.js file.
name='CFFormScriptDirectory' type='string'
// Your Google maps API key
name='googleMapKey' type='string'
// True/false
name='serverCFCEenabled' type='boolean'
// Specify the absolute path to a CFC having onServerStart() method, like "c:\server.cfc". Or specify a dot delimited CFC path under webroot, like "a.b.server". By default, ColdFusion will look for server.cfc under webroot.
name='serverCFC' type='string'

// file extensions as a comma separated list which gets compiled when used in the CFInclude tag * for all.
name='compileExtForCFInclude' type='string'
name='generalErrorTemplate' type='string'
name='missingErrorTemplate' type='string'
// Maximum number of parameters in a POST request sent to the server.
name='postParametersLimit' type='numeric'
// Limits the amount of data in MB that can be posted to the server in a single request.
name='postSizeLimit' type='numeric'
// Requests smaller than the specified limit in MB are not handled by the throttle.
name='throttleThreshold' type='numeric'
// Limits total memory size in MB for the throttle
name='totalThrottleMemory' type='numeric'
// Plain text admin password
name='adminPassword' type='string'
// Plain text admin RDS password
name='adminRDSPassword' type='string'
// Plain text default password for new Lucee web context
name='adminPasswordDefault' type='string'
// hashed salted password for Lucee
name='hspw' type='string'
// hashed password for Lucee/Railo
name='pw' type='string'
// Salt for admin password in Lucee
name='adminSalt' type='string'
// hashed salted default password for new Lucee web context
name='defaultHspw' type='string'
// hashed default password for new Lucee/Railo web context
name='defaultPw' type='string'
// License key (only used for Adobe)
name='license' type='string'
// Previous license key (required for an upgrade license key)
name='previousLicense' type='string'
// TODO: Figure out what hashing algorithms each version of ACF use, and share the
// same setting so the hashes passwords are as portable as possible
// hashed admin password for Adobe CF11
name='ACF11Password' type='string'
// hashed RDS password for Adobe CF11
name='ACF11RDSPassword' type='string'
```