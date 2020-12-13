# Change style to dark-mode

## Result

![# d3.statosio](https://d3.statosio.com/assets/images/example-customize-400.jpg)<br>
[Change style to dark-mode](https://d3.statosio.com/tutorials/change-style.html)

```html
<!DOCTYPE html>
<head>
    <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js"></script>
</head>
<body>
    <script>
        d3.json( "https://d3.statosio.com/data/performance.json" )
            .then( ( file ) => {
                d3.statosio( 
                    file, 
                    "name", 
                    [ "mobile" ], 
                    { 
                        "styleColorSelectorsChart": ["#E2B08E", "#CC8074"],
                        "styleColorCanvasBackground" : "none",
                        "styleColorGridline" : "#2F3138",
                        "styleStrokeGridline" : 1,
                        "styleColorFont" : "#BABABA",
                        "styleColorSelectorsText" : ["#E2B08E", "#BABABA"],
                        "showAverage" : false
                    }
                )
            } 
        )
    </script>
</body>
```


## Steps

We need following files.

| **Name** | **Source** | **Description** |
|:---|:---|:---|
| d3.js | [https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js](https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js) | d3.js Library | 
| statosio.js | [https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js](https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js) | statosio.js Library | 
| performance.json | [https://d3.statosio.com/data/performance.json](https://d3.statosio.com/data/performance.json) | Dataset |

- statosio.js Structure

```javascript
d3.statosio( source, x, y, options )
``````

| | **Value** | **Type** |
|------:|:------|:------|
| **Source** | ```[{},{}...]``` | Array of Objects |
| **X** | ```"name"``` | String |
| **Y** | ```[ "mobile" ]``` | Array of Strings or String |
| **Options** | ```{}``` | Object |


### 1: HTML Structure
Set HTML Structure

```html
<!DOCTYPE html>
<head>
    <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
</head>
<body>
</body>
```

### 2: Load d3.js
Insert ```<script>``` Element to load d3.js library.

```html
<!DOCTYPE html>
<head>
    <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js"></script>
</head>
<body>
</body>
```

### 3: Load statosio.js
Insert ```<script>``` Element to load statosio.js.

```html
<!DOCTYPE html>
<head>
    <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js"></script>
</head>
<body>
</body>

```
[Source Code](https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js)


### 4: Load dataset
d3.js expect a json array with object in it: ```[ {},{}...]```

```html
<!DOCTYPE html>
<head>
    <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js"></script>
</head>
<body>
    <script>
        d3.json( "https://d3.statosio.com/data/performance.json" )
            .then( ( file ) => {

            } 
        )
    </script>
</body>
```
[Example Dataset](https://d3.statosio.com/data/performance.json)

### 5: Set dataset ranges
Load diagram

```html
<!DOCTYPE html>
<head>
    <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js"></script>
</head>
<body>
    <script>
        d3.json( "https://d3.statosio.com/data/performance.json" )
            .then( ( file ) => {
                d3.statosio( 
                    file, 
                    "name", 
                    [ "mobile" ], 
                    {}
                )
            } 
        )
    </script>
</body>
```

[Example Dataset](https://d3.statosio.com/data/performance.json)


### 6: Add "style" options

```html
<!DOCTYPE html>
<head>
    <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js"></script>
</head>
<body>
    <script>
        d3.json( "https://d3.statosio.com/data/performance.json" )
            .then( ( file ) => {
                d3.statosio( 
                    file, 
                    "name", 
                    [ "mobile" ], 
                    { 
                        "styleColorSelectorsChart": ["#E2B08E", "#CC8074"],
                        "styleColorCanvasBackground" : "none",
                        "styleColorGridline" : "#2F3138",
                        "styleStrokeGridline" : 1,
                        "styleColorFont" : "#BABABA",
                        "styleColorSelectorsText" : ["#E2B08E", "#BABABA"]
                    }
                )
            } 
        )
    </script>
</body>
```

- Colors in use.

| **Color** | **Hex** | **Used for** | 
|:---|:---|:---|
| <svg width="20" height="20"><rect width="20" height="20" style="fill:#E2B08E;stroke-width:3;stroke:rgb(0,0,0)" /></svg> | #E2B08E | Highlight bar chart color |
| <svg width="20" height="20"><rect width="20" height="20" style="fill:#CC8074;stroke-width:3;stroke:rgb(0,0,0)" /></svg> | #CC8074 | Default bar chart color |
| <svg width="20" height="20"><rect width="20" height="20" style="fill:#2F3138;stroke-width:3;stroke:none" /></svg> | #2F3138 | Gridline Color |
| <svg width="20" height="20"><rect width="20" height="20" style="fill:#BABABA;stroke-width:3;stroke:rgb(0,0,0)" /></svg> | #BABABA | Default text color |

- Options explained

| **Name** | **Description** | **Details** | 
|:---|:---|:---|
| [styleColorSelectorsChart](https://d3.statosio.com/options/style__color__selectors__chart.html) | Colorize the chart of the selection. Use "hex" values or "html" color-names. | ["#E2B08E", "#CC8074"] |
| [styleColorCanvasBackground](https://d3.statosio.com/options/style__color__canvas_background.html) | Set background color. | "none" |
| [styleColorGridline](https://d3.statosio.com/options/style__color__gridline.html) | Set the gridline color. Use "hex" value or "html" color-names. | "#2F3138" |
| [styleStrokeGridline](https://d3.statosio.com/options/style__stroke__gridline.html) | Set stroke weight of gridline. | 1 |
| [styleColorFont](https://d3.statosio.com/options/style__color__font.html)  | Set default font color. Excluding non-selection content. | "#BABABA" |
| [styleColorSelectorsText](https://d3.statosio.com/options/style__color__selectors__text.html) | Colorize the font of the selection. Use "hex" values or "html" color-names. | ["#E2B08E", "#BABABA"] |

List of all "style" Options: [here](https://d3.statosio.com/options/index.html#style)


### 7: Add "show" options

```html
<!DOCTYPE html>
<head>
    <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js"></script>
</head>
<body>
    <script>
        d3.json( "https://d3.statosio.com/data/performance.json" )
            .then( ( file ) => {
                d3.statosio( 
                    file, 
                    "name", 
                    [ "mobile" ], 
                    { 
                        "styleColorSelectorsChart": ["#E2B08E", "#CC8074"],
                        "styleColorCanvasBackground" : "none",
                        "styleColorGridline" : "#2F3138",
                        "styleStrokeGridline" : 1,
                        "styleColorFont" : "#BABABA",
                        "styleColorSelectorsText" : ["#E2B08E", "#BABABA"],
                        "showAverage" : false
                    }
                )
            } 
        )
    </script>
</body>
```

- Option explained

| **Name** | **Description** | **Details** | 
|:---|:---|:---|
| [showAverage](https://d3.statosio.com/options/show__average.html) | Calculate and show average line | false |

List of all "show" Options: [here](https://d3.statosio.com/options/index.html#show)