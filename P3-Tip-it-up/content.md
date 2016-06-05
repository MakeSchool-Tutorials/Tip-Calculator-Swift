
Segment 3: (ironically named after making 3 segments)



wiring it up:
1. click on the linked rings above the `Preview` in the `Assistant Editor` and change it to `Automatic`. It should now show `ViewController.swift` in the `Assistant Editor`. You can verify this by finding our `print("Hello World")` line.
1. Drag the divider between the `editors` to make more space
1. Close the `Debugger Area` (icon screenshot) or command-shift-y

[script]: steps for wiring it up:
1. control click drag from `bill amount` label to under the `class ViewController` line and call the field `billAmountField`
1. control click drag from the `% selector` and call the field `tipSelector`
1. control click drag from the `tip amount` label and call the field `tipAmountField`
1. control click drag from the `total amount` label and call the field `totalAmountField`
1. control click drag from `bill amount` label to and choose `Action` and `Value Changed` and call it `billAmountChanged`
1. control click drag from `tip selector` label to and choose `Action` and `Value Changed` and call it `tipChanged`
1. add some space between the functions

[action]
code for calculation
>@IBAction func billAmountChanged(sender: AnyObject) {
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
1. Run the project
1. Type in a bill amount
1. Click `18%`
1. It crashed!!!!

Why did it crash? Very simple, your `Main.storyboard` has the `Tip % Selector` wired up to two functions, and when it called one of them, it crashed. `reason: -[TipPro.ViewController tipChanged:]: unrecognized selector sent` This is objective-c syntax for `message passing` which in Swift, would be the equivalent of calling a function. Think of it as `ViewController.tipChanged(something)`. It crashed because that doesn't exist. So lets unlink it, and try again.

1. Open `Main.storyboard`
1. Right(control)-click on the `Tip % Selector`
1. In the pop-up window [screenshot] click the `X` next to `Value Changed` that says `ViewController tipChanged`. Close the pop-up.
1. Since we already have the function defined that we want to connect to, right(control)-click and drag from the `Tip % Selector` to the `View Controller` in the _hierarchy_ of your storyboard under `View Controller Scene`.
1. Select `billAmountChanged`
1. Run
1. Type in a bill amount
1. Click `18%`
1. Success!!!


Now, lets change `billAmountChanged` to `updateTip`. For this, try it on your own first. It is ok, if you wound up doing something different then these instructions, as long as it works.

1. Open `ViewController.swift`
1. Rename `billAmountChanged` to `updateTip`
1. Open `Main.storyboard`
1. Right(control)-click on the `Bill Amount `
1. In the pop-up window click the `X` next to `Editing did end` that says `ViewController billAmountChanged` and click the `X` next to `Editing Changed` that says `ViewController billAmountChanged`.
1. Drag from the circle next to `Editing Changed`  to the `View Controller` in the _hierarchy_. Let go and select `updateTip`
1. Drag from the circle next to `Editing did End`  to the `View Controller` in the _hierarchy_. Let go and select `updateTip`
1. Close the pop-up.
1. Right(control)-click on the `Tip % Selector`
1. In the pop-up window click the `X` next to `Value Changed` that says `ViewController billAmountChanged`.
1. Drag from the circle next to `Value Changed` to the `View Controller` in the _hierarchy_. Let go and select `updateTip`
1. Close the pop-up.


## Update the styles

1. {steps to add the images to xcode}
1. Open `Main.Storyboard`
1. clear and type `image` in the the object browser filter box
1. drag imageview to the view
1. in the `attributes selector` change `image` to `logo`
1. add the constraints [screenshot]
1. run the app and rotate the simulator to see how things look.

With an on-screen keyboard, the landscape mode is going to look weird, so lets disable rotation.

1. In the `Project Navigator` select the `TipPro` project, which will be the first item listed. Its the root of everything.
1. Under the tab `General` (which should already be selected) look under the `Deployment Info` section for the `Device Orientation` options.
[screenshot?]
1. Deselect `Landscape Left` and `Landscape Right` so that `Portrait` is the only option left.
[screenshot afterwards?]
1. run the app and rotate the simulator to see how things look.

## Splash of color
1. Open `Main.Storyboard`
1. Select the `Tip Calculator` label.
1. In the `Attributes Inspector` under `View` click on the `Background` attribute which is currently set looks like this: [screenshot]. This represents the default setting, which is fully transparent.
1. A color selection window has popped up. Click on the _eye-dropper_ to select the color in the same way a real eye-dropper or turkey baster would suck up liquid. Its on the bottom of the `Colors` palette, and if you have never seen one before, it also looks like a knife.
1. Once you click it, you will notice your cursor has turned into a virtual _loupe_. (The thing jewelers use to look at diamonds, or graphic designers use to look at detail. In this case, both are relevant, since the graphic design we care about, is a diamond.)
1. Move the _loupe_ over the blue part of the _Make School_ logo and click to select that color.

Notice the background color for the label change? Perfect. Now lets change the text color to white, and make the label bigger for a more dramatic effect.

1. Close the colors selector. (It is blocking the next setting we want to click)
1. Now, notice the `Color` setting, currently set to black. Click the right side of that control (the blue part with arrowheads or carets), and select `White Color` from the drop down menu.
1. Under the `Size Inspector`, set the `Top Space`, `Leading Space` and `Trailing Space` to `0` using the `edit` button on each of the settings.
1. Using the `Pin` icon, at the bottom of the storyboard editor, set the `Height` to `50`.

1. Select the `Bill Amount` label, and under the `Size Inspector`, double-click on the `Top Space to Tip Calculator`.
1. Update the `Second Item` to `Bottom`, and change the `Constant` to `10`
1. Repeat the same with the `Bill Amount Field`.

1. Select the `Tip Calculator` label.
1. Under the `Size Inspector`, set the `Top Space`, `Leading Space` and `Trailing Space` to `-20` using the `edit` button on each of the settings.
1. Open `ViewController.swift` and add the following code:
>
override func preferredStatusBarStyle() -> UIStatusBarStyle {
  return .LightContent
}





## Changes after running on device
* after running on device, change the software keyboard:
> 1. Select the `Bill Amount Field` and using the `Attributes Inspector`, set the `Keyboard Type` to `Decimal Pad`
* make other fields read-only
> 1. Select the `Tip Amount Field` and using the `Attributes Inspector`, disable this field by unchecking `Enabled` in the `Control` section.
> 1. Do the same for `Total Amount Field`
>
