# <img src="https://user-images.githubusercontent.com/70295997/218906095-46afc481-10a9-488a-a724-2c462382cd69.png" width=40> Location, Network, Configuration

## Why Interruption/Interference Scenarios are Important in Testing the Mobile App Activities

📝 This post is mostly about Android.

[Why Conduct Interrupt Testing?](https://www.professionalqa.com/interrupt-testing)

<img src="https://user-images.githubusercontent.com/70295997/218905741-a1f5e20e-e7c8-4ee5-a09a-66edc34e1b05.png" width=400>


Test the following common scenarios for mobile app testing:
- [ ] ***Rotation*** <img src="https://user-images.githubusercontent.com/70295997/218911298-3c58edef-5015-4b55-9b2c-a300d366aada.png" width=40>
- [ ] ***Multi-window*** <img src="https://user-images.githubusercontent.com/70295997/218907179-6b0588ad-58dd-4e37-a60b-9b86749ee821.png" width=80>
- [ ] ***Language Input*** <img src="https://user-images.githubusercontent.com/70295997/218907607-999608ec-56c8-4274-acd5-e878fb2a3dcd.png" width=40>
- [ ] ***User Taps Back Button***<img src="https://user-images.githubusercontent.com/70295997/218907897-7318ec9d-6c30-449c-b7d1-9348e1f98441.png" width=40>
  * [Override the onBackPressed() method to implement some custom behavior, for example a "confirm-quit" dialog](https://developer.android.com/guide/components/activities/state-changes#back)
- [ ] ***System kills app process*** <img src="https://user-images.githubusercontent.com/70295997/218908294-629df897-917d-4732-a559-d1b2491eee82.png" width=40>


A poorly implemented [Android Lifecycle](https://developer.android.com/guide/components/activities/activity-lifecycle) can lead to the following results:
* <img src="https://user-images.githubusercontent.com/70295997/218911927-3d60dc4b-d9c6-4ce6-83a8-7cd4b9d384c3.png" width=40> **Crashing** if the user **receives a phone call** <img src="https://user-images.githubusercontent.com/70295997/218909704-4e92de01-7d2f-4b84-bbc9-4270b13dd7b4.png" width=40> or **switches to another app** <img src="https://user-images.githubusercontent.com/70295997/218910767-921173bf-9267-4e00-96c7-fc4331613934.png" width=40> while using your app.
* **Consuming** valuable **system resources** <img src="https://user-images.githubusercontent.com/70295997/218910576-a68d8bee-d5f9-41e2-8146-30d3d6ca7722.png" width=40> when the user is not actively using it.
* **Losing the user's progress** <img src="https://user-images.githubusercontent.com/70295997/218911014-3f1424da-30ea-43ac-b91c-bee6690137fe.png" width=40> if they **leave** your app and **return** <img src="https://user-images.githubusercontent.com/70295997/218910074-e5e8fa53-05f9-402f-b532-014ddd957abb.png" width=40> to it at a later time.
* <img src="https://user-images.githubusercontent.com/70295997/218911927-3d60dc4b-d9c6-4ce6-83a8-7cd4b9d384c3.png" width=40> **Crashing** or **losing the user's progress** <img src="https://user-images.githubusercontent.com/70295997/218911014-3f1424da-30ea-43ac-b91c-bee6690137fe.png" width=40> when the **screen rotates** <img src="https://user-images.githubusercontent.com/70295997/218906435-d084f2a4-3720-4959-97b1-584eaa1cf74d.png" width=40> between landscape and portrait orientation.

### [Test your app's activities](https://developer.android.com/guide/components/activities/testing)

Activities serve as containers for every user interaction within your app, so it's important to test how your app's activities behave during device-level events, such as the following:

* Another app, such as the device's phone app, interrupts your app's activity.
* The system destroys and recreates your activity.
* The user places your activity in a new windowing environment, such as picture-in-picture (PIP) or multi-window.

In particular, it's important to ensure that your activity behaves correctly in response to the events described in [Understanding the Activity Lifecycle](https://developer.android.com/guide/components/activities/activity-lifecycle).

Different events, some user-triggered and some system-triggered, can cause an Activity to transition from one state to another. The [Activity State Changes document](https://developer.android.com/guide/components/activities/state-changes) describes some common cases in which such transitions happen, and how to handle those transitions.
