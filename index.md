---
layout: default
---

# Creating Reusable Charts with D3

## What is a Chart?

A chart is a mapping between data attributes and visual attributes.

![Fruits](http://imgs.xkcd.com/comics/fuck_grapefruit.png)

## What is D3 (Data Driven Documents)

D3 allows us to bind data elements to DOM elements, and manipuate attributes of the element based on attributes of the data

<a class="jsbin-embed" href="http://jsbin.com/wefila/7/embed?html,js">

The function we used to calculate the width of the bars is a bit difficult to calculate (not really), we can use a [linear scale](https://github.com/mbostock/d3/wiki/Quantitative-Scales#linear-scales) to have this calculation made for us:

<a class="jsbin-embed" href="http://jsbin.com/gepuvi/3/embed?js,output">JS Bin</a>

## Enter, Update and Exit Selections

In the previous examples, we already have 4 div elements, and we also have exactly 4 data items to bind to the divs. What happens if we don’t have enough DOM elements, or if we have too many?

### Exit Selection

If there are more DOM elements that data items, the remaining DOM elements will be stored in the [exit selection](https://github.com/mbostock/d3/wiki/Selections#exit), and can be manipulated as regular selections

<a class="jsbin-embed" href="http://jsbin.com/wilaja/3/embed?html,js">JS Bin</a>

### Enter Selection

If there are less (or none) DOM elements than data items, the [enter selection](https://github.com/mbostock/d3/wiki/Selections#enter) will contain _placeholder_ DOM elements to create the mapping. In order to modify the attributes of the entering items, we need to create them first using [append](https://github.com/mbostock/d3/wiki/Selections#append)

<a class="jsbin-embed" href="http://jsbin.com/tosubi/2/embed?js,output">JS Bin</a>

### Simplifying

<a class="jsbin-embed" href="http://jsbin.com/canawi/1/embed?html,js">Simplifying</a>

### Creating a Charting Function

<a class="jsbin-embed" href="http://jsbin.com/qupeza/2/embed?html,js,output">Creating a Charting Function</a>

 It assumes that the class of the divs is 'bar'. We can modify the charting function to bind the data to the container selection and encapsulate the creation, update and removing of the divs. Also, we will use the 'call' syntax (idiomatic to D3)

<a class="jsbin-embed" href="http://jsbin.com/buyelo/1/embed?js,output">JS Bin</a>

It also assumes that the functions 'x', 'xScale' and 'label' are defined properly. We can create a better version using closures

#### Accessors

<a class="jsbin-embed" href="http://jsbin.com/rugufo/1/embed?html,js,output">Accessors</a>





## Links and Resources

- [Towards Reusable Charts](http://bost.ocks.org/mike/chart/)
- [How Selections Work](http://bost.ocks.org/mike/selection/)