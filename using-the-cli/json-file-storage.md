# JSON File Storage

CFConfig can represent the settings for any server in a generic JSON format. Even though some settings may be specific to Lucee Server or Adobe ColdFusion, the JSON format itself is generic and can be used on any engine. Any settings that don't apply to a given engine will simply be ignored. For example, caches or mail servers past the first one are ignored when importing to Adobe ColdFusion.

### Automatically Deploying Saved Configurations  
You may choose to commit your settings to a file called `.cfconfig.json` in the webroot, which will cause them to automatically get loaded in on every server start. This is the easiest way to share configuration with your coworkers. One issue with this may be that you don't want the json file in your web root in case it accidentally gets moved to a production server and it directly accessible. Web servers such as Apache will not serve files starting with `.` by default, but other web servers will happily share those "hidden" files. You can work around this by placing the JSON file outside the web root and using the `cfconfigFile` property in your `server.json` to point to it. You can use relative paths like `../build/mySettings.json`.

#### Dynamic Values and System Settings  
Another potential issue with the JSON file is that you may have secrets in your config such as passwords that you don't want to commit to your repo or that are simply different on some servers. You can manage this by using CommandBox's "system settings" which will expand any environment variables in your CFConfig JSON file. System settings are in the format `${mySetting}` and would look like so in your JSON file:

```javascript
{
  "adminPassword" : "${LOCAL_DEV_CF_PASS}"
}
```

That JSON above would automatically replace the `adminPassword` setting with the value of an environment variable called `LOCAL_DEV_CF_PASS`.

You can take this a step further and provide a default value so the env var is just an override. The format is `${name:default}`.

```javascript
{
"requestTimeout" : "${LOCAL_DEV_TIMEOUT:0,0,1,0}"
}
```

That JSON above would set the request timeout to 1 minute unless it was overridden by an env var called `LOCAL_DEV_TIMEOUT`.

#### Handling Scheduled Tasks  
Since scheduled tasks are also managed by CFConfig, any running tasks on the source server will be running on the destination server which might not be desirable. Use these techniques to pause tasks:

In conjunction with the `cfconfigFile` in `server.json`, set the `CFConfigPauseTasks` setting to true with ```server set CFConfigPauseTasks=true```. 

When using CFConfig to import, export or transfer settings use the `--pauseTasks` flag i.e. ```cfconfig import myConfig.json --pauseTasks```. 
