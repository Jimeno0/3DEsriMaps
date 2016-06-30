# Examples using Esri Cedar Graphics and the new JS-API 4.0

## About this example

There are two examples of 3D maps where we can see the USA population represented by struded symbols. By clicking on any graphic bar/pie we can go to the selected state:

* [Using horizontal bars graphics](http://jimeno0.github.io/3DEsriMaps/3DmapCedarBars.html)
* [Using pie chart graphics](http://jimeno0.github.io/3DEsriMaps/3DmapCedarPie.html).

## How cedar works

### First we define the chart:

* Params:

Url service, what field to display on each axe and what field to renderize at the popups
```js
var usaStatesUrl = 'http://sampleserver6.arcgisonline.com/arcgis/rest/services/Census/MapServer/3';

var xField = "STATE_NAME",
  yField = "POP2000",
  toolTipTitle1 = "{POP2000}",
  toolTipTitle2 = "{STATE_NAME}";
```

* Chart:
Then we create a new Cedar chart

```js
var chart = new Cedar({
  "type": "pie",
  "dataset": {
    "url":usaStatesUrl,
    "mappings":{
    "label": {"field":xField,"label":"States"},
    "y": {"field":yField,"label":"Population"},
     "sort": yField,
    "radius": 270
    }
  }
});
```
* Tooltip:

Set the tooltip (popup)
```js
chart.tooltip = {
  "title": toolTipTitle2,
  "content": "Population: " + toolTipTitle1
};
```
* Show:

Set where we show the graphic

```js
chart.show({
  elementId: "#cedarDiv",
  width: 550,
  height: 550,
  autolabels: true
});
```
* On click event:

By clicking on any bar/pie trigger the clickBar function

```js
chart.on('click', clickBar);
```


