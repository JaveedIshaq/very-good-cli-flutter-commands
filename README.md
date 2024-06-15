# create Flutter app command
```
very_good create flutter_app flutter_instagram_clone --org "com.farabicoders" --application-id "com.farabicoders.flutter_instagram_cone"
```

# add these 2 values inside
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
``

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
