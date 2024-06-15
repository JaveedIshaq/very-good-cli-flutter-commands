# create Flutter app command
```
very_good create flutter_app flutter_instagram_clone --org "com.farabicoders" --application-id "com.farabicoders.flutter_instagram_cone"
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
