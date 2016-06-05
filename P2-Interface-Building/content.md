
[action]
1. On the bottom right of the screen, in the `Object Browser`, scroll until you find `Label`
1. Click and drag the `Label` into the white square in the middle of the screen.
1. The `Label` should be selected (you can tell by the box with resizing controls) and in the `Utility Area` there should be `Label` controls.

Currently you are in the `Attributes Inspector` part of the `Utility Area`. In this area, you will see all the _Attributes_ of the `UILabel`. In code, these are the external _properties_ that you can set on a `UILabel` object. If you are planning to change those attributes dynamically, you will have to do that in code. But if you are going to set them once, including certain automatic/dynamic settings, you can do that here. Let's jump right in.

[action]
1. In the `Attributes Inspector` change the `Text` value from `Label` to `Tip Calculator`

Uh oh. The label is too small to display the full text. We could use the little resizing squares to make it the right size, or even the aptly named `Size Inspector` to change its size. But we are going to use this opportunity to get started with the most powerful part of `Interface Builder` that they would have killed for back in 1988. `Constraints` are an important part of a system called `Auto-Layout` that we can use to design our interface once, and have it adjust to different phone sizes. It doesn't stop there, it can help if you want to support rotating the device, or other languages.

[action]
---------video---------- of adding constraints to the tip calculator label.

Let's quickly review what we did there. We added `constraints` to the label, so that its size will be set automatically. We told the label that it should sit 20 pixels from the top, 20 pixels from the left, and 20 from the right. These are not magic numbers, and as you progress, you will get a better idea for how things should look on the screen of a handheld device. Apple has so many thoughts on the subject, that they publish _Human Interface Guidelines_ that you can follow the rules they propose for all _user interfaces_ that you design. Also, in the future you will probably work with designers who will spend large amounts of time thinking about how things should look, and then you can translate their design into the right values for the interface. For now, we have selected `20`.

Next, we are going to need some place for the user to put in the amount of the bill.

[action]
---------video---------- adding an input with constraints.

[script]: steps for the video
1. type label in the the object browser filter box
1. drag label to the view
1. change label text to `Bill Amount:`
1. right click and drag from label to view. select `center horizontally`
1. choose the `size inspector`
1. change the `align center x to` to `-50` (make sure to hit `-` twice)
1. right click and drag from the label to the `Tip Calculator` label and select `Top`
1. change the `Align Top To: Tip Calculator` to `50`
1. click on the label again and `update frame`
1. clear and type field in the the object browser filter box
1. drag textfield to the view
1. right click and drag from label to view. select `center horizontally`
1. change the `align center x to` to `-50` (make sure to hit `-` twice)
1. right click and drag from the label to the `Tip Calculator` label and select `Top`
1. change the `Align Top To: Tip Calculator` to `50`
1. right click and drag from the label to the `Bill Amount` label and select `Equal Heights`
1. click the `Pin` button and set the `Width` to 75
1. click on the label again and `update frame`

things to explain:
* `Pinning`
* constraints are first class citizens because of OOP.

things that we might have to change:
* separating steps so that we can see why they are required


[script]: steps for the video
1. option click and drag the `Bill Amount:` label down a little bit.
1. double-click the new `Bill Amount:` label and change text to `Tip %:` and then hit enter
1. clear object browser filter and type in `segment`
1. drag segmented control
1. select `Attributes Inspector`
1. Increase number of segments to `3`
1. Double click `First` and change to `15%`
1. Double click `Second` and change to `18%`
1. Double click ` ` (the empty third one) and change to `20%`

[action]
1. run the app and rotate the simulator to see how things move around without pinning and the proper setup


[action]
1. click the `Segmented Control` and click `Add Missing Constraints`
1. click the `Tip %:` and click `Add Missing Constraints`

[action]
1. run the app and see how everything is messed up now. rotate to see again how its messed up. rotate back to see how its consistent at being messed up.


[script]: video for deleting/editing the automatic constraints
1. use shift to select all the `Tip %:` and `15% 18%` constraints. and then hit delete to delete them.
1. right click and drag from `Tip %:` to `Bill Amount:`. select `Leading`.
1. right click and drag from the `Segmented Control` to the `Text Field` select `Trailing`.
1. update frames

content about the UI elements floating to the top. why did they do that? This is programming. In programming, the device does exactly what you tell it to. Nothing more, and nothing less. Most of the time, when something seems unexpected, you will feel like the device actually did more, or less. Almost every single time, that is not the case. Its user error. Now, you may not have been the user that made the error. But since you have built on top of someone else's error, it is at least your problem now. If this error proves to be critical, you will have to _work-around_ it, file a bug report, or maybe even fix it yourself. But we're not talking about low-level components of the operating system here, or even Xcode. We are talking about _auto-layout_! So how do we fix it? More constraints! Keep in mind that these constraints actually boil down to code that gets executed on the target device. So remember, it may feel like using _Microsoft Word_ or _Google Docs_ or even _Pages_ but its actually writing XML in a DSL (_Domain Specific Language_) that has a clear path to code being run. If you don't believe me, hover over (give an example of something in the attributes inspector) and bask in the glory of the Objective-C message equivalent that will actually get run on your users devices.

[script]: video for spacing the new elements to the old ones
1. right click and drag from `Tip %:` to the `Bill Amount` label and select `Top`
1. change the `Align Top To: Bill Amount` to `50`
1. click on the label again and `update frame`
1. right click and drag from from the `Segmented Control` to the `Text Field` and select `Top`
1. change the `Align Top To: Round Style...` to `50`
1. click on the label again and `update frame`

[action]
1. run the app and see how everything is looking much more consistent. rotate to see again how stays consistent. rotate back to see how its good.

preview ui in xcode. other than "update frames" you can use the `Assistant Editor`. talk about the assistant editor.

[action]
1. click on the linked rings/venn diagram (needs screenshot) to open the `Assistant Editor`.
1. Set it to preview (with screenshot)
1. Click on the `+` icon on the bottom left of the preview area to add an extra device. Select 'iPhone 5.5 inch'
1. Click on the `+` icon on the bottom left of the preview area to add an extra device. Select 'iPhone 4 inch'
1. Close the `Navigation Area` [screenshot for button] to make more space. (or command-0)
1. Drag the divider between the `editors` to make more space

now you should have some sample devices without having to launch your code. talk about the limitations of this. talk about having two `iPhone 4 inch` so that you can see landscape mode

[script]: steps for the video
1. option click and drag the `Tip %:` label down a little bit.
1. double-click the new `Tip %:` label and change text to `Tip Amount:` and then hit enter
1. option click and drag the `Tip Amount:` label down a little bit.
1. double-click the new `Tip Amount:` label and change text to `Total Amount:` and then hit enter
1. right click and drag from `Tip Amount:` to the `Tip %` label and select `Top`
1. right click and drag from `Tip Amount:` to the `Tip %` label and select `Leading`
1. change the `Align Top To: Tip %` to `50`
1. right click and drag from `Total Amount:` to the `Tip Amount` label and select `Top`
1. right click and drag from `Total Amount:` to the `Tip Amount` label and select `Leading`
1. change the `Align Top To: Tip Amount` to `50`
1. option click and drag the text field next to the `Bill Amount` label down to line up with the `Tip Amount Label`.
1. right click and drag from the new text field to the view. select `center horizontally`
1. change the `align center x to` to `50`
1. right click and drag from the new text field to the `Tip Amount` label and select `Equal Heights`
1. option click and drag the new text field next to the `Tip Amount` label down to line up with the `Total Amount Label`.
1. right click and drag from the new text field to the view. select `center horizontally`
1. change the `align center x to` to `50`
1. right click and drag from the new text field to the `Total Amount` label and select `Equal Heights`


## Running it on your device
