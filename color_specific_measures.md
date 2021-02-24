# Hint/Trick: Coloring only specific measures in a worksheet in Tableau

This is another relatively simple topic, but hopefully some will find it useful.

## Scenario

You have a visualization where you want multiple values in a cell, but you want only to color some of the elements based on their value. The technique will also work to color items in Tooltips based on their value.

## Solution

To change the values, you have to create calculations to represent each of the color groupings. For example, one calculation for negative values, and one for values that are 0 and above.

Image for calculation

Image for calculation


Once you have the calculations, you can include them in

Image for text Dialog

That results in:

Image of final views

## Discussion

Since the values are mutually exclusive, only 1 will show. Essentially, you end up constructing the same display that you have with measure names/measure values. You just won't have the zebra striping of the rows.

Many more sophisticated implementations can be created using the technique. This is just a simple implementation.
