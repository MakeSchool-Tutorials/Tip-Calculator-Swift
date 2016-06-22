---
title: "Updating the style"
slug: updating-the-style
---

## Adding Assets to an App

All assets used within an iOS app are stored in *Asset catalogs*. Every iOS projects that you create with Xcode comes with one default asset catalog called *Images.xcassets*.

That asset catalog contains one resource for the App's icon. You add new resources to your app by creating new entries (called *Image Sets*) in this asset catalog. You can also create multiple asset catalogs which is useful for apps with huge amounts of images.

Let's briefly discuss some important concepts about asset handling on iOS. You probably have realized that we're providing three different image files for each asset we wanted to use in our App (*@1x*, *@2x* and *@3x*). These different images have different resolutions, each suited to a specific type of iOS devices with a different screen resolution. The *@1x* assets are used for the oldest iOS devices, e.g. iPhone 3Gs, which don't have retina displays. The *@2x* images are used for the 3.5 and 4 inch retina screens of the iPhone 4(S) and iPhone 5(S). Finally, the *@3x* images are used by the iPhone 6 and iPhone 6 Plus. In most cases you won't have to spend too much time thinking about this, as long as you provide assets in all relevant resolutions.

Applications that designers use such as _Sketch_ allow *exporting* all versions at the same time. And applications like _Xcode_ allow *importing* all versions at the same time.

Let's do that now!

> [action]
> ## Importing into Assets.xcassets
> Watch the video and follow the steps below:
>
1. Download the [art pack](https://github.com/MakeSchool-Tutorials/Tip-Calculator-Swift/raw/master/logo.zip) for this tutorial.
1. Unzip the downloaded art pack (by double-clicking the downloaded folder).
1. Select *Assets.xcassets* from the project navigator.
1. Drag the unzipped folder into the empty space.
>
Note: if you don't name the files this way, you have to manually import each version of each asset, and it takes up way more time.
>
![ms-video](https://s3.amazonaws.com/mgwu-misc/TipCalculator/19_add_assets.mp4)

You should also note that we don't reference images in asset catalogs by their file name, but instead by the name of their Image Set. For this project, we only have "logo" but in the future we'll have more.

# Adding the logo

Let's add the Make School logo to our tip calculator!

>[action]
> Watch the video and follow the steps below:
>
1. Open `Main.Storyboard`.
1. Open the layout tree and attribute inspector.
1. Drag an `Image View` from the object browser to just below the calculate button and _into_ the super stack view. It should show a purple line and say super stack view (see video).
1. Set the `image` for the image view to `logo` from the  `Attributes Inspector`.
1. `control` + `click and drag` from the image to the image to set an `aspect ratio` constraint for `1:1` (see video).
1. `control` + `click and drag` from super stack view in the layout tree to the empty white space in the view square and add a `vertical spacing to bottom layout guide` constraint.
1. Select the new constraint, change it's `relation` to `greater than or equal` and it's `constant` to `10`. This will make sure the super stack view will always have a bottom padding of at least `10`.
1. Don't panic yet, but our `calculate` button just disappeared!
>
![ms-video](https://s3.amazonaws.com/mgwu-misc/TipCalculator/20_adding_logo.mp4)

# The case of a disappearing button!

Setting the new constraints to fit a logo made our `calculate` button disappear! If you remember, we never pinned the height for it. Auto-layout has decided to give it a height of `0` so it is no longer showing :( Let's pin a heigh of `40` to bring it back!

>[action]
> Watch the video and follow the steps below:
>
1. Select the `calculate` button from the layout tree view.
1. Open the pin menu, check `height`, and set it to `40`.
1. Press `enter` on your keyboard or click `add 1 constraint`. Our button is back!
1. The app and admire our handy work!
>
![ms-video](https://s3.amazonaws.com/mgwu-misc/TipCalculator/21_fix_button.mp4)

# A splash of color

Now lets add some color to make this app stand out even more.

>[action]
>
1. Select the `Tip Calculator` label.
1. In the `Attributes Inspector` under `View` click on the `Background` attribute. This represents the default setting, which is fully transparent.
1. A color selection window has popped up. Click on the _eye-dropper_ to select the color in the same way a real eye-dropper or turkey baster would suck up liquid. It's on the bottom of the `Colors` palette, and if you have never seen one before, it also looks like a knife.
1. Once you click it, you will notice your cursor has turned into a virtual _loupe_. (The thing jewelers use to look at diamonds, or graphic designers use to look at detail. In this case, both are relevant, since the graphic design we care about, is a diamond.)
1. Move the _loupe_ over the blue part of the _Make School_ logo and click to select that color.
1. Close the colors selector. (It is blocking the next setting we want to click).
1. Now, notice the `Color` setting, currently set to black. Click the right side of that control (the blue part with arrowheads or carets), and select `White Color` from the drop down menu. Or use the _eye-dropper_ to sample white from our logo.
1. Select the `calculate` button and go through the same steps to make the `background` blue and the text white.
1. Run the app and admire how nice it looks with color! ![ms-video](https://s3.amazonaws.com/mgwu-misc/TipCalculator/22_adding_color.mp4)
1. Open `ViewController.swift` and add the following code to make the iPhone status bar a bit prettier:
>
```
override func preferredStatusBarStyle() -> UIStatusBarStyle {
  return .LightContent
}
```

# Changing the keyboard

Now that you have running it on your device, you may have noticed some UX/UI bugs, or areas that we could improve. Lets fix one of them now, but feel free to come back in the future and fix more.

>[action]
>
1. Select the `Bill Amount Field` and using the `Attributes Inspector`, set the `Keyboard Type` to `Decimal Pad`
1. Select the `Tip Amount Field` and using the `Attributes Inspector`, disable this field by unchecking `Enabled` in the `Control` section.
1. Do the same for `Total Amount Field`
>
![ms-video](https://s3.amazonaws.com/mgwu-misc/TipCalculator/23_change_keyboard.mp4)

Wow, now things are looking pretty professional. Nice work for your first app!
