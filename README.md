# Overview

Metrics Collector Service collects statistics for deployment of a github sample code on Cloud Foundry, Kubernetes, Data Science Experience, OpenWhisk etc.

This is Node client for Metrics Collector Service. It is an npm module that can track and report details of a demo/tutorial that has been deployed to Cloud Foundry.

# To Use

1. Open a terminal and run  
   ```
   npm install metrics-tracker-client --save
   ```
2. Require the package in your main entry point to your app (probably app.js).  
    ```
    require("metrics-tracker-client").track();
    ```
3. Add a copy of the Privacy Notice to the readme file. 

   **Note:** All apps that have deployment tracker must include the Privacy Notice.

4. Add a repository.yaml file in the same directory of your main entry point files.


# Example **repository.yaml** file
The repository.yaml need to be written in Yaml format. Also, please put all your keys in lower case.

```
id: https://github.com/IBM/watson-discovery-news
runtimes: 
  - Cloud Foundry
services: 
  - Discovery
event_id: web
event_organizer: dev-journeys
language: nodejs
```

Required field:
1. id: Put your Github URL of your pattern/project.
   - Note: Please put down the Github URL if your pattern is not from **IBM** organization in Github.
2. runtimes: Put down all your platform runtime environments in a list.
3. services: Put down all the IBM Cloud services that are used in your journey in a list.
4. event_id: Put down where you will distribute your application. Default is **web**. 
5. event_organizer: Put down your event organizer if you have one. Default is **dev-journeys**
6. language: If your journey is not in **nodejs**, please put down the application's main language in lower case.

# List of runtimes, services, and languages

Please go to the [service list page](https://github.com/IBM/metrics-collector-service/blob/master/docs/service_list.md) to get the list of official names for runtimes, services, and languages.

# Example app

To see how to include this into your app please visit [Watson Multimedia Analyzer](https://github.com/IBM/watson-multimedia-analyzer).  You will want to pay attention to [package.json](https://github.com/IBM/watson-multimedia-analyzer/blob/master/package.json#L27), [repository.yaml](https://github.com/IBM/watson-multimedia-analyzer/blob/master/repository.yaml), and [app.js](https://github.com/IBM/watson-multimedia-analyzer/blob/master/app.js#L39).

# Privacy Notice

Sample web applications that include this package may be configured to track deployments to [IBM Cloud](https://www.bluemix.net/) and other Cloud Foundry platforms. The following information is sent to a [Deployment Tracker](https://github.com/IBM/metrics-collector-service) service on each deployment:

* Node.js package version
* Node.js repository URL
* Application Name (`application_name`)
* Application GUID (`application_id`)
* Application instance index number (`instance_index`)
* Space ID (`space_id`) or OS username
* Application Version (`application_version`)
* Application URIs (`application_uris`)
* Cloud Foundry API (`cf_api`)
* Labels of bound services
* Number of instances for each bound service and associated plan information
* Metadata in the repository.yaml file

This data is collected from the `package.json` and `repository.yaml` file in the sample application and the `VCAP_APPLICATION` and `VCAP_SERVICES` environment variables in IBM Cloud and other Cloud Foundry platforms. This data is used by IBM to track metrics around deployments of sample applications to IBM Cloud to measure the usefulness of our examples, so that we can continuously improve the content we offer to you. Only deployments of sample applications that include code to ping the Deployment Tracker service will be tracked.

## Disabling Deployment Tracking

Please see the README for the sample application that includes this package for instructions on disabling deployment tracking, as the instructions may vary based on the sample application in which this package is included.
