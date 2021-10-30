# Read: 26 - Android Fundamentals

## Application Fundamentals

![Anroid](https://udemydegree.com/wp-content/uploads/2021/10/Android-Application-Development-Certification-2021-2048x1152.jpg)

Android apps can be written using Kotlin, Java, and C++ languages. The Android SDK tools compile your code along with any data and resource files into an APK or an Android App Bundle.

An Android package, which is an archive file with an .apk suffix, contains the contents of an Android app that are required at runtime and it is the file that Android-powered devices use to install the app.

- The Android operating system is a multi-user Linux system in which each app is a different user.

- By default, the system assigns each app a unique Linux user ID (the ID is used only by the system and is unknown to the app). The system sets permissions for all the files in an app so that only the user ID assigned to that app can access them.
- Each process has its own virtual machine (VM), so an app's code runs in isolation from other apps.
- By default, every app runs in its own Linux process. The Android system starts the process when any of the app's components need to be executed, and then shuts down the process when it's no longer needed or when the system must recover memory for other apps.
  This creates a very secure environment in which an app cannot access parts of the system for which it is not given permission.

## App Components

There are four different types of app components:

- Activities: entry point for interacting with the user. It represents a single screen with a user interface
  activity facilitate:

  - Keeping track of what the user currently cares about (what is on screen);
  - Knowing that previously used processes contain things the user may return to (stopped activities).
  - Helping the app handle having its process killed so the user can return to activities with their previous state.
  - Providing a way for apps to implement user flows between each other, and for the system to coordinate these flows.

- Services: general-purpose entry point for keeping an app running in the background for all kinds of reasons
- Broadcast receivers: component that enables the system to deliver events to the app outside of a regular user flow, allowing the app to respond to system-wide broadcast announcements
- Content providers : manages a shared set of app data that you can store in the file system, in a SQLite database, on the web, or on any other persistent storage location that your app can access.

Each type serves a distinct purpose and has a distinct lifecycle that defines how the component is created and destroyed.

## Activating components

![](https://d2h0cx97tjks2p.cloudfront.net/blogs/wp-content/uploads/sites/2/2019/02/Android-Activity-back-stack.png)

Three of the four component types—activities, services, and broadcast receivers—are activated by an asynchronous message called an intent. Intents bind individual components to each other at runtime.

An intent is created with an Intent object, which defines a message to activate either a specific component (explicit intent) or a specific type of component (implicit intent).

- You can start an activity or give it something new to do by passing an Intent to startActivity() or startActivityForResult() (when you want the activity to return a result).
- With Android 5.0 (API level 21) and later, you can use the JobScheduler class to schedule actions. For earlier Android versions, you can start a service (or give new instructions to an ongoing service) by passing an Intent to startService(). You can bind to the service by passing an Intent to bindService().
- You can initiate a broadcast by passing an Intent to methods such as sendBroadcast(), sendOrderedBroadcast(), or sendStickyBroadcast().
- You can perform a query to a content provider by calling query() on a ContentResolver.

## The manifest file

`AndroidManifest.xml` app must declare all components in this file, which must be at the root of the app project directory

The manifest does a number of things in addition to declaring the app's components, such as the following:

- Identifies any user permissions the app requires, such as Internet access or read-access to the user's contacts.
- Declares the minimum API Level required by the app, based on which APIs the app uses.
- Declares hardware and software features used or required by the app, such as a camera, or a multitouch screen.
- Declares API libraries the app needs to be linked against, such as the Google Maps library.

## Declare Components

```
<?xml version="1.0" encoding="utf-8"?>
<manifest ... >
    <application android:icon="@drawable/app_icon.png" ... >
        <activity android:name="com.example.project.ExampleActivity"
                  android:label="@string/example_label" ... >
        </activity>
        ...
    </application>
</manifest>
```

- In the `<application>` element, the android:icon attribute points to resources for an icon that identifies the app.

- In the `<activity`> element, the android:name attribute specifies the fully qualified class name of the Activity subclass and the android:label attribute specifies a string to use as the user-visible label for the activity.

You must declare all app components using the following elements:

- `<activity>` elements for activities.
- `<service>` elements for services.
- `<receiver>` elements for broadcast receivers.
- `<provider>` elements for content providers.

---

## Resources:

[Android fundamentals](https://developer.android.com/guide/components/fundamentals)
