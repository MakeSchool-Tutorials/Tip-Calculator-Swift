---
title: "Tip it up!"
slug: adding-the-logic
---

## Linking your interface to code

_Xcode_ makes it easy to connect your interface to code. Now that we've got an interace

>[info]
>
There are two main kinds of code connections: _outlets_, and _actions_. _Outlets_ let you assign a variable in code to a component of your interface you have created in your storyboard to interact with that component in code. We will use that to read and set values from our interface. _Actions_ let our code know when the user did certain things to an interface component that we want to react to.

<!--  -->

>[action]
> ## Adding code connections
>
1. Close the layout tree and attribute inspector to make some room.
1. Open the assistant editor and make sure `ViewController.swift` is displayed.
1. Control-click (or right-click) drag from `bill amount text field` to under the `class ViewController` line and name the outlet `billAmountField`.
1. Control-click (or right-click) drag from the `tip selector text field` and name the outlet `tipSelector`.
1. Control-click (or right-click) drag from the `tip amount text field` and name the outlet `tipAmountField`.
1. Control-click (or right-click) drag from the `total amount text field` and name the outlet `totalAmountField`.
1. Control-click (or right-click) drag from the `calculate` button to the view controller. Choose `Action` and name it `calculateTip`.
1. Add some space to clean up the file.
>
> ![ms-video](https://s3.amazonaws.com/mgwu-misc/TipCalculator/17_outlets_and_actions.mp4)

# Adding the logic

> [info]
>
> Before we get started with the logic, we need to go over a new Swift concept! Let's talk about `guard` statements...
>
> `guard` is a special conditional statement that must `return` or throw an error if the condition is not met. In the code below, we are saying "if we cannot cast `billAmountField.text` to a `Double` and save it to `billAmount`, then we should stop what we are doing and clear the fields". If the condition _is_ met, then the function can continue. `guard` is different from `if` because it adds anything it unwraps to it's parent scope -- the scope it was called from!

Now that we have some _outlets_ and _actions_, we can actually code our logic. Since this tutorial is about _Xcode_, not programming, we are going to give you the logic. Study the code below and make sure you understand the logic!

> [action]
> Overwrite the two new functions you created with the code below. You should type it out and make sure you understand the logic!
>
```
@IBAction func calculateTip(sender: AnyObject) {
    guard let billAmount = Double(billAmountField.text!) else {
        //show error
        billAmountField.text = ""
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
    let roundedBillAmount = round(100*billAmount)/100
    let tipAmount = roundedBillAmount * tipPercentage
    let roundedTipAmount = round(100*tipAmount)/100
    let totalAmount = roundedBillAmount + roundedTipAmount
>
    if (!billAmountField.editing) {
        billAmountField.text = String(format: "%.2f", roundedBillAmount)
    }
    tipAmountField.text = String(format: "%.2f", roundedTipAmount)
    totalAmountField.text = String(format: "%.2f", totalAmount)
}
```
>
Run it and give it a spin! Do you understand the code? Hover over the _Solution_ below to see an explanation!

<!--  -->

> [solution]
> The `calculateTip` function starts off with a `guard` statement. If `billAmount` does not contain a number, it resets all the fields and returns immediately.
>
> If it does have a number, the function continues. It uses a `switch` statement to read the segmented control and set `tipPercentage`. It then calculates the `tipAmount` and `totalAmount`. Finally, it updates the respective text fields.

# Testing it out

Now that we have an interface, code connections, and logic... let's test it all out! Run the simulator and try calculating a tip :)

![ms-video](https://s3.amazonaws.com/mgwu-misc/TipCalculator/18_testing_the_code.mp4)

Looking good! Everything seems to work. On the next page, we'll make some small UI improvements before moving on to a more substantial app!
