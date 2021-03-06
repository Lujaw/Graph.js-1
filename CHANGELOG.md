# CHANGELOG

## v0.3 - Released [not yet]

 * Fixed: when the shadow was enabled, the line-filling also had a shadow making it darker than it should be.
 * Added: Issue #5: new option: `options['gridDotted']` to make the grid lines dotted.
 * Added: new option: `options['axisSize']` to specify the axis line size. (value 'auto' to use Grid setting)
 * Added: new option: `options['axisColor']` to specify the axis line color. (value 'auto' to use Grid setting)
 * Added: new option: `options['axisShadow']` to give the axis line a shadow. (value 'auto' to use Grid setting)
 * Added: new option: `options['gridYCount']` to define the number of vertical lines (default is 2)
 * Added: Issue #1: new option: `options['gridX']` to enable/disable the horizontal grid lines.
 * Added: Issue #1: new option: `options['gridY']` to enable/disable the vertical grid lines.
 * Fixed: `addLine` now accepts a third parameter, the fillColor. Useful for multiple data lines.
 * Fixed: `options['spacing']` now works as it should with the height instead of changing values.
 * Changed: the default style options have been changed a bit.
 * Changed: tabs in graph.js source to 8 spaces instead of 4, to see if Github formats it better then.
 * Fixed: Issue #6: if you have `options['lineCurve']` enabled, but less than 3 data points it now disables lineCurve.

## v0.2 - Released May 18th, 2011

 * Added: new sample files demonstrating some of the changes.
 * Fixed: Issue #4 - Improved support for multiple data lines and `getClosestBullet`.
 * Added: Issue #3 - Added border support (new options `options['border']` and `options['borderColor']`)
 * Added: Issue #2 - Support for meta-data per data point. (also the new option: `options['valueKey']`)
 * Added: new method `getOffset()` and option `options['useOffset']` to improve ease of use for `getClosestBullet`.

## v0.1 - Released May 17th, 2011

This was the initial release, so basic feature set.