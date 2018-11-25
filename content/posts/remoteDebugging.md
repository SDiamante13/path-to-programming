+++ 
draft = false
date = 2018-10-16T10:37:44-05:00
title = "Remote Debugging PCF Apps"
slug = "" 
tags = ["PCF", "Debug"]
+++

# Remote Debugging 

We all know how to debug locally, but have you ever had an application or database running on a remote server and ever wondered if you could debug that. 

Well let me tell you it is possible. 

We try our hardest to have parity among our production and lower environments, but sometimes an exact replica can not be achieved.

An example of one application at my company that could benefit from remote debugging a Production instance is the Mobile Server Team. They experience rare login issues that are difficult to replicate in the lower environments. 

Today I will go through the simple tasks to set up a SSH tunnel from your IntelliJ IDE to the PCF instance.

## Setup a simple project to test

To test out remote debugging on a simple project, you can navigate to [start.spring.io]https://start.spring.io You can configure your simple rest controller.

[Controller] (/images/controller.png)

## Configuration

To deploy your app to PCF you will need to include a file called: `manifest.yml`

Here is a sample `manifest.yml`:

![Manifest] (/images/manifest.png)

Please add the following line:

```
env:
JBP_CONFIG_DEBUG: '{enabled: true}'
```

This will enable your PCF instance to be debuggable.

##### **NOTE**: It is also possible to include this environment variable in the PCF dashboard under the User Provided Environment Variables drop-down menu.

### Set up IntelliJ IDEA for Remote Debugging

##### Navigate to:

> \>Run \> Edit Configurations...

Select `+` and choose `Remote`
 
##### Under Command Line Arguments for running JVM you should see:

```
-agentlib:jdwp=transport=dt_socket,
server=y,suspend=n,address=8000
```

##### Under settings change host and port if not already set:

```
host: localhost     port: 8000
```


## Deploy and set up SSH tunnel

Now you can redeploy your app with the debug configuration enabled. You may carry this out with your favorite CI/CD or from the PCF CLI with

`cf push <my-app>`

Next you must set up an SSH tunnel between your IDE and the PCF instance by running the following command in your terminal:

`cf ssh  -L 8000:localhost:8000 remote-debug`

If the port is not blocked you will have a secure connection to the PCF instance.

## Debug

* Now set up some breakpoints in the area you would like to debug
* Run the debug configuration from IntelliJ we set up
* Hit the endpoint in question and watch the IDE take over

## Production

#### There are some caveats to remote debugging a production instance:

* To add the debug configuration environment variable you must restart the application which leads to down time
* After debugging you should remove the debug configuration due to security issues
* If you have configured your PCF application to have multiple instances it may be more difficult to set up the SSH tunnel








