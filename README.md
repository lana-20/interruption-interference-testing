# <img src="https://user-images.githubusercontent.com/70295997/218906095-46afc481-10a9-488a-a724-2c462382cd69.png" width=40> Why Interruption/Interference Configuration is Important in Testing the Mobile App Activities

📝 This post is mostly about Android.

[Why Conduct Interrupt Testing?](https://www.professionalqa.com/interrupt-testing)

<img src="https://user-images.githubusercontent.com/70295997/218905741-a1f5e20e-e7c8-4ee5-a09a-66edc34e1b05.png" width=400>

Interruption Testing is a type of testing that involves simulating various types of interruptions or distractions that a user may experience while using a mobile app. Some common types of interruptions that may be tested include:
- [ ] **Incoming Phone Calls**: If an app is being used and an incoming phone call is received, it’s important to test how the app handles the interruption. Does it pause or stop functioning? Does it allow the user to continue using the app while the call is being taken?
  - For example, simulate a call on an emulator with <code>adb</code>:
  
        adb shell am start -a android.intent.action.CALL
 
  - Or, simulate a call on an emulator with Extended Controls: <img src="https://user-images.githubusercontent.com/70295997/222863470-caa0ea5d-aa6c-4a68-b718-2e0d3f7d12ab.png" width=800>

- [ ] **Incoming Text Messages**: Similar to phone calls, incoming texts can interrupt an app and cause it to pause or close. This type of interruption tests how the app handles an incoming text message while it’s being used and ensures it resumes correctly after the interruption ends.
  - Or, simulate a call on an emulator with Extended Controls: <img src="https://user-images.githubusercontent.com/70295997/222863553-a69d412a-15d7-4589-92a7-db029a6addb1.png" width=800>
  
- [ ] **Notifications or Alarms**: Mobile apps often generate (push) notifications to alert the user of new events or updates. It’s important to test how the app handles notifications and whether the user is able to continue using the app while the notification is being displayed.
- [ ] **System Alerts**: The OS may generate alerts or notifications that interrupt the app. It’s important to test how the app handles these interruptions and whether it allows the user to continue using the app while the alert is being displayed.
- [ ] **System Updates**: If the device’s OS is updated while the app is being used, it can interrupt the app and cause it to close. It’s important to test how the app handles these interruptions and ensure that it can resume correctly after the update is complete.
- [ ] **Low Battery or Power Loss**: If the device’s battery is running low or the device loses power, it can interrupt the app and cause it to close. It’s important to test how the app handles the interruption and whether it allows the user to continue and save all the important data while the device is being charged.
- [ ] **Multitasking / App Switching / Multi-Window**: Many mobile devices allow users to multitask and switch between multiple apps. It’s important to test how the app handles multitasking an whether it allows the user to continue using the app while other apps are being used. App switching tests how the app handles being switched out of the foreground and into the background.
- [ ] **Device Rotation**:  This type of interruption tests how the app handles the device being rotated from portrait to landscape and vice versa.
- [ ] **Network Changes**:  If the device’s network connection changes while the app is being used (e.g. from WiFi to cellular data), it can interrupt the app and cause it to behave differently. It’s important to test how the zoo handles these interruptions and ensure that it functions properly under different network conditions.
It’s crucial to test these types of interruptions that may occur while the app is being used to ensure the app provides smooth, seamless, uninterrupted, stable and consistent user experience.

----

Test the following common scenarios for mobile app testing:
- [ ] ***Rotation*** <img src="https://user-images.githubusercontent.com/70295997/218911298-3c58edef-5015-4b55-9b2c-a300d366aada.png" width=30>
- [ ] ***Multi-window*** <img src="https://user-images.githubusercontent.com/70295997/218907179-6b0588ad-58dd-4e37-a60b-9b86749ee821.png" width=60>
- [ ] ***Language Input*** <img src="https://user-images.githubusercontent.com/70295997/218907607-999608ec-56c8-4274-acd5-e878fb2a3dcd.png" width=30>
- [ ] ***User Taps Back Button***<img src="https://user-images.githubusercontent.com/70295997/218907897-7318ec9d-6c30-449c-b7d1-9348e1f98441.png" width=30>
  * [Override the onBackPressed() method to implement some custom behavior, for example a "confirm-quit" dialog](https://developer.android.com/guide/components/activities/state-changes#back)
- [ ] ***System kills app process*** <img src="https://user-images.githubusercontent.com/70295997/218908294-629df897-917d-4732-a559-d1b2491eee82.png" width=30>


A poorly implemented [Android Lifecycle](https://developer.android.com/guide/components/activities/activity-lifecycle) can lead to the following results:
* **Crashing** <img src="https://user-images.githubusercontent.com/70295997/218911927-3d60dc4b-d9c6-4ce6-83a8-7cd4b9d384c3.png" width=30> if the user **receives a phone call** <img src="https://user-images.githubusercontent.com/70295997/218909704-4e92de01-7d2f-4b84-bbc9-4270b13dd7b4.png" width=30> or **switches to another app** <img src="https://user-images.githubusercontent.com/70295997/218910767-921173bf-9267-4e00-96c7-fc4331613934.png" width=30> while using your app.
* **Consuming** valuable **system resources** <img src="https://user-images.githubusercontent.com/70295997/218910576-a68d8bee-d5f9-41e2-8146-30d3d6ca7722.png" width=30> when the user is not actively using it.
* **Losing the user's progress** <img src="https://user-images.githubusercontent.com/70295997/218911014-3f1424da-30ea-43ac-b91c-bee6690137fe.png" width=30> if they **leave** your app and **return** <img src="https://user-images.githubusercontent.com/70295997/218910074-e5e8fa53-05f9-402f-b532-014ddd957abb.png" width=30> to it at a later time.
* **Crashing** <img src="https://user-images.githubusercontent.com/70295997/218911927-3d60dc4b-d9c6-4ce6-83a8-7cd4b9d384c3.png" width=30> or **losing the user's progress** <img src="https://user-images.githubusercontent.com/70295997/218911014-3f1424da-30ea-43ac-b91c-bee6690137fe.png" width=30> when the **screen rotates** <img src="https://user-images.githubusercontent.com/70295997/218906435-d084f2a4-3720-4959-97b1-584eaa1cf74d.png" width=40> between landscape and portrait orientation.

### [Test your app's activities](https://developer.android.com/guide/components/activities/testing)

Activities serve as containers for every user interaction within your app, so it's important to test how your app's activities behave during device-level events, such as the following:

* Another app, such as the device's phone app, interrupts your app's activity.
* The system destroys and recreates your activity.
* The user places your activity in a new windowing environment, such as picture-in-picture (PIP) or multi-window.

In particular, it's important to ensure that your activity behaves correctly in response to the events described in [Understanding the Activity Lifecycle](https://developer.android.com/guide/components/activities/activity-lifecycle).

Different events, some user-triggered and some system-triggered, can cause an Activity to transition from one state to another. The [Activity State Changes document](https://developer.android.com/guide/components/activities/state-changes) describes some common cases in which such transitions happen, and how to handle those transitions.

----

### Stress and Interrupt Testing
Stress and interrupt testing is an important part of the mobile testing process. With the aid of tools, mobile testers are able to determine any potential performance or stability issues exhibited by an app. To test your app against interrupts, you can manually trigger lots of notifications to the device while using the app. Notifications can be incoming messages, calls, app updates, or push notifications (software interrupts). Furthermore, pressing the volume up and down buttons or any other kind of hardware button is also an interrupt (hardware interrupt) that can also have an impact on your app.

Doing all of these tasks manually is a lot of work and very time-consuming. In most cases, these test scenarios can’t be done manually because it is very hard to simulate fast and multiple user inputs with one or two hands. But it can be done with the aid of tools, and it is really easy to integrate them into the development and testing process.

For Android apps, a tool called [Monkey](https://developer.android.com/studio/test/other-testing-tools/monkey) can be used which is part of the
Android SDK (Software Development Kit). Monkey can run on either a physical device or an emulator. While running, it generates pseudo-random user events such as a touch, click, rotate, swipe, mute, Internet connection shutdown, and much more to stress-test the app and see how it handles all those inputs and interrupts.

The [package name of the Android .apk file](https://github.com/lana-20/android-package-name) is needed to be able to run Monkey; otherwise it will execute its random commands to the entire phone. When the package name (in this case <code>com.appiumpro.the_app</code>) is available, execute Monkey with <code>adb</code> (Android Debug Bridge):

    adb shell monkey -p com.appiumpro.the_app -v 2000

The number 2000 indicates the number of random commands that Monkey will perform. With an additional parameter <code>-s</code> for seed, Monkey will generate the same sequence of events again. This is really important for reproducing a bug that may occur when running Monkey.

The Monkey tool makes it simple to stress- and interrupt-test a mobile application. Besides that, using them is a huge benefit for mobile testers as it helps the team build a reliable and robust mobile app. It’s useful to combine battery testing with stress and interrupt testing to see how the battery is used when lots of interrupts and user inputs are triggered throughout the app.

