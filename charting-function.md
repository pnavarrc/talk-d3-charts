---
layout: default
---

## Creating a Charting Function

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

Now that we understand the essentials, we will create a chart with real data [earthquake chart](/earthquake.html)