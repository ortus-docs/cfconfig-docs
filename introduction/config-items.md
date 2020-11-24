# Config Items

CFConfig supports over 200 individual config items. Here's the list of settings that CFConfig can manage

```javascript
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
// Ex:     America/Chicago
name='thisTimeZone' type='string'
// Ex:     pool.ntp.org
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
* "currorroot" -  Current dir or web root (Lucee and Adobe [option 3])
* "curr2driveroot" - Current dir to drive root (Adobe only [option 1])
*/
name='applicationMode' type='string'

// Timespan Ex: 0,5,30,0
name='clientTimeout' type='string'
// One of the strings "memory", "file", "cookie", <cache-name>, <datasource-name>
name='sessionStorage' type='string'
// One of the strings "memory", "file", "cookie", <cache-name>, <datasource-name>, "Registry"
name='clientStorage' type='string'
// Number of minutes between client storage purge.  Not to be less tham 30 minutes.
name='clientStoragePurgeInterval' type='numeric'
// A struct of valid client storage locations including registry, cookie, and any configured datasources. Only used by Adobe.
name='clientStorageLocations' type='struct'

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
// One of the strings "off", "simple", "smart"
// for Lucee backwards compat, you can use "regular", "white-space", "white-space-pref" which map to the above options in the same order.
// Adobe only has on and off so "simple" and "smart" both just map to the fetaure being on.
name='whitespaceManagement' type='string'
// True/false
name='compression' type='boolean'
// True/false
name='supressContentForCFCRemoting' type='boolean'
// True/false
name='bufferTagBodyOutput' type='boolean'
// Key is datasource name, value is struct of properties
name='datasources' type='struct'

// Array of structs of properties.  Mail servers are uniquely identified by host
name='mailServers' type='array'
/**
 * Custom tags have no unique identifier.  In Adobe, there's a made up
 * "virtual" key of /WEB-INF/customtags(somenumber), but it's never shown
 * topside.  In Lucee, you *could* name a path, but you don't have to.
 *
 * We're going to store in an array, and later if we need to determine
 * uniqueness, we'll manufacture a key to do so.
 */
// Array of tag paths ( value struct of properties )
name='customTagPaths' type='array'
// Encoding to use for mail. Ex: UTF-8
name='mailDefaultEncoding' type='string'
// True/false enable mail spooling
name='mailSpoolEnable' type='boolean'
// Number of seconds for interval
name='mailSpoolInterval' type='numeric'
// Number of seconds to wait for mail server response
name='mailConnectionTimeout' type='numeric'
// True/false to allow downloading attachments for undelivered emails
name='mailDownloadUndeliveredAttachments' type='boolean'
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
// Key is log name, value is struct of properties
name='loggers' type='struct'
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

/* Error Templates. One of the strings
* "default" - Standard handling for engine. Blank for Adobe, "error.cfm" for Lucee/Railo. Not secure.
* "secure" - Uses the engine's secure template.
* "neo" - Mirrors appearance of default Adobe handler (Lucee/Railo)
* Alternatively, you can provide the path to a custom template
*/
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


// Maximum number of simultaneous Template requests
name='maxTemplateRequests' type='numeric'
// Maximum number of simultaneous Flash Remoting requests
name='maxFlashRemotingRequests' type='numeric'
// Maximum number of simultaneous Web Service requests
name='maxWebServiceRequests' type='numeric'
// Maximum number of simultaneous CFC function requests
name='maxCFCFunctionRequests' type='numeric'
// Maximum number of simultaneous Report threads
name='maxReportRequests' type='numeric'
// Maximum number of threads available for CFTHREAD
name='maxCFThreads' type='numeric'
// Timeout requests waiting in queue after XX seconds
name='requestQueueTimeout' type='numeric'
// Request Queue Timeout Page
name='requestQueueTimeoutPage' type='string'

// Key is cache connection name, value is struct of properties
name='caches' type='struct'

// name of default Object cache connection
name='cacheDefaultObject' type='string'
// name of default function cache connection
name='cacheDefaultFunction' type='string'
// name of default Template cache connection
name='cacheDefaultTemplate' type='string'
// name of default Query cache connection
name='cacheDefaultQuery' type='string'
// name of default Resource cache connection
name='cacheDefaultResource' type='string'
// name of default Include cache connection
name='cacheDefaultInclude' type='string'
// name of default File cache connection
name='cacheDefaultFile' type='string'
// name of default HTTP cache connection
name='cacheDefaultHTTP' type='string'
// name of default WebService cache connection
name='cacheDefaultWebservice' type='string'

// Line Debugger Settings - Allow Line Debugging
name='lineDebuggerEnabled' type='boolean'
// Line Debugger Settings - Debugger Port
name='lineDebuggerPort' type='numeric'
// Line Debugger Settings - Maximum Simultaneous Debugging Sessions:
name='lineDebuggerMaxSessions' type='numeric'

// Enable robust error information (Adobe only)
name='robustExceptionEnabled' type='boolean'
// Enable Ajax debugging window (Adobe only)
name='ajaxDebugWindowEnabled' type='boolean'
// Enable Request Debugging Output
name='debuggingEnabled' type='boolean'
// Remote DOM Inspection Settings
name='weinreRemoteInspectionEnabled' type='boolean'
// Report Execution Times
name='debuggingReportExecutionTimes' type='boolean'

// Debugging Highlight templates taking longer than the following ms
name='debuggingReportExecutionTimesMinimum' type='numeric'
// Debugging Use the following output mode for long template request execution times
name='debuggingReportExecutionTimesTemplate' type='string'
// Debugging Output Format (dockable.cfm, classic.cfm)
name='debuggingTemplate' type='string'
// Debugging show General debug information
name='debuggingShowGeneral' type='boolean'
// Debugging show Database Activity
name='debuggingShowDatabase' type='boolean'
// Debugging show Exception Information
name='debuggingShowException' type='boolean'
// Debugging show Tracing Information
name='debuggingShowTrace' type='boolean'
// Debugging show Timer Information
name='debuggingShowTimer' type='boolean'
// Debugging Flash Form Compile Errors and Messages
name='debuggingShowFlashFormCompileErrors' type='boolean'
// Debugging Variables. Select this option to enable variable reporting.
name='debuggingShowVariables' type='boolean'
// Debugging include application vars
name='debuggingShowVariableApplication' type='boolean'
// Debugging include cgi vars
name='debuggingShowVariableCGI' type='boolean'
// Debugging include client vars
name='debuggingShowVariableClient' type='boolean'
// Debugging include cookie vars
name='debuggingShowVariableCookie' type='boolean'
// Debugging include form vars
name='debuggingShowVariableForm' type='boolean'
// Debugging include request vars
name='debuggingShowVariableRequest' type='boolean'
// Debugging include server vars
name='debuggingShowVariableServer' type='boolean'
// Debugging include session vars
name='debuggingShowVariableSession' type='boolean'
// Debugging include URL vars
name='debuggingShowVariableURL' type='boolean'
// Debugging IP Addresses
name='debuggingIPList' type='string'

// Monitoring Service Port (Only used by Adobe CF)
// The port for the monitoring service to bind to
name='monitoringServicePort' type='numeric'
// The host for the monitoring service to bind to
// See https://tracker.adobe.com/#/view/CF-4202562
name='monitoringServiceHost' type='string'

// .NET Services (Only used by Adobe CF)
// Java port for .NET services
name='dotNetPort' type='numeric'
// .Net port of JNBridge for .NET services
name='dotNetClientPort' type='numeric'
// Install path to the .NET services
name='dotNetInstallDir' type='string'
// Protocol for the .NET services.  Possible options: TCP, ??
name='dotNetProtocol' type='string'

// Enable logging for scheduled tasks
name='schedulerLoggingEnabled' type='boolean'
name='schedulerClusterDatasource' type='string'
name='schedulerLogFileExtensions' type='string'
name='scheduledTasks' type='struct'

// Enable Event Gateway Services
name='eventGatewayEnabled' type='boolean'
// Maximum number of events to queue
name='eventGatewayMaxQueueSize' type='numeric'
// Event Gateway Processing Threads
name='eventGatewayThreadpoolSize' type='numeric'
// Event Gateways > Gateway Instances
name='eventGatewayInstances' type='array'
// Event Gateways > Gateway Types
name='eventGatewayConfigurations' type='array'

// Enable WebSocket Service
name='websocketEnabled' type='boolean'


// Enable Flash remoting
name='FlashRemotingEnable' type='boolean'
//  Enable Remote Adobe LiveCycle Data Management access
name='flexDataServicesEnable' type='boolean'
// Enable RMI over SSL for Data Management
name='RMISSLEnable' type='boolean'
// RMI SSL Keystore
name='RMISSLKeystore' type='string'
// RMI SSL Keystore Password
name='RMISSLKeystorePassword' type='string'

// Plain text admin password
name='adminPassword' type='string'
// Plain text admin RDS password
name='adminRDSPassword' type='string'
// True/false is RDS enabled?
name='adminRDSEnabled' type='boolean'
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


// Password required for admin
name='adminLoginRequired' type='boolean'
// Password required for RDS
name='adminRDSLoginRequired' type='boolean'
// user ID required for admin login. False means just a password is required
name='adminUserIDRequired' type='boolean'
// user ID required for RDS login. False means just a password is required
name='adminRDSUserIDRequired' type='boolean'
// Default/root admin user ID
name='adminRootUserID' type='string'
// Allow more than one user to be logged into the same userID at once in the admin
name='adminAllowConcurrentLogin' type='boolean'
// Enable sandbox security
name='sandboxEnabled' type='boolean'
// List of allowed IPs for exposed services.  Formatted like 1.2.3.4,5.6.7.*
name='servicesAllowedIPList' type='string'
// List of allowed IPs for admin access.  Formatted like 1.2.3.4,5.6.7.*
name='adminAllowedIPList' type='string'
// Enable secure profile.  Note, fipping this flag doesn't actually change any of the security settings.  It really just tracks the fact that you've enabled it at some point.
name='secureProfileEnabled' type='boolean'

// License key (only used for Adobe)
name='license' type='string'
// Previous license key (required for an upgrade license key)
name='previousLicense' type='string'

// hashed admin password for Adobe CF11
// TODO: Need to get 10, 11, 2016, and 2018 ironed out here.
name='ACF11Password' type='string'
// hashed RDS password for Adobe CF11
name='ACF11RDSPassword' type='string'
```

