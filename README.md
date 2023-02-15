# Why is Interruption/Interference Important in Testing the Mobile App Activities?

📝 This post is mostly about Android.

[Why Conduct Interrupt Testing?](https://www.professionalqa.com/interrupt-testing)

<img src="https://user-images.githubusercontent.com/70295997/218905741-a1f5e20e-e7c8-4ee5-a09a-66edc34e1b05.png" width=400>


Test the following common scenarios for mobile app testing:
* Rotation
* Multi-window
* Language Input
* User Taps Back Button - [override the onBackPressed() method to implement some custom behavior, for example a "confirm-quit" dialog](https://developer.android.com/guide/components/activities/state-changes#back)
* System kills app process


A poorly implemented [Android Lifecycle](https://developer.android.com/guide/components/activities/activity-lifecycle) can lead to the following results:
* Crashing if the user receives a phone call or switches to another app while using your app.
* Consuming valuable system resources when the user is not actively using it.
* Losing the user's progress if they leave your app and return to it at a later time.
* Crashing or losing the user's progress when the screen rotates between landscape and portrait orientation.


## [Test your app's activities](https://developer.android.com/guide/components/activities/testing)

Activities serve as containers for every user interaction within your app, so it's important to test how your app's activities behave during device-level events, such as the following:

* Another app, such as the device's phone app, interrupts your app's activity.
* The system destroys and recreates your activity.
* The user places your activity in a new windowing environment, such as picture-in-picture (PIP) or multi-window.

In particular, it's important to ensure that your activity behaves correctly in response to the events described in Understanding the Activity Lifecycle.

Different events, some user-triggered and some system-triggered, can cause an Activity to transition from one state to another. The [Activity State Changes document](https://developer.android.com/guide/components/activities/state-changes) describes some common cases in which such transitions happen, and how to handle those transitions.
