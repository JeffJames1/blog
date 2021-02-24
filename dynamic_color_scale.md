# Hint/Trick: Creating a dynamic color scale in Tableau

This is a relatively simple topic, but hopefully some will find it useful.


## Scenario

You have a visualization where you are coloring items based on a measure. Everything is pretty easy if the scale is consistent across dimension values, but what if you need the scale to vary based on dimension values?


### Potential use cases:

* Lab tests with different turnaround times
* Operating rooms with different clearance times
* Quality measures that have different targets per payer/plan
* ...


## Solution

At the basic level, you will need to normalize all of the values to a single range. Then, base your color scale on the normalized range rather than the specific values.

Normalization is done using a formula that is pretty simple:

`([variable] - min)/(max - min)`

* variable: the measure you are normalizing
* min: the minimum value for the color scale
* max: the maximum value for the color scale

The end result will be a scale that runs from 0 to 1.

As an example, we might need to set different ranges for different facilities. Facility 1 has a range of 0-6, Facility 2 has a range of 24-48, and all others have a range of 12-36. To implement, a case statement is used:

```
case [Facility]
when 'Facility 1' then ([Target Range] - 0)/(6-0)
when 'Facility 2' then ([Target Range]- 24)/(48-24)
else ([Target Range]-12)/(36-12)
end
```

*Variables:*

* [Facility]: the dimension that will be on rows/columns
* [Target Range]: the measure the will be colored

One downside of this approach is implementation of a color legend. You can't use the default legend because it will show 0 and 1. If your view shows multiple dimension values at once, you probably can't have a legend or it will need to have "min" and "max" instead of numbers. If your view shows a single dimension at a time, you can create a custom legend using worksheets.

### Enhancement possibility

The described implementation has hard-coded ranges. If those ranges change frequently, or are used in multiple workbooks, it will be easier to maintain if the values are more dynamic. To make that change, the values can be brought in through a separate data source and blended in the views. That's right, blended. This is one of the time where blending will work without issues as long as the data source with the range values is secondary.

Alternatively, the range values can be added to the data set(s) being used when they are created.

## Example

Working with demo data that can be found in every tenant, so you can work along and replicate the process.

Create a view using Plan Type and Plan Name on rows, and Quarter of Server From Date and Out of Network Percentage on columns

Create a calculation that sets the target for Commercial at or below 36% and for Medicare at or below 40%.

Place the calculation on the color button on the Marks card and choose the appropriate settings

The result will show in the view

As you can see, the default legend is not really useful, so probably want to hide it.

Hopefully, that process will give you some ideas on how to handle varying colors.
