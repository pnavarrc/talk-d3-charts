---
layout: default
---

# Creating Reusable Charts with D3

Outline

- Charts
- Introduction to D3
  - Data binding
  - Enter, Update and Exit
- Creating a Charting Function
  - Simple function
  - Adding a closure
  - Adding accessors
  - Automatic accessor creation
- SVG Charts
  - Simple SVG
  - Earthquake chart
  - Components
  - Assembling a new chart
  - Map of Earthquakes


## What is a Chart?

A chart is a _mapping_ between data attributes and visual attributes of objects representing the data items. The data attributes are encoded using position, colour, size or shape of the visual elements.


In the following chart, the tastiness and easiness of eating different fruits is encoded using the position in two axes.

![Fruits](http://imgs.xkcd.com/comics/fuck_grapefruit.png)


[xkcd: Tastiness of Fruits](https://xkcd.com/388/)

Bar charts, for instance, use rectangles to represent the data items, encoding one quantitative dimension in the length of one of the sides of the rectangle

IMAGE HERE

In most charting software and utils, we are given a set of charts (bar chart, scatter plot) and we need to provide the data to create the items. With D3, we create charts by manipulating the mapping between data attributes and attributes (and styles) of DOM elements.

## Introduction to D3 (Data Driven Documents)

[D3.js](http://www.d3js.org) is a JavaScript library to bind data elements to documents (DOM elements) and manipulate attributes of the documents based in the data bound to it.

IMAGE HERE

Binding data items to DOM elements allows us to manipulate their attributes, in this case, the div width and content. The color, margin and borders are set using CSS:

<a class="jsbin-embed" href="http://jsbin.com/wefila/latest/embed?html,js&height=600px">Data Binding</a>

D3 also includes a number of utility functions to help us creating charts. Here we will use a [linear scale](https://github.com/mbostock/d3/wiki/Quantitative-Scales#linear-scales) to compute the mapping between the tastiness of the fruit to pixels in the screen.

<a class="jsbin-embed" href="http://jsbin.com/gepuvi/latest/embed?html,js&height=600px">JS Bin</a>

## The Selection Lifecycle: Enter, Update and Exit

In the previous examples, we already had 4 div elements, and we also had exactly 4 elements in the array to bind to the divs. What happens if we don’t have enough DOM elements, or if we have too many?

D3 creates special selections, that allow us to create, remove and update the elements in each case. We need to specify what will happen in every step of the element’s life cycle.

### Exit Selection (Removing)

If there are more DOM elements that data items, the remaining DOM elements will be stored in the [exit selection](https://github.com/mbostock/d3/wiki/Selections#exit). These elements can be manipulated in the same way that regular selections, except that they don’t have bound data items.

<a class="jsbin-embed" href="http://jsbin.com/wilaja/latest/embed?html,js&height=700px">JS Bin</a>

### Enter Selection

If there are less (or none) DOM elements than data items, the [enter selection](https://github.com/mbostock/d3/wiki/Selections#enter) will contain _placeholder_ DOM elements to create the mapping. Before manipulating the element attributes, we need to create the _actual_ DOM elements first by using the [append](https://github.com/mbostock/d3/wiki/Selections#append) method

<a class="jsbin-embed" href="http://jsbin.com/tosubi/latest/embed?js,output&height=700px">JS Bin</a>

Before starting to create a more generic bar chart, we will simplify our code a bit

<a class="jsbin-embed" href="http://jsbin.com/canawi/latest/embed?html,js&height=900px">Simplifying</a>

### Creating a Charting Function

<a class="jsbin-embed" href="http://jsbin.com/qupeza/latest/embed?js,output&height=900px">Creating a Charting Function</a>

This version of the charting function assumes that the container has a single element, but it might not always be the case. We are also moving the scale to the body of the charting function, so each chart has their own relative scale

<a class="jsbin-embed" href="http://jsbin.com/buyelo/latest/embed?html,output&height=900px">JS Bin</a>

Another problem of this implementation is that our charting function assumes that we have defined the functions `x`, `label` and the width of the chart. We can use closures and accessor methods to encapsulate the chart related parameters

<a class="jsbin-embed" href="http://jsbin.com/rugufo/latest/embed?html,js&height=1200px">Accessors</a>

Excelent! We can still improve a bit by creating a function to attach the accessor methods automatically.

<a class="jsbin-embed" href="http://jsbin.com/lixuwi/1/embed?js,output">JS Bin</a>

## Scalable Vector Graphics (SVG)

SVG is a vectorial image format. Modern browsers can reder SVG natively. SVG can be created and injected in the DOM, can be styled with CSS, animated and also manipulated with D3

<a class="jsbin-embed" href="http://jsbin.com/rigawi/latest/embed?html">JS Bin</a>

## Earthquake Chart

Now that we understand the essentials, we will create a chart with real data [earthquake chart](/earthquake.html)



## Links and Resources

- [Towards Reusable Charts](http://bost.ocks.org/mike/chart/)
- [How Selections Work](http://bost.ocks.org/mike/selection/)