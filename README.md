# Plexus-Gradle-Plugin

This Gradle plugin helps make the [Plexus Messaging SDK](https://github.com/plexusinc/PlexusMessaging) compatible with your Android Studio / Gradle project. It automatically fixes and notifies you of required changes to make the Plexus Messaging SDK compatible with your app.

## Setup
1. In your root `build.gradle`, under `buildscript`, add the following 2 new lines to your existing `repositories` and `dependencies` sections
```gradle
buildscript {
    repositories {
        // ...
        maven { url 'https://plugins.gradle.org/m2/' } // Gradle Plugin Portal 
    }
    dependencies {
        // ...
        // Plexus-Gradle-Plugin
        classpath 'gradle.plugin.com.plexus.gradle.plexus-gradle-plugin:1.0'
    }
}
```
2. Add the following to the top of your `app/build.gradle`
```gradle
apply plugin: 'com.plexus.gradle.plexus-gradle-plugin'
```
3. Android Studio - Sync gradle
4. Clean and rebuild

## Features
- Automatically aligns versions of module dependencies under the same group. This fixes compile and runtime errors due to mismatched interdependencies.
Applies to the following libraries:
  - `com.google.android.gms`
  - `com.google.firebase`
  - `com.android.support`
- Ensures `com.android.support` is never higher than `compileSdkVersion`
- Ensures a compatible Plexus Messaging SDK version for the `targetSdkVersion` you're using
- Ensures new enough Plexus Messaging SDK is included when `com.android.support` is upgraded
- Calculates intersecting range of 2 version ranges
   - Including backwards capability with Gradle 2.14.1
- Future: Other warnings and checks specific to OneSignal such as app_id and notification icons

## Compatibility
* Recommend using AGP 3.0.0 or newer ([Android Gradle Plugin](https://developer.android.com/studio/releases/gradle-plugin)) and Gradle 4.1 or newer.
  - Compatible with Gradle 2.14.1+ and AGP 2.2.3+
  - Tested up to Gradle 6.7.1 and AGP 4.1.1
