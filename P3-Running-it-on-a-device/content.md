---
title: "Running it on a device"
slug: on-device-testing
---

Running your code on your device used to be a complicated process that required a paid membership to Apple's Developer Portal. But now, it is literally one click! (With a lot of extra clicks).

>[action]
>
>1. Plug your iOS device into your Mac using a lightning cable.
>1. Unlock your phone and click "trust" if prompted
>1. On the top left section of the _Xcode_ window where it says `iPhone 6S Plus` (or something similar), select your device from the drop down menu. (If it says your device is unavailable because of the version, lower the `Deployment Target` in the project settings).
>1. Click the `Run` button on the top left. It will tell you that there is no team selected, and that you need a team to run on the device.
>1. Let _Xcode_ fix this issue for you by logging in with your `Apple ID` or `iCloud` account. This is the same you use to download apps in the _App Store_. If you do not have an `Apple ID` _Xcode_ will let you create one, and follow the onscreen steps in order to do so.
>1. Click the `Run` button again.
>You may get an error that the device is not available yet because it is processing symbols. If so, there will be a progress bar you can watch while you wait. Then you can run it again.
