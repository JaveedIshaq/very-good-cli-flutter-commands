# create Flutter app command
```
very_good create flutter_app flutter_instagram_clone --org "com.farabicoders" --application-id "com.farabicoders.flutter_instagram_clone"
```

# run flutter gen-l10n command to create loacalizations
```
flutter gen-l10n
```

# add following values into l10n.yaml
```
use-escaping: true
synthetic-package: false
```

# Android Setup

# update in app/build.gradle
```
compileSdkVersion 34
minSdkVersion 21
```

## Add any of Required permissions for Android

```
   <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.READ_MEDIA_IMAGES" />
    <uses-permission android:name="android.permission.READ_MEDIA_VIDEO" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE>" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.MANAGE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.VIBRATE"/>
```



# update the following in AndroidManifest.xml
`
 android:enableOnBackInvokedCallback="true"
 `
 `
 android:requestLegacyExternalStorage="true"
 `
in

```
   <application
        android:label="${appName}"
        android:name="${applicationName}"
        android:icon="@mipmap/ic_launcher"
        android:enableOnBackInvokedCallback="true"
        android:requestLegacyExternalStorage="true">
```

<pre>
   android:enableOnBackInvokedCallback="true": This property enables the onBackInvoked callback for the application. It means that when the user presses the back button, the application can handle the back navigation event.
   android:requestLegacyExternalStorage="true": This property requests legacy external storage access for the application. It allows the application to access external storage, such as SD cards, directly instead of using the modern storage system. Note that this property is 
    deprecated in newer versions of Android and it is recommended to use the modern storage system instead.
</pre>


# Add  Meta Data Tag for to configure the default notification channel ID for Firebase Cloud Messaging (FCM) notifications in an Android app.

```
<!-- to configure the default notification channel ID for Firebase Cloud Messaging (FCM) notifications in an Android app. -->
            <meta-data
              android:name="com.google.firebase.messaging.default_notification_channel_id"
              android:value="chat_channel"
              /> 

```

# Add intent Filters

```
  <intent-filter>
                <action android:name="android.intent.action.VIEW" />
                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />
                <!-- Accepts URIs that begin with YOUR_SCHEME://YOUR_HOST -->
                <data
                android:scheme="io.supabase.flutterquickstart"
                android:host="login-callback" />
            </intent-filter>
            <intent-filter> 
                <action android:name="FLUTTER_NOTIFICATION_CLICK" /> 
                <category android:name="android.intent.category.DEFAULT" /> 
            </intent-filter>
```

## very_good packages get --recursive

```
To recursively get dependencies for all packages in a Dart/Flutter monorepo using the Very Good CLI, you can use the very_good packages get --recursive command. This command automatically traverses through your project directory and runs flutter pub get for each package it finds.
```
