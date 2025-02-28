# Flutter App Creation Command

Create a new Flutter application using Very Good CLI with proper organization and application ID:

```bash
very_good create flutter_app flutter_instagram_clone --org "com.farabicoders" --application-id "com.farabicoders.flutter_instagram_clone"
```

**Parameters explained:**
- `flutter_instagram_clone`: The name of your Flutter application
- `--org`: Specifies the organization name in reverse domain notation
- `--application-id`: Sets the unique identifier for your application (used in Android and iOS)

# Localization Setup

## Generate Localization Files
Run the following command to generate localization files for your Flutter app:

```bash
flutter gen-l10n
```

This command generates the necessary Dart classes for handling translations in your app.

## Configure l10n.yaml
Add the following configuration to your `l10n.yaml` file:

```yaml
use-escaping: true    # Enables string escaping in translations
synthetic-package: false    # Generates real Dart files instead of synthetic packages
```

# Android Setup

## Gradle Configuration
Update the following values in `android/app/build.gradle` to set proper Android SDK versions:

```gradle
compileSdkVersion 34    # Latest Android SDK version for compilation
minSdkVersion 21        # Minimum Android version supported (Android 5.0)
```

These settings ensure:
- Your app can use modern Android features (compileSdkVersion)
- Your app runs on Android 5.0 and newer devices (minSdkVersion)

## Android Permissions
Add these permissions to your `AndroidManifest.xml` file as needed:

```xml
<!-- Network Permissions -->
<uses-permission android:name="android.permission.INTERNET" />                    <!-- Required for internet access -->
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />        <!-- Required for checking network connectivity -->

<!-- Media Permissions -->
<uses-permission android:name="android.permission.READ_MEDIA_IMAGES" />           <!-- For accessing images on Android 13+ -->
<uses-permission android:name="android.permission.READ_MEDIA_VIDEO" />            <!-- For accessing videos on Android 13+ -->
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />       <!-- For accessing storage on older Android versions -->
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>       <!-- For writing to storage -->
<uses-permission android:name="android.permission.MANAGE_EXTERNAL_STORAGE" />     <!-- For managing files on Android 11+ -->

<!-- Hardware Permissions -->
<uses-permission android:name="android.permission.VIBRATE"/>                      <!-- For haptic feedback -->
```



## Application Configuration
Update your `AndroidManifest.xml` file's application tag with these properties:

```xml
<application
    android:label="${appName}"
    android:name="${applicationName}"
    android:icon="@mipmap/ic_launcher"
    android:enableOnBackInvokedCallback="true"
    android:requestLegacyExternalStorage="true">
```

**Properties explained:**

- `android:enableOnBackInvokedCallback="true"`
  - Enables the new Android 13+ back navigation system
  - Provides consistent back gesture handling across Android versions
  - Required for modern Android navigation patterns

- `android:requestLegacyExternalStorage="true"`
  - Enables broad storage access on Android 10 (API level 29)
  - Maintains compatibility with older storage access patterns
  - **Note:** Consider migrating to modern storage access APIs for Android 11+ compatibility


## Firebase Cloud Messaging Configuration

Add this meta-data tag to your `AndroidManifest.xml` to configure Firebase Cloud Messaging (FCM):

```xml
<meta-data
    android:name="com.google.firebase.messaging.default_notification_channel_id"
    android:value="chat_channel"
/> 
```

**Purpose:**
- Defines the default notification channel for FCM notifications
- Required for Android 8.0 (API level 26) and higher
- `chat_channel` is your custom channel ID that you'll create in your app's notification setup

## Intent Filters Configuration

Add these intent filters to your `AndroidManifest.xml` inside the `<activity>` tag:

```xml
<!-- Deep Link Handler -->
<intent-filter>
    <action android:name="android.intent.action.VIEW" />
    <category android:name="android.intent.category.DEFAULT" />
    <category android:name="android.intent.category.BROWSABLE" />
    
    <!-- URI Scheme Configuration -->
    <data
        android:scheme="io.supabase.flutterquickstart"
        android:host="login-callback" 
    />
</intent-filter>

<!-- FCM Notification Click Handler -->
<intent-filter>
    <action android:name="FLUTTER_NOTIFICATION_CLICK" />
    <category android:name="android.intent.category.DEFAULT" />
</intent-filter>
```

**Purpose of each filter:**

1. **Deep Link Handler**
   - Enables app to respond to custom URL schemes
   - Handles authentication callbacks
   - Makes the app browsable from web links

2. **FCM Notification Handler**
   - Captures notification click events
   - Enables proper navigation when user taps on notifications

## Package Dependencies Management

To update dependencies in a monorepo structure, use:

```bash
very_good packages get --recursive
```

**What this command does:**
- Recursively searches through all packages in your project
- Runs `flutter pub get` in each package directory
- Updates dependencies for the main app and all sub-packages
- Ensures consistency across your entire project structure

**When to use:**
- After adding new dependencies
- When switching branches with different dependencies
- After pulling updates from your repository
- When setting up the project for the first time
