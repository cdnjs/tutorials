# Sort dataset by values

## Result

![# d3.statosio](https://d3.statosio.com/assets/images/example-sort-400.jpg)<br>
[Sort dataset by values](https://d3.statosio.com/tutorials/sort-data.html)

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
                        "dataSortCurrent" : "values", 
                        "dataSortByValues" : "ascending", 
                        "showAverage" : false,
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


### 6: Add "data" options

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
                        "dataSortCurrent" : "values", 
                        "dataSortByValues" : "ascending"
                    }
                )
            } 
        )
    </script>
</body>
```

- Option explained

| **Name** | **Description** | **Details** | 
| [dataSortCurrent](https://d3.statosio.com/options/data__sort__current.html) | Set the general route for sorting. You can choose between "none", "values", "names". | "values" |
| [dataSortByValues](https://d3.statosio.com/options/data__sort__by__values.html) | Here you can set type of sorting. You can choose between "ascending" and "decending" | "ascending" |

List of all "data" Options: [here](https://d3.statosio.com/options/index.html#data)


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
                        "dataSortCurrent" : "values", 
                        "dataSortByValues" : "ascending", 
                        "showAverage" : false,
                    }
                )
            } 
        )
    </script>
</body>
```

- Option explained

| **Name** | **Description** | **Details** | 
| [showAverage](https://d3.statosio.com/options/show__average.html) | Calculate and show average line | false |

List of all "show" Options: [here](https://d3.statosio.com/options/index.html#show)