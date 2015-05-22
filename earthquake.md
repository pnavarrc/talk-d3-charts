---
layout: default
---

# Earthquake Chart

We have a CSV file with earthquake data since 1980, courtesy of the [ANSS Catalog](http://quake.geo.berkeley.edu/anss/catalog-search.html). We have about 400 registered earthquakes of magnitude 7.0 or more since then. We have the earthquake date, time, latitude, longitude, depth and Richter magnitude.

<pre class="csv">
Date,       Time,        Lat,       Lon,       Depth,  Mag
1980/02/23, 05:51:03.20,  43.5300,  146.7530,  44.00,  7.00
1980/07/08, 23:19:19.80, -12.4100,  166.3810,  33.00,  7.50
1980/07/17, 19:42:23.20, -12.5250,  165.9160,  33.00,  7.90
1980/10/10, 12:25:23.50,  36.1950,    1.3540,  10.00,  7.30
1980/10/25, 11:00:05.10, -21.8900,  169.8530,  33.00,  7.20
</pre>

We will create a scatter plot to display the earthquakes, using the latitude and longitude to determine the position of the dots, and the magnitude to set the radius of the points.

## Geographic Points Chart

We already know how to create a chart, so we will dive into it right away. We will start by creating the closure function, setting the chart attributes and generating the accesor methods. In the charting function, we will create and SVG element, set its width and height, create a container group and translate it to have margins, configure the scales and finally, create a selection of circles, bind them to our data, set their position and size.

This time, we will retrieve the data from the internet, and use the [d3.csv](https://github.com/mbostock/d3/wiki/CSV) method to get the data asynchronously. D3 will do its best to parse the data and transform it into a JavaScript array of objects, but CSV doesn’t support data types, so we will need to cast the type of each element by hand.

When our data is ready, we can select the container, bind the data and invoke our chart.

<a class="jsbin-embed" href="http://jsbin.com/lebawe/latest/embed?js&height=2000px">JS Bin</a>

And the resulting visualisation:

<a class="jsbin-embed" href="http://jsbin.com/lebawe/latest/embed?output&height=530px">JS Bin</a>

This is nice, but it could be more modular. The SVG creation and setup will be needed in any SVG based chart we might want to do, creating and translating groups is another very common task. It would be ideal to have a configurable chart to take care of the SVG creation, update and removal, so we can use it in other charts as well.

Instead of writing the code to create every element of our chart in one charting function, we will create smaller charts that will manage each part separately, allowing us to reuse these components in the future.

## Composing the Charts

We will separate the components in our chart in smaller units. We will create a chart to draw the SVG element, another chart to create and translate SVG groups and also a scatter plot chart, which will just draw a set of points. The scatter chart will not need to care about SVG dimensions, just to get data items and how to draw them in a parent container.

We will use these three charts to create a more complex chart (our earthquake chart) in a more modular way, keeping the chart API unchanged.

<a class="jsbin-embed" href="http://jsbin.com/jodoja/latest/embed?js&height=2000px">JS Bin</a>

We will also add a delay when updating the radius of the circles, creating a timelapse

<a class="jsbin-embed" href="http://jsbin.com/jodoja/latest/embed?output&height=540px">JS Bin</a>

[Thanks!](thanks.html)
