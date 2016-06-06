
>[action]
>
>1. On the bottom right of the screen, in the `Object Browser`, scroll until you find `Label`
>1. Click and drag the `Label` into the white square in the middle of the screen.
>1. The `Label` should be selected (you can tell by the box with resizing controls) and in the `Utility Area` there should be `Label` controls.

Currently you are in the `Attributes Inspector` part of the `Utility Area`. In this area, you will see all the _Attributes_ of the `UILabel`. In code, these are the external _properties_ that you can set on a `UILabel` object. If you are planning to change those attributes dynamically, you will have to do that in code. But if you are going to set them once, including certain automatic/dynamic settings, you can do that here. Let's jump right in.

>[action]
>
>1. In the `Attributes Inspector` change the `Text` value from `Label` to `Tip Calculator`

Uh oh. The label is too small to display the full text. We could use the little resizing squares to make it the right size, or even the aptly named `Size Inspector` to change its size. But we are going to use this opportunity to get started with the most powerful part of `Interface Builder` that they would have killed for back in 1988. `Constraints` are an important part of a system called `Auto-Layout` that we can use to design our interface once, and have it adjust to different phone sizes. It doesn't stop there, it can help if you want to support rotating the device, or other languages.

>[action]
>
> ---------video---------- label_autolayout.mp4

Let's quickly review what we did there. We added `constraints` to the label, so that its size will be set automatically. We told the label that it should sit 20 pixels from the top, 20 pixels from the left, and 20 from the right. These are not magic numbers, and as you progress, you will get a better idea for how things should look on the screen of a handheld device. Apple has so many thoughts on the subject, that they publish _Human Interface Guidelines_ that you can follow the rules they propose for all _user interfaces_ that you design. Also, in the future you will probably work with designers who will spend large amounts of time thinking about how things should look, and then you can translate their design into the right values for the interface. For now, we have selected `20`.

Next, we are going to need some place for the user to put in the amount of the bill.

>[action]
>
>---------video---------- bill_amount.mp4

Okay, take a deep breath and get ready to do it again.

>[action]
>
>---------video---------- tip_percent.mp4


>[action]
>
>1. run the app and rotate the simulator to see how things move around without pinning and the proper setup


>[action]
>
>1. click the `Segmented Control` and click `Add Missing Constraints`
>1. click the `Tip %:` and click `Add Missing Constraints`


>[action]
>
>1. run the app and see how everything is messed up now. rotate to see again how its messed up. rotate back to see how its consistent at being messed up.


>[action]
>
> video delete_edit_constraints.mp4

Why did they do that? This is programming. In programming, the device does exactly what you tell it to. Nothing more, and nothing less. Most of the time, when something seems unexpected, you will feel like the device actually did more, or less. Almost every single time, that is not the case. Its user error. Now, you may not have been the user that made the error. But since you have built on top of someone else's error, it is at least your problem now. If this error proves to be critical, you will have to _work-around_ it, file a bug report, or maybe even fix it yourself. But we're not talking about low-level components of the operating system here, or even Xcode. We are talking about _auto-layout_! So how do we fix it? More constraints! Keep in mind that these constraints actually boil down to code that gets executed on the target device. So remember, it may feel like using _Microsoft Word_ or _Google Docs_ or even _Pages_ but its actually writing XML in a DSL (_Domain Specific Language_) that has a clear path to code being run. If you don't believe me, hover over (give an example of something in the attributes inspector) and bask in the glory of the Objective-C message equivalent that will actually get run on your users devices.

>[action]
>
>1. video spacing.mp4
>1. hmmm... its still a little off. lets fix that.
>1. video center_vertically.mp4
>1. run the app and see how everything is looking much more consistent. rotate to see again how stays consistent. rotate back to see how its good.

We have previewing our UI by running the app. Which can get annoying if you are working somewhere deep in the app, and want to test it out on multiple devices. You can use the `Assistant Editor` to display a preview of the screen you are working on across multiple devices.

>[action]
>
>1. click on the linked rings/venn diagram (needs screenshot) to open the `Assistant Editor`.
>1. Set it to preview (with screenshot)
>1. Click on the `+` icon on the bottom left of the preview area to add an extra device. Select 'iPhone 5.5 inch'
>1. Click on the `+` icon on the bottom left of the preview area to add an extra device. Select 'iPhone 4 inch'
>1. Close the `Navigation Area` [screenshot for button] to make more space. (or command-0)
>1. Drag the divider between the `editors` to make more space

Now you should have some sample devices without having to launch your code. This is not a perfect solution and may not work when using custom controls you download from the internet or create yourself in the future. There are ways now to make this work with these custom controls, but they may not be worth the tradeoff in time. For now, we decided to have two `iPhone 4 inch` devices so that you can see landscape mode at the same time.


>[action]
>
>------video------- final_controls.mp4

## Running it on your device
