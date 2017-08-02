# CommandBox Server Interceptors

The CommandBox CLI module will automatically register several interceptors that listen for server starts and stops.  This allows you to automate your configuration without needing to manually load settings.

This functionality only applies to servers that are started in CommandBox.  Examples would be using CommandBox for local development, deploying our Docker images or Heroku buildpacks.

You can use the CFConfig commands to manually import/export configuration on 'standard' CF installs, but these automatic interceptors here don't apply.  