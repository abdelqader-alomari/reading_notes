# Read: 41 - Intent Filters

![Intent Filters](https://th.bing.com/th/id/R.957da468b815f81b44f3d8a92bc35ab4?rik=o0rB1gnTftoqmg&riu=http%3a%2f%2fwww.wideskills.com%2fsites%2fdefault%2ffiles%2fsubjects%2fandroid%2fchapter3%2f3_2%2fImage_3_2_4.png&ehk=92nVRZZgeaJ3HrTG%2bcltD6HAWZJBmQ1X4gT4BXfjqRg%3d&risl=&pid=ImgRaw&r=0)

## What is Intent Filter and why to use it?

Intent Filter specifies the types of intents that an activity, service, or broadcast receiver can respond to. An intent filter declares the capabilities of its parent component — what an activity or service can do and what types of broadcasts a receiver can handle. It opens the component to receiving intents of the advertised type, while filtering out those that are not meaningful for the component.
Most of the contents of the filter are described by its `<action>`, `<category>`, and `<data>` subelements.

## Allowing Other Apps to Start Your Activity

To allow other apps to start your activity, you need to add an `<intent-filter>` element in your manifest file for the corresponding `<activity>` element.

When your app is installed on a device, the system identifies your intent filters and adds the information to an internal catalog of intents supported by all installed apps. When an app calls startActivity() or startActivityForResult(), with an implicit intent, the system finds which activity (or activities) can respond to the intent.

### Add an Intent Filter

In order to properly define which intents your activity can handle, each intent filter you add should be as specific as possible in terms of the type of action and data the activity accepts.

#### Action

A string naming the action to perform. Usually one of the platform-defined values such as ACTION_SEND or ACTION_VIEW.
Specify this in your intent filter with the `<action>` element. The value you specify in this element must be the full string name for the action

#### Data

A description of the data associated with the intent

`<data>` Using one or more attributes in this element, you can specify just the MIME type, just a URI prefix, just a URI scheme, or a combination of these and others that indicate the data type accepted.

#### Category

Provides an additional way to characterize the activity handling the intent, usually related to the user gesture or location from which it's started. All implicit intents are defined with CATEGORY_DEFAULT by default.
Specify this in your intent filter with the `<category>` element.

In your intent filter, you can declare which criteria your activity accepts by declaring each of them with corresponding XML elements nested in the `<intent-filter>` element.

### Handle the Intent in Your Activity

As your activity starts, call getIntent() to retrieve the Intent that started the activity. You can do so at any time during the lifecycle of the activity, but you should generally do so during early callbacks such as onCreate() or onStart().


### Example of using Intent Filter in manifest

```
<activity android:name="ShareActivity">
    <!-- filter for sending text; accepts SENDTO action with sms URI schemes -->
    <intent-filter>
        <action android:name="android.intent.action.SENDTO"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:scheme="sms" />
        <data android:scheme="smsto" />
    </intent-filter>
    <!-- filter for sending text or images; accepts SEND action and text or image data -->
    <intent-filter>
        <action android:name="android.intent.action.SEND"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:mimeType="image/*"/>
        <data android:mimeType="text/plain"/>
    </intent-filter>
</activity>
```
