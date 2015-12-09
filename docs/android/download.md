# Download Campaign Kit for Android

Requirements for use:

* Minimum Android API Level 7.
* Android API Level 18 or higher to use AltBeacon features.
* Android API Level 9 or higher to use Geofencing features.
* Google Play Services library set as a dependency. The library version must be
  within the range of 4.2 - 8.x
* `CampaignKit.properties` file downloaded from
  https://campaignkit.radiusnetworks.com


## Using Android Studio

We suggest using [Android Studio](https://developer.android.com/sdk/index.html)
1.2 or later with [Gradle](http://gradle.org) 2.2.1+. This guide assumes a
default application project layout. `PROJECT_ROOT` is the directory where your
project resides and `app` is the main application module.

1. Download the latest [`.aar` library file](https://github.com/RadiusNetworks/campaignkit-android/releases/latest)
2. Add the library as a dependency to your project
  * Place the `.aar` file into your Android Studio project's `libs/` directory:
    `PROJECT_ROOT/app/libs`.  This should be next to your `src/` folder. If
    there is no `libs/` directory create one.
  * Next to your `src/` and `libs/` folder, there should be a `build.gradle`
    file: `PROJECT_ROOT/app/build.gradle`. Open it and include the following:

    ```gradle
    dependencies {
        compile fileTree(dir: 'libs', include: ['*.jar'])
        compile 'com.radiusnetworks:campaignkit-android:0+@aar'
    }

    repositories {
        jcenter()
        flatDir {
            dirs 'libs'
        }
    }
    ```
3. Setup the `CampaignKit.properties` file
  * Log into https://campaignkit.radiusnetworks.com.
  * Select an existing kit from the drop-down menu or create a new one.
  * Add some content, places, and campaigns.
  * On the Campaign Activity, Kit overview, page click the Android button to
    download the `CampaignKit.properties` file.
  * In Android Studio, import the `CampaignKit.properties` file as an _asset_.
    Alternatively, move the `CampaignKit.properties` file directly into the
    _assets_ directory: `PROJECT_ROOT/app/src/main/asseets`. You may have to
    create this directory first.
4. Adjust the build settings

  In the application module's `build.gradle` file, be sure to set
  `minSdkVersion`, `compileSdkVersion`, `targetSdkVersion`, and
  `buildToolsVersion` according to your requirements.

  ```gradle
  android {
      compileSdkVersion 23
      buildToolsVersion "23.0.2"

      defaultConfig {
          minSdkVersion 7
          targetSdkVersion 23
      }
  }
  ```
5. On the top bar of Android Studio click the "Build" drop down and select
   "Rebuild Project" to make sure everything is configured correctly.

See the [Getting Started](getting-started) guide for details on using Campaign
Kit in your app.


## Using Eclipse

1. Download the latest [.tar.gz library file](https://github.com/RadiusNetworks/campaignkit-android/releases/latest)
2. Add the library as a dependency to your project
  * Double click the `.tar.gz` file, this will produce a directory containing the library.
  * Import the library as an Android Project to your workspace.

    ![alt tag](https://raw.githubusercontent.com/RadiusNetworks/campaignkit-documentation/master/docs/android/screenshots/importing.png)
  * Right-click the library and open the Properties menu.
  * Select the Android tab on the left side of the window.
  * Make sure the library has the "is Library" checkbox checked.

    ![alt tag](https://raw.githubusercontent.com/RadiusNetworks/campaignkit-documentation/master/docs/android/screenshots/cklibrary_islibrary.png)
  * Right-click your project and open the Properties menu.
  * Select the Android tab on the left side of the window.
  * Add the `campaignkit-android` as a library.

    ![alt tag](https://raw.githubusercontent.com/RadiusNetworks/campaignkit-documentation/master/docs/android/screenshots/adding_cklibrary.png)
  * Afterwards, your project's Android properties should look like this:

    ![alt tag](https://raw.githubusercontent.com/RadiusNetworks/campaignkit-documentation/master/docs/android/screenshots/project_settings.png)
3. Setup the `CampaignKit.properties` file
  * Log into https://campaignkit.radiusnetworks.com.
  * Select an existing kit from the drop-down menu or create a new one.
  * Add some content, places, and campaigns.
  * On the Campaign Activity, Kit overview, page click the Android button to
    download the `CampaignKit.properties` file.
  * Move the `CampaignKit.properties` file into the `src/` folder of your project.
4. Adjust Build Settings
  * In the main folder of your project, find the `project.properties` file. On
    a new line, add `manifestmerger.enabled=true`.
  * In the `AndroidManifest.xml`, set the `minSdkVersion` and
    `targetSdkVersion` according to your requirements.

    ```xml
    <uses-sdk
        android:minSdkVersion="7"
        android:targetSdkVersion="19" />
    ```
5. On the top bar of Eclipse click the "Project" drop down, and select
   "Clean..." for all projects.

See the [Getting Started](getting-started) guide for details on using Campaign
Kit in your app.

