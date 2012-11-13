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

# List of Options 

Any subset of these can be passed as a second parameter to tablify, in a dictionary.

  - `show_index`   include a column showing the row number of each row. The default is `false` unless tablify is passed an array of dictionaries, in which case the default is `true`
  - `has_header`   include the first row as a header; this defaults to `false` unless passed an array of dicts, in which case 
  - `keys`         which columns to use, when tablifying an array of dictionaries; by default all keys are used in alphabetical order
  - `row_start`    default = '| '
  - `row_end`      default = ' |'
  - `spacer`       default = ' | '
  - `row_sep_char` default = '-'


```coffee-script
data = [
	[1,2,3], 
	["cat","dog",Math.PI]
]
console.log tablify data, {show_index: true}
```


# Installation
```
> npm install -g tablify
```
