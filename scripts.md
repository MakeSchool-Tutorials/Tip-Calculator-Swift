[script]: bill_amount.mp4
1. type label in the the object browser filter box
1. drag label to the view
1. change label text to `Bill Amount:`
1. Right-click and drag from label to view. select `center horizontally`
1. choose the `size inspector`
1. change the `align center x to` to `-50` (make sure to hit `-` twice)
1. Right-click and drag from the label to the `Tip Calculator` label and select `Top`
1. change the `Align Top To: Tip Calculator` to `50`
1. click on the label again and `update frame`
1. clear and type field in the the object browser filter box
1. drag textfield to the view
1. Right-click and drag from label to view. select `center horizontally`
1. change the `align center x to` to `-50` (make sure to hit `-` twice)
1. Right-click and drag from the label to the `Tip Calculator` label and select `Top`
1. change the `Align Top To: Tip Calculator` to `50`
1. Right-click and drag from the label to the `Bill Amount` label and select `Equal Heights`
1. click the `Pin` button and set the `Width` to 75
1. click on the label again and `update frame`

[script]: ---------video---------- tip_percent.mp4
1. Option-click and drag the `Bill Amount:` label down a little bit.
1. double-click the new `Bill Amount:` label and change text to `Tip %:` and then hit enter
1. clear object browser filter and type in `segment`
1. drag segmented control
1. select `Attributes Inspector`
1. Increase number of segments to `3`
1. Double click `First` and change to `15%`
1. Double click `Second` and change to `18%`
1. Double click ` ` (the empty third one) and change to `20%`


[script]: video delete_edit_constraints.mp4
1. use shift to select all the `Tip %:` and `15% 18%` constraints. and then hit delete to delete them.
1. Right-click and drag from `Tip %:` to `Bill Amount:`. select `Leading`.
1. Right-click and drag from the `Segmented Control` to the `Text Field` select `Trailing`.
1. update frames

[script]: video spacing.mp4
1. Right-click and drag from `Tip %:` to the `Bill Amount` label and select `Top`
1. change the `Align Top To: Bill Amount` to `50`
1. click on the label again and `update frame`
1. Right-click and drag from from the `Segmented Control` to the `Text Field` and select `Top`
1. change the `Align Top To: Round Style...` to `50`
1. click on the label again and `update frame`

[script]: video center_vertically.mp4
1. control click and drag from the tip selector to the `tip %` label and choose center vertically.
1. update frames.



[script]: ------video------- final_controls.mp4
(had to modify to use the pin menu)
1. Option-click and drag the `Tip %:` label down a little bit.
1. double-click the new `Tip %:` label and change text to `Tip Amount:` and then hit enter
1. Option-click and drag the `Tip Amount:` label down a little bit.
1. double-click the new `Tip Amount:` label and change text to `Total Amount:` and then hit enter
1. Right-click and drag from `Tip Amount:` to the `Tip %` label and select `Top`
1. Right-click and drag from `Tip Amount:` to the `Tip %` label and select `Leading`
1. change the `Align Top To: Tip %` to `50`
1. Right-click and drag from `Total Amount:` to the `Tip Amount` label and select `Top`
1. Right-click and drag from `Total Amount:` to the `Tip Amount` label and select `Leading`
1. change the `Align Top To: Tip Amount` to `50`
1. Option-click and drag the text field next to the `Bill Amount` label down to line up with the `Tip Amount Label`.
1. Right-click and drag from the new text field to the view. select `center horizontally`
1. change the `align center x to` to `50`
1. Right-click and drag from the new text field to the `Tip Amount` label and select `Equal Heights`
1. Option-click and drag the new text field next to the `Tip Amount` label down to line up with the `Total Amount Label`.
1. Right-click and drag from the new text field to the view. select `center horizontally`
1. change the `align center x to` to `50`
1. Right-click and drag from the new text field to the `Total Amount` label and select `Equal Heights`

[script]: wiring_it_up.mp4
1. control click drag from `bill amount` label to under the `class ViewController` line and call the field `billAmountField`
1. control click drag from the `% selector` and call the field `tipSelector`
1. control click drag from the `tip amount` label and call the field `tipAmountField`
1. control click drag from the `total amount` label and call the field `totalAmountField`
1. control click drag from `bill amount` label to and choose `Action` and `Value Changed` and call it `billAmountChanged`
1. control click drag from `tip selector` label to and choose `Action` and `Value Changed` and call it `tipChanged`
1. add some space between the functions
