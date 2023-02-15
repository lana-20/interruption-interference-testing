# Why is Interruption/Interference Important in Testing the Mobile App Activities?

📝 This post is mostly about Android.

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
