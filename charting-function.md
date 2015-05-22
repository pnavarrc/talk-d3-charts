---
layout: default
---

## Creating a Charting Function

The sequence of creating a selection, binding the data, creating elements on enter, updating and removing the items on exit can be put in a function to make our code more modular. We can then invoke our charting function passing the container selection to it, making easier to update the data.

<a class="jsbin-embed" href="http://jsbin.com/qupeza/1/embed?js,output&height=900px">Creating a Charting Function</a>

There is some room for improvement here. Our charting function is assuming that the container selection contains a single DOM element, but it might not always be the case. As selections are basically arrays of DOM elements, we will use [each](https://github.com/mbostock/d3/wiki/Selections#each) to iterate through the elements in the selection.

When using `each`, the context of the iteratee function will be the DOM element, and the first argument of the iteratee will be the data item bound to that DOM element.

<a class="jsbin-embed" href="http://jsbin.com/buyelo/latest/embed?html,output&height=900px">JS Bin</a>

Note that we also moved the scale to the iteratee function, so each selection has its own relative scale. Another problem of this implementation is that our charting function assumes that we have defined the functions `x`, `label` and the width of the chart.

We will use [closures](http://jibbering.com/faq/notes/closures/) to encapsulate the charting parameters, in order to avoid polluting the global context. The charting parameters can’t be changed from outside the charting function, we will attach accessor methods in order to change their values.

Returning the chart function when setting the values of each charting parameter will allow to chain our methods, so we can configure several parameters in one statement.

Being able to configure the chart allows us to add interactivity to our chart, in this case, by changing the variable we are using to determine the width of the bars. We can create some buttons to change this function and redraw the chart (with fancy transitions!).

<a class="jsbin-embed" href="http://jsbin.com/rugufo/latest/embed?html,js&height=1200px">Accessors</a>

This structure works for any kind of chart we might want to create, and not only for charts, the same structure can be used to create custom [layouts](https://github.com/mbostock/d3/wiki/Layouts), among other things.

<a class="jsbin-embed" href="http://jsbin.com/lixuwi/1/embed?js,output">JS Bin</a>

Creating charts with DIV elements is limited, the real fun begins when we use SVG to create more complex graphics and visualisations.

## Scalable Vector Graphics (SVG)

[SVG](https://developer.mozilla.org/en/docs/Web/SVG) is a vectorial image format, which means we can zoom in and the graphic will not be pixelated. SVG is a image format that describes the image in terms of geometric shapes, circles, rectangles, paths, symbols and glyphs. The structure of a SVG image looks like HTML, but with a different set of elements and attributes.

As D3 is not aware of HTML tags or attribtues (it only manipulates the DOM), we can create SVG images with D3 in exactly the same way than we create and manipulate HTML elements. If the SVG element is part of the document, it can be styled with CSS and manipulated with JavaScript.

<a class="jsbin-embed" href="http://jsbin.com/rigawi/latest/embed?html">JS Bin</a>

Now that we understand the essentials, we will create a chart with real [earthquake](earthquake.html) data.