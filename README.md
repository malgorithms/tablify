tablify
=======

In nodeJs programs, it's a pain to print data structures to the console. `tablify` turns an array of structures into a pretty-printed table.

For example:

```coffee-script
tablify = require('tablify').tablify
data = [
	[1,2,3], 
	["cat","dog",Math.PI]
]
console.log tablify data
```

Output:
```
---------------------------------
| 1   | 2   | 3                 |
| cat | dog | 3.141592653589793 |
---------------------------------
```

### Showing headers

If your structure has a header row, pass the optional "has_header" param:

```coffee-script
data = [
	["name","age"]
	["Chris","Max"] 
	[10,8]
]
console.log tablify data, {has_header: true}
```

Output:
```
---------------
| name  | age |
---------------
| Chris | Max |
| 10    | 8   |
---------------
```

### Including row numbers

data = [
	[1,2,3], 
	["cat","dog",Math.PI]
]
console.log tablify data, {show_index: true}
```

### Even cooler: an array of dictionaries

Even with inconsistent keys, you can print an array of dictionaries:

```coffee-script
data = [
	{name: "Chris", age: 16, gender: "M"} 
	{name: "Max",   age: 12, gender: "M"}
	{name: "Sam",            gender: "F", colors: ["Orange", "Blue"]}
]
console.log tablify data
```

Output:
```
-------------------------------------------------
| # | age  | colors            | gender | name  |
-------------------------------------------------
| 0 | 16   |                   | M      | Chris |
| 1 | 12   |                   | M      | Max   |
| 2 |      | ["Orange","Blue"] | F      | Sam   |
-------------------------------------------------
```

### Selecting only specific keys:
```
console.log tablify data, {keys: ["age","name"]}
```

Output:
```
--------------------
| # | age  | name  |
--------------------
| 0 | 16   | Chris |
| 1 | 12   | Max   |
| 2 |      | Sam   |
--------------------
```

# Installation
```
> npm install -g tablify
```
