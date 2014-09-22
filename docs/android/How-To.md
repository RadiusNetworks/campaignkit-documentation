---
layout: campaignkit
---

#Campaign Kit Library for Android Client

Requirements for use: 

* Android API Level 18 or higher

* Google Play Services library set as a dependency if using Geofencing features.





##If Using Android Studio (we recommend Android Studio v0.8.6 with gradle 1.12):


1) Download the [.aar library file](https://s3.amazonaws.com/campaignkit-android/campaignkit-android-0.0.2.aar)
 

2) Add the library as a dependency to your project

 * Drag and drop the .aar file into your Android Studio Project's "libs" folder. This should be next to your "src" folder. If there is no "libs" folder, create one. 

 * Next to your "src" and "libs" folder, there should be a build.gradle file. Open that and include the following:

```java
  dependencies {
      compile fileTree(dir: 'libs', include: ['*.jar'])
      compile 'com.radiusnetworks:campaignkit-android:0+@aar'
  }

  repositories {
      mavenCentral()
      flatDir {
          dirs 'libs'
      }
  }
```

 * On the top bar of Android Studio click the "Build" drop down, and select "Rebuild project".


3) Implement CampaignKitNotifier and CampaignKitManager

 * Open the Application class in your project. If you don't have one, create a class that extends Application.

 * Type 'extends Application implements CampaignKitNotifier" after the class name in its declaration.

 * Add all required methods for the CampaignKitNotifier. Quick-fix can do this for you.

 * Create an instance of the CampaignKitManager (i.e. CampaignKitManager _ckManager;).

 * In the Application class's onCreate() method, add the following code:

```java 
    _ckManager = CampaignKitManager.getInstanceForApplication(this);
    _ckManager.start();
    _ckManager.setNotifier(this);
``` 

4) Handle didFindCampaign callback from CampaignKitNotifier

```java

  @Override
  public void didFindCampaign(Campaign campaign) {

    //sending notification or alert, depending on whether app is in background or foreground
    new CampaignNotificationBuilder(_mainActivity, campaign)
    .setSmallIcon(R.drawable.ic_launcher)
    .show();
    
    //displaying Campaign content
    showCampaign(campaign);
  }

  public void showCampaign(Campaign campaign){
    // TODO: write custom code or use code from the Campaign Kit reference app
  }
```


##If Using the Eclipse IDE:

1) Download the [.tar.gz library file](https://s3.amazonaws.com/campaignkit-android/campaignkit-android-0.0.2.tar.gz)
campaignkit-android
===================

Campaign Kit Library for Android Client
 
2) Add the library as a dependency to your project

 * Double click the .tar.gz file, this will produce a folder containing the library.

 * Import the library as an Android Project to your workspace.

 * Right-click the library and open the Properties menu.

 * Select the Android tab on the left side of the window.

 * Make sure the library has the "is Library" checkbox checked.

 * Right-click your project and open the Properties menu.

 * Select the Android tab on the left side of the window.

 * Add the campaignkit-android as a library.
 

3) Implement CampaignKitNotifier and CampaignKitManager

 * Create/Open the Application class in your project.

 * Type 'extends Application implements CampaignKitNotifier" in the class declaration.

 * Add all required methods. Quick-fix can do this for you.

 * Create an instance of the CampaignKitManager (i.e. CampaignKitManager _ckManager;).

 * In the Application class's onCreate() method, add the following code:

```java
 
  _ckManager = CampaignKitManager.getInstanceForApplication(this);
  _ckManager.start();
  _ckManager.setNotifier(this);
``` 

4) Handle didFindCampaign callback from CampaignKitNotifier

```java

  @Override
  public void didFindCampaign(Campaign campaign) {

    //sending notification or alert, depending on whether app is in background or foreground
    new CampaignNotificationBuilder(_mainActivity, campaign)
    .setSmallIcon(R.drawable.ic_launcher)
    .show();
    
    //displaying Campaign content
    showCampaign(campaign);
  }

  public void showCampaign(Campaign campaign){
    // TODO: write custom code or use code from the Campaign Kit reference app
  }
``` 




##Adding Geofence Support

Since geofence support is relatively new, it is disabled by default. Below are
the steps necessary to configure a sample app to use geofences through
Campaign Kit.

1) Install Google Play services. Due to the differences between Eclipse and
   Android Studio please refer to the [Google Setup docs](https://developer.android.com/google/play-services/setup.html)
   for the proper IDE instructions.


   - Android SDK Manager > Extras > Google Play services

2) If using Android Studio, Include the Google Play services as a dependency in `app/build.gradle`:

```groovy
  // PROJECT_ROOT/app/build.gradle
  dependencies {
      compile 'com.android.support:appcompat-v7:+'
      compile 'com.google.android.gms:play-services:+'
      compile fileTree(dir: 'libs', include: ['*.jar'])
      compile project(":campaignkit-android")
  }
```

3) Declare the Google Play service in the app's `AndroidManifest.xml` under the
   `<application>` section:

```xml
  <meta-data
      android:name="com.google.android.gms.version"
      android:value="@integer/google_play_services_version" />
```

4) Declare that the app needs to request `ACCESS_FINE_LOCATION`. To request
   this permission, add the following element as a child element of the
   `<manifest>` element:

```groovy
  <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
```

5) Check for Google Play support. For the most recent suggestions by Google,
   please refer to the [Android documentation on checking for Google Play
   services support](https://developer.android.com/google/play-services/setup.html#ensure).

  > Because each app uses Google Play services differently, it's up to you
  > decide the appropriate place in your app to check verify the Google Play
  > services version. For example, if Google Play services is required for your
  > app at all times, you might want to do it when your app first launches. On
  > the other hand, if Google Play services is an optional part of your app,
  > you can check the version only once the user navigates to that portion of
  > your app.
  >
  > To verify the Google Play services version, call
  > `isGooglePlayServicesAvailable()`. If the result code is `SUCCESS`, then
  > the Google Play services APK is up-to-date and you can continue to make a
  > connection. If, however, the result code is `SERVICE_MISSING`,
  > `SERVICE_VERSION_UPDATE_REQUIRED`, or `SERVICE_DISABLED`, then the user
  > needs to install an update. So, call
  > `GooglePlayServicesUtil.getErrorDialog()` and pass it the result error
  > code. This returns a `Dialog` you should show, which provides an
  > appropriate message about the error and provides an action that takes the
  > user to Google Play Store to install the update.


```java

  /**
   * Verify that Google Play services is available before making a request.
   *
   * @return true if Google Play services is available, otherwise false
   */
  private boolean servicesConnected() {

      // Check that Google Play services is available
      int resultCode =
              GooglePlayServicesUtil.isGooglePlayServicesAvailable(this);

      // If Google Play services is available
      if (ConnectionResult.SUCCESS == resultCode) {

          // In debug mode, log the status
          Log.d(TAG, "Google Play services available");

          // Continue
          return true;

      // Google Play services was not available for some reason
      } else {

          // Display an error dialog
          Dialog dialog = GooglePlayServicesUtil.getErrorDialog(resultCode, this, 0);
          if (dialog != null) {
              ErrorDialogFragment errorFragment = new ErrorDialogFragment();
              errorFragment.setDialog(dialog);
              errorFragment.show(getSupportFragmentManager(), TAG);
          }
          return false;
      }
  }

  /**
   * Define a DialogFragment to display the error dialog generated in
   * showErrorDialog.
   */
  public static class ErrorDialogFragment extends DialogFragment {

      // Global field to contain the error dialog
      private Dialog mDialog;

      /**
       * Default constructor. Sets the dialog field to null
       */
      public ErrorDialogFragment() {
          super();
          mDialog = null;
      }

      /**
       * Set the dialog to display
       *
       * @param dialog An error dialog
       */
      public void setDialog(Dialog dialog) {
          mDialog = dialog;
      }

      /*
       * This method must return a Dialog to the DialogFragment.
       */
      @Override
      public Dialog onCreateDialog(Bundle savedInstanceState) {
          return mDialog;
      }
  }

```

6) If Google Play is available, enable geofences for Campaign Kit.

```java

  ckManager = CampaignKitManager.getInstanceForApplication(this);
  if (servicesConnected()) {
      try {
          ckManager.enableGeofences();
      } catch (GooglePlayServicesException e) {
          Log.e(TAG, "Failed to enable geofences: " + e.getMessage());
      }
  }
  ckManager.setNotifier(this);
  ckManager.start()

```
