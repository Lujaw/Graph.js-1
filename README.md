# Graph.js

## Purpose

A lightweight JavaScript class for drawing line graphs in a canvas element, that doesn't do any DOM manipulations.

## Features
  
 * Easily configurable / theme support
 * Multiple data lines in different colors
 * Additional methods to add functionality (e.g. mouseover bubble, html labels)
 * Included a minified version for quick download

## To Do

 * Add horizontal grid lines (with `y` label support in `getGridAxes()`)
 * Add support for complex data points ( {'value': 123, 'custom-thing': 123} )

## Idea behind Graph.js

For a project I was working on I needed to add a simple line graph, and while there are plenty of good options out there, most of them were to bloated for my needed, or depended on some library I wasn't using — besides I love creating my own components, getting my hands dirty. I've created this simplified lightweight version as a result, it doesn't do any DOM manipulation so if you want labels — you'll need to add them yourselves. To help you do this, I have included a couple methods, demonstrated in the (poorly written) vanilla JavaScript examples.

There is also no detection for canvas support, so old fashioned browsers will not work by default and there is no alternative. You might be able to get them to work, at least for IE, with the `excanvas` project. But I have not tried this myself.

## Example

Example from example/basic.js:

	<script type="text/javascript" src="graph.min.js"></script>
	<script type="text/javascript">
		var canvas	= document.getElementById( "canvas_object" );
		var graph	= new Graph( canvas, [10,20,50,20,30,60,10], true );
	</script>
	
	<canvas id="canvas_object" width="800" height="400">
		Your browser does not support the HTML Canvas object, so... no graph for you!
	</canvas>

## Documentation

### new Graph( canvas[, dataPoints, draw] );

Create a new Graph instance for said canvas, with the optional parameters you can make it immediately draw the graph with the given data — instead of calling the draw method later.

Parameters:

* `canvas`: Requires a pure DOM Canvas element.
* `dataPoints`: An array filled with numbers.
* `draw`: A boolean to start drawing the graph or not, default is false.

#### addLine( dataPoints[, color] )

Add a new line with the given dataPoints, and optionally you can give it a new color.

Parameters:

* `dataPoints`: An array filled with numbers.
* `color`: A textual representation of a color (e.g. `red`, `#ff0000`, `rgb(255,0,0)`), defaults to the 'default' color.

#### options['name']	= value;

The options are available in a simple array form on the graph, you can overwrite them easily. A quick sample, can also be found in the examples directory (sample2_options.html) but it is advised to just play around with them so you can see what they actually do.

	var graph		= new Graph( canvas );
	graph.options['minValue']		= "auto";
	// Will automatically get the lowest number from your data array.
	
	graph.options['maxValue']		= "auto";
	// Will automatically get the highest number from your data array.
	
	graph.options['padding']		= 50;
	// The padding from the canvas border to where the grid/graph begins.
	
	graph.options['spacing']		= 20; 
	// The spacing for top/bottom, only used if minValue/maxValue is auto and could be 0. 
	// It helps prevent lines from being EXACTLY ON the top/bottom line of graph but adds some spacing.
	
	graph.options['background']		= ["#fff","#eee","#ddd"];
	// Background, either string ('#fff', or 'red') or array with strings representing colors for a gradient.
	
	graph.options['grid']			= true;
	// Enable the background lines/grid. Only Vertical and bottom line support for now.
	
	graph.options['gridSize']		= 0.2;
	// The size of the background lines/grid. Can be half as well (0.5)
	
	graph.options['gridColor']		= "rgba(0, 0, 0, 0.3 )";
	// The color for the background lines/grid.
	
	graph.options['gridShadow']		= false;
	// Give the grid a small shadow as well for depth effect.
	
	graph.options['bullets']		= true;
	// Show bullets for the data points from your data array.
	
	graph.options['bulletSize']		= 5;
	// The radius of the bullet points.
	
	graph.options['bulletColor']	= "#000";
	// The inside color of the bullet, only visible if you have 'bulletFill' enabled.
	
	graph.options['bulletFill']		= true;
	// Enable or disable the inside color for the bullet.
	
	graph.options['bulletShadow']	= true;
	// Give the bullet a shadow, or don't! Your choice. 
	
	graph.options['shadowColor']	= "rgba(0, 0, 0, 0.6)";
	// The color for all shadows (grid/bullet/etc)
	
	graph.options['fill']			= true;
	// Do you want to fill the data from line to bottom (nice effect if you use an alpha color)
	
	graph.options['fillColor']		= "rgba(255,0,87,0.2)";
	// The color, only visible if you enable 'fill'.
	
	graph.options['lineSize']		= 3;
	// The size of the line.
	
	graph.options['lineCurve']		= true;
	// Do you want the line to curve, or not?
	
	graph.options['lineColor']		= "#ff0059";
	// Which color is the line (and bullets/bullet outside)

#### draw()

Draw the graph for the first time, useful if you didn't specify that the graph immediately draws in the constructor.

#### redraw()

Redraw the graph, a very useful method if you add/update/deleted data. 

#### getClosestBullet( mouseX[, magnify] )

Determine what the closest bullet point is near the `mouseX` position, you have to manually calculate this (relative) position though. An example can be found in the examples directory, sample4_mouseover.html — optionally you can have this method magnify the closest bullet so you can visually represent where the user is.

Parameters:

* `mouseX`: The X coordinate where your mouse is, or finger, or whichever X you wish.
* `magnify`: A boolean to determine if you want to highlight the closest bullet, defaults to false;

#### getGridAxes()

Returns an object, containing positions for both the `x` and `y` gridlines. The current version does not (yet) contain `y` gridlines so it will be an empty array, the `x` will be an array filled with objects containing the `x`,`y` position where you can put your label. A sample can be found in the examples directory, sample5_labels.html

## Minified with YUI! Compressor

This is the simple way this version has been minified, in case you were wondering. Also a note for myself so I can make it consistent throughout versions.

	java -jar yuicompressor-2.4.2.jar graph.js --line-break 300 --preserve-semi --output graph.min.js