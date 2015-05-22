---
layout: default
---

# Earthquake Chart

We have tabular data for earthquake dates, locations and magnitude

<pre class="csv">
Date,       Time,        Lat,       Lon,       Depth,  Mag
1980/02/23, 05:51:03.20,  43.5300,  146.7530,  44.00,  7.00
1980/07/08, 23:19:19.80, -12.4100,  166.3810,  33.00,  7.50
1980/07/17, 19:42:23.20, -12.5250,  165.9160,  33.00,  7.90
1980/10/10, 12:25:23.50,  36.1950,    1.3540,  10.00,  7.30
1980/10/25, 11:00:05.10, -21.8900,  169.8530,  33.00,  7.20
</pre>

## Geographic Points Chart

Using the principles from the previous section, we can create a very nice chart, displaying the location of the earthquakes and their magnitude.

<a class="jsbin-embed" href="http://jsbin.com/lebawe/latest/embed?js&height=2000px">JS Bin</a>

<a class="jsbin-embed" href="http://jsbin.com/lebawe/latest/embed?output&height=530px">JS Bin</a>

This works perfectly, but it could be more modular. We can create smaller components and compose them to reduce the complexity and overall size of the charts.

## Composing the Charts

We will separate the components of our chart in smaller units. We will create a chart for the SVG element, a chart for container groups and a chart to create dots.

<a class="jsbin-embed" href="http://jsbin.com/jodoja/latest/embed?js&height=2000px">JS Bin</a>

