# Demo App for SightCall Classic SDK Integration

## Overview

This repository contains a demo Android application designed to showcase and test the functionalities of the SightCall Classic SDK. The app demonstrates how to effectively integrate the Classic SDK into an Android project.

For detailed documentation and guidance on the SDK, refer to the [official SightCall Android SDK documentation](https://support.sightcall.com/hc/en-us/articles/16101832875668-Android-SDK-Documentation).

## Prerequisites

Before proceeding with the integration, ensure that your project meets the following requirements:

- **Minimum SDK Version**: `minSdkVersion 26`
- **AndroidManifest Configuration**:  
  If your project includes `android:allowBackup="false"` in the `<application>` element of your `AndroidManifest.xml`, you may need to add the following attribute to avoid conflicts:

  ```xml
  <application
      tools:replace="android:allowBackup">


## Implementation

### Using Gradle Version Catalog (Modern Approach)

1. Add the Maven repository for SightCall SDK:

   ```kotlin
   maven("https://sightcall-maven.s3.amazonaws.com")

2. In your `libs.versions.toml` file, define the SDK version and dependency configuration:

   ```toml
    [versions]
    sightcallSdk = "7.5.2" # Replace with the latest version

    [libraries]
    sightcall-sdk = { group = "com.sightcall.universal", name = "universal-sdk", version.ref = "sightcallSdk" }
   
3. Add the dependency to your app-level `build.gradle` file:

    ```kotlin
    implementation(libs.sightcall.sdk)

### Old Way (Without Version Catalog)

If you're not using the Gradle Version Catalog, follow these steps to add the SDK directly:

1. Add the Maven repository for SightCall SDK:

   ```gradle
       allprojects {
        repositories {
            maven {
                url "https://sightcall-maven.s3.amazonaws.com"
            }
        }
     }

2. Add the dependency to your app-level `build.gradle` file:

   ```gradle
   dependencies {
          implementation "com.sightcall.universal:universal-sdk:7.5.2" // Replace with the latest version
    }' 


### Usage

 Start your call using the following code snippet:

```kotlin
        val url = "YOUR_URL_HERE"
        Universal.start(url)