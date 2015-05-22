---
layout: default
---

# Creating Maps

We need a file with the geometric description of the shape we want to draw.

links

## JSON Format

<pre class="csv">
{
  "type": "Feature",
  "properties": {
    "scalerank": 3,
    ...
    "name": "Aruba",
    ...
  },
  "geometry": {
    "type": "Polygon",
    "coordinates": [
        [
          [-69.899121, 12.452001],
          [-69.895703, 12.422998],
          [-69.942187, 12.438525],
          [-70.004150, 12.500488],
          [-70.066113, 12.546972],
          [-70.050878, 12.597070],
          [-70.035107, 12.614111],
          [-69.973144, 12.567626],
          [-69.911816, 12.480468],
          [-69.899121, 12.452001]
        ]
      ]
    }
  }
}
</pre>

D3 includes a powerful package of geographic-related utilities, the two more important being [projections]() and [path generators]()

## Projections

## SVG Paths

## Path Generators

## Creating a Map

