
Segment 3: (ironically named after making 3 segments)



>[action]
>
>1. click on the linked rings above the `Preview` in the `Assistant Editor` and change it to `Automatic`. It should now show `ViewController.swift` in the `Assistant Editor`. You can verify this by finding our `print("Hello World")` line.
>1. Drag the divider between the `editors` to make more space
>1. Close the `Debugger Area` (icon screenshot) or command-shift-y

[script]: steps for wiring it up:
1. control click drag from `bill amount` label to under the `class ViewController` line and call the field `billAmountField`
1. control click drag from the `% selector` and call the field `tipSelector`
1. control click drag from the `tip amount` label and call the field `tipAmountField`
1. control click drag from the `total amount` label and call the field `totalAmountField`
1. control click drag from `bill amount` label to and choose `Action` and `Value Changed` and call it `billAmountChanged`
1. control click drag from `tip selector` label to and choose `Action` and `Value Changed` and call it `tipChanged`
1. add some space between the functions

>[action]
>
>1. Overwrite the two new functions you created with the code below
>
>  @IBAction func billAmountChanged(sender: AnyObject) {
      guard Double(billAmountField.text!) != nil else {
        //show error
        tipAmountField.text = ""
        totalAmountField.text = ""
        return
      }
>
      var tipPercentage = 0.0
>
      switch tipSelector.selectedSegmentIndex {
      case 0:
        tipPercentage = 0.15
      case 1:
        tipPercentage = 0.18
      case 2:
        tipPercentage = 0.20
      default:
        break
      }
>
      let billAmount = Double(billAmountField.text!)!
      let roundedBillAmount = round(100*billAmount)/100
      let tipAmount = roundedBillAmount * tipPercentage
      let roundedTipAmount = round(100*tipAmount)/100
      let totalAmount = roundedBillAmount + roundedTipAmount
>
>
      if (!billAmountField.editing) {
        billAmountField.text = String(format: "%.2f", roundedBillAmount)
      }
      tipAmountField.text = String(format: "%.2f", roundedTipAmount)
      totalAmountField.text = String(format: "%.2f", totalAmount)
>
>
    }
>
    @IBAction func tipChanged(sender: AnyObject) {
    }



## Unlinking

If you look at the code we wrote for `billAmountChanged` it can look at all the inputs (not just the `Bill Amount`) but the `Tip% Selector` as well. So lets link up the `Tip% Selector` to `billAmountChanged` and delete `tipChanged`.


Now, lets test it out...

>[action]
>
>1. Run the project
>1. Type in a bill amount
>1. Click `18%`
>1. It crashed!!!!

Why did it crash? Very simple, your `Main.storyboard` has the `Tip % Selector` wired up to two functions, and when it called one of them, it crashed. `reason: -[TipPro.ViewController tipChanged:]: unrecognized selector sent` This is objective-c syntax for `message passing` which in Swift, would be the equivalent of calling a function. Think of it as `ViewController.tipChanged(something)`. It crashed because that doesn't exist. So lets unlink it, and try again.

>[action]
>
>1. Open `Main.storyboard`
>1. Right(control)-click on the `Tip % Selector`
>1. In the pop-up window [screenshot] click the `X` next to `Value Changed` that says `ViewController tipChanged`. Close the pop-up.
>1. Since we already have the function defined that we want to connect to, right(control)-click and drag from the `Tip % Selector` to the `View Controller` in the _hierarchy_ of your storyboard under `View Controller Scene`.
>1. Select `billAmountChanged`
>1. Run
>1. Type in a bill amount
>1. Click `18%`
>1. Success!!!


Now, lets change `billAmountChanged` to `updateTip`. For this, try it on your own first. It is ok, if you wound up doing something different then these instructions, as long as it works.

>[action]
>
>1. Open `ViewController.swift`
>1. Rename `billAmountChanged` to `updateTip`
>1. Open `Main.storyboard`
>1. Right(control)-click on the `Bill Amount `
>1. In the pop-up window click the `X` next to `Editing did end` that says `ViewController billAmountChanged` and click the `X` next to `Editing Changed` that says `ViewController billAmountChanged`.
>1. Drag from the circle next to `Editing Changed`  to the `View Controller` in the _hierarchy_. Let go and select `updateTip`
>1. Drag from the circle next to `Editing did End`  to the `View Controller` in the _hierarchy_. Let go and select `updateTip`
>1. Close the pop-up.
>1. Right(control)-click on the `Tip % Selector`
>1. In the pop-up window click the `X` next to `Value Changed` that says `ViewController billAmountChanged`.
>1. Drag from the circle next to `Value Changed` to the `View Controller` in the _hierarchy_. Let go and select `updateTip`
>1. Close the pop-up.



## Update the styles

##Adding Assets to an App

> [action]
> TODO: update the link
[Download the art pack for this tutorial!](https://s3.amazonaws.com/mgwu-misc/SA2015/Makestagram_Art.zip)

All assets used within an iOS app are stored in *Asset catalogs*. Every iOS projects that you create with Xcode comes with one default asset catalog called *Images.xcassets*:

![image](asset_catalog.png)

That asset catalog contains one resource for the App's icon. You add new resources to your app by creating new entries (called *Image Sets*) in this asset catalog. You can also create multiple asset catalogs which is useful for apps with huge amounts of images.

Let's briefly discuss some important concepts about asset handling on iOS. You probably have realized that we're providing three different image files for each asset we wanted to use in our App (*@1x*, *@2x* and *@3x*). These different images have different resolutions, each suited to a specific type of iOS devices with a different screen resolution. The *@1x* assets are used for the oldest iOS devices, e.g. iPhone 3Gs, which don't have retina displays. The *@2x* images are used for the 3.5 and 4 inch retina screens of the iPhone 4(S) and iPhone 5(S). Finally, the *@3x* images are used by the iPhone 6 and iPhone 6 Plus. In most cases you won't have to spend too much time thinking about this, as long as you provide assets in all relevant resolutions.

Applications that designers use such as _Sketch_ allow *exporting* all versions at the same time. And applications like _Xcode_ allow *importing* all versions at the same time.

Let's do that now!
> [action]
Unzip the downloaded art pack, and click the small `+` icon at the bottom of the list that has only `AppIcon` in it. Select `Import` from the pop-up menu. Select the unzipped art folder and bam!
>
Note: if you don't name the files this way, you have to manually import each version of each asset, and it takes up way more time.
>
![image](all_assets.png)

You should also note that we don't reference images in asset catalogs by their file name, but instead by the name of their Image Set. For this project, we only have "logo" but in the future we'll have more. Also, for this project we cheated because all three files are the same size. If you have an app with many assets, this will make your life more painful, and possibly make your app slower.


>[action]
>
>1. Open `Main.Storyboard`
>1. clear and type `image` in the the object browser filter box
>1. drag imageview to the view
>1. in the `attributes selector` change `image` to `logo`
>1. add the constraints [screenshot]
>1. run the app and rotate the simulator to see how things look.

With an on-screen keyboard, the landscape mode is going to look weird, so lets disable rotation.

>[action]
>1. In the `Project Navigator` select the `TipPro` project, which will be the first item listed. Its the root of everything.
>1. Under the tab `General` (which should already be selected) look under the `Deployment Info` section for the `Device Orientation` options.
[screenshot?]
>1. Deselect `Landscape Left` and `Landscape Right` so that `Portrait` is the only option left.
[screenshot afterwards?]
>1. run the app and rotate the simulator to see how things look.

## Splash of color

Now lets add some color to make this app stand out even more.

>[action]
>
>1. Open `Main.Storyboard`
>1. Select the `Tip Calculator` label.
>1. In the `Attributes Inspector` under `View` click on the `Background` attribute which is currently set looks like this: [screenshot]. This represents the default setting, which is fully transparent.
>1. A color selection window has popped up. Click on the _eye-dropper_ to select the color in the same way a real eye-dropper or turkey baster would suck up liquid. Its on the bottom of the `Colors` palette, and if you have never seen one before, it also looks like a knife.
>1. Once you click it, you will notice your cursor has turned into a virtual _loupe_. (The thing jewelers use to look at diamonds, or graphic designers use to look at detail. In this case, both are relevant, since the graphic design we care about, is a diamond.)
>1. Move the _loupe_ over the blue part of the _Make School_ logo and click to select that color.


Notice the background color for the label change? Perfect. Now lets change the text color to white, and make the label bigger for a more dramatic effect.

>[action]
>
>1. Close the colors selector. (It is blocking the next setting we want to click)
>1. Now, notice the `Color` setting, currently set to black. Click the right side of that control (the blue part with arrowheads or carets), and select `White Color` from the drop down menu.
>1. Under the `Size Inspector`, set the `Top Space`, `Leading Space` and `Trailing Space` to `0` using the `edit` button on each of the settings.
>1. Using the `Pin` icon, at the bottom of the storyboard editor, set the `Height` to `50`.
>1. Select the `Bill Amount` label, and under the `Size Inspector`, double-click on the `Top Space to Tip Calculator`.
>1. Update the `Second Item` to `Bottom`, and change the `Constant` to `10`
>1. Repeat the same with the `Bill Amount Field`.
>1. Select the `Tip Calculator` label.
>1. Under the `Size Inspector`, set the `Top Space`, `Leading Space` and `Trailing Space` to `-20` using the `edit` button on each of the settings.
>1. Open `ViewController.swift` and add the following code:
>
override func preferredStatusBarStyle() -> UIStatusBarStyle {
  return .LightContent
}





## Changes after running on device
Now that you have run it on your device, you may have noticed some UX/UI bugs, or areas that we could improve. Lets fix some, and feel free to come back in the future and fix more.


>[action]
> 1. Select the `Bill Amount Field` and using the `Attributes Inspector`, set the `Keyboard Type` to `Decimal Pad`
> 1. Select the `Tip Amount Field` and using the `Attributes Inspector`, disable this field by unchecking `Enabled` in the `Control` section.
> 1. Do the same for `Total Amount Field`
