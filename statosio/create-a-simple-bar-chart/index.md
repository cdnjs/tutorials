# Create a simple bar chart

## Result

![# d3.statosio](https://d3.statosio.com/assets/images/example-bar-400.jpg)<br>

```html
<!DOCTYPE html>
<head>
    <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js" integrity="sha512-I54fxhTJwRigWTc3uNjgDzgii7LW+WJuyyA8kc6WaaZ7RQQNAf8bOEJLRNav7n/ca09MUwl5FptUukvqrOTUvQ==" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js" integrity="sha512-cpZ1Pq+WxFjYMahfsghI7nRqv7FVeZLH5CirYPLX11iF6jWfMgkvYVp3UYQ/W109s/3RWtyFNM0wPUOpGfNLJA==" crossorigin="anonymous"></script>
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
                        "showAverage" : false,
                    }
                )
            } 
        )
    </script>
</body>
```


## Steps

- We need following files.

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
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js" integrity="sha512-I54fxhTJwRigWTc3uNjgDzgii7LW+WJuyyA8kc6WaaZ7RQQNAf8bOEJLRNav7n/ca09MUwl5FptUukvqrOTUvQ==" crossorigin="anonymous"></script>
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
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js" integrity="sha512-I54fxhTJwRigWTc3uNjgDzgii7LW+WJuyyA8kc6WaaZ7RQQNAf8bOEJLRNav7n/ca09MUwl5FptUukvqrOTUvQ==" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js" integrity="sha512-cpZ1Pq+WxFjYMahfsghI7nRqv7FVeZLH5CirYPLX11iF6jWfMgkvYVp3UYQ/W109s/3RWtyFNM0wPUOpGfNLJA==" crossorigin="anonymous"></script>
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
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js" integrity="sha512-I54fxhTJwRigWTc3uNjgDzgii7LW+WJuyyA8kc6WaaZ7RQQNAf8bOEJLRNav7n/ca09MUwl5FptUukvqrOTUvQ==" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js" integrity="sha512-cpZ1Pq+WxFjYMahfsghI7nRqv7FVeZLH5CirYPLX11iF6jWfMgkvYVp3UYQ/W109s/3RWtyFNM0wPUOpGfNLJA==" crossorigin="anonymous"></script>
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
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js" integrity="sha512-I54fxhTJwRigWTc3uNjgDzgii7LW+WJuyyA8kc6WaaZ7RQQNAf8bOEJLRNav7n/ca09MUwl5FptUukvqrOTUvQ==" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js" integrity="sha512-cpZ1Pq+WxFjYMahfsghI7nRqv7FVeZLH5CirYPLX11iF6jWfMgkvYVp3UYQ/W109s/3RWtyFNM0wPUOpGfNLJA==" crossorigin="anonymous"></script>
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


### 6: Add "show" options

```html
<!DOCTYPE html>
<head>
    <meta content="text/html;charset=utf-8" http-equiv="Content-Type">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/d3/6.2.0/d3.js" integrity="sha512-I54fxhTJwRigWTc3uNjgDzgii7LW+WJuyyA8kc6WaaZ7RQQNAf8bOEJLRNav7n/ca09MUwl5FptUukvqrOTUvQ==" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/statosio/0.9/statosio.js" integrity="sha512-cpZ1Pq+WxFjYMahfsghI7nRqv7FVeZLH5CirYPLX11iF6jWfMgkvYVp3UYQ/W109s/3RWtyFNM0wPUOpGfNLJA==" crossorigin="anonymous"></script>
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
|:---|:---|:---|
| [showAverage](https://d3.statosio.com/options/show__average.html) | Calculate and show average line | false |

List of all "show" Options: [here](https://d3.statosio.com/options/index.html#show)