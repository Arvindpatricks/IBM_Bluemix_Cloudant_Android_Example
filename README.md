# Example app: Todo App using Cloudant as the Db

The Todo application shows how to do basic CRUD with the Sync Datastore and how to set up a replication between a remote Cloudant database and an application.


## In Brief

Create a database on your Cloudant account for the app to synchronise with. And make sure you create a API Key and Password which can be later used in our App.


For the example below, this database is called `helloworld'.

Gather the following information:

1. Your Cloudant account username.
2. The name of the database set up above.
3. API key set up above.
4. API password set up above.

Add these values to `res/values/settings.xml` as shown:

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="default_user">cloudant_account_name</string>
    <string name="default_dbname">example_app_todo</string>
    <string name="default_api_key">dongshengcn</string>
    <string name="default_api_password">secretpassword</string>
</resources>
```

## Build

You will need [gradle][gradle] 1.8 installed to build the sample application.

[gradle]: http://www.gradle.org/installation

Set up a `local.properties` file in the root folder of the sample app with the location of your Android SDK:

```
sdk.dir=/Users/mike/Code/android/android-sdk-macosx
```


To test your connection, add a couple of tasks and hit "Upload (Push)" from the menu in the top right. You should see the JSON documents appear in your Cloudant database. Changes to the documents in the Cloudant database will be replicated back to the device when you tap "Download (Pull)".

If you see "Replication Error" rather than "Replication Complete" as a popup message, check the logs using `adb` to see what the exception was.

Note : I faced Replication Error due to the wrong host name that was provided. Actually its not wrong, but make sure you dont add the ".cloudant.com" in the host name.
