# JavaScript array cheat sheet

* [Create an array](#create-an-array)
* [Empty an array](#empty-an-array)
* [Clone an array](#clone-an-array)
* [Get first item](#get-first-item)
* [Get last item](#get-last-item)
* [Remove first item](#remove-first-item)
* [Remove last item](#remove-last-item)
* [Add new item(s) to beginning](#add-new-items-to-beginning)
* [Add new item(s) to end](#add-new-items-to-end)
* [Overwrite item at a specific index](#overwrite-item-at-a-specific-index)
* [Add new item(s) at a specific index](#add-new-items-at-a-specific-index)
* [Remove single item at a specific index](#remove-single-item-at-a-specific-index)
* [Remove several items](#remove-several-items)
* [Reverse an array](#reverse-an-array)
* [Delimit an array](#delimit-an-array)
* [Sort in numerical order](#sort-in-numerical-order)
* [Sort in alphabetical order](#sort-in-alphabetical-order)
* [Join two arrays together](#join-two-arrays-together)
* [Copy specific item(s)](#copy-specific-items)
* [Augment items within an array](#augment-items-within-an-array)
* [Return true if every item meets a condition](#return-true-if-every-item-meets-a-condition)
* [Return true if at least one item matches a condition](#return-true-if-at-least-one-item-matches-a-condition)
* [Execute a function once per array item](#execute-a-function-once-per-array-item)
* [Filter an array](#filter-an-array)
* [Detect an array](#detect-an-array)
  * [ES5 and above](#es5-and-above)
  * [ES4 and below](#es4-and-below)
* [Simple FIFO queue](#simple-fifo-queue)
* [Find index of an item](#find-index-of-an-item)
  * [ES5 and above](#es5-and-above-1)
  * [ES4 and below](#es4-and-below-1)
* [Randomise an array](#randomise-an-array)
* [Chaining methods](#chaining-methods)

For documentation on JavaScript Array object and its methods go [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).


## Create an array

With `Array` constructor (not recommended)

```javascript
var meals = new Array('breakfast', 'lunch', 'dinner')

meals
// ['breakfast', 'lunch', 'dinner']
```

With array literal notation

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals
// ['breakfast', 'lunch', 'dinner']
```

## Empty an array

Replace an array with an empty array

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals = []
```

Set an array’s length to `0`

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals.length = 0
```

With `splice` method

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals.splice(0, meals.length)
```

## Clone an array

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

var copy = meals.slice()
// ['breakfast', 'lunch', 'dinner']
```

## Get first item

```javascript

var meals = ['breakfast', 'lunch', 'dinner']

meals[0]
// 'breakfast'
```

## Get last item

```javascript

var meals = ['breakfast', 'lunch', 'dinner']

meals[meals.length - 1]
// 'dinner'
```

Or

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals.slice(-1)[0]
// 'dinner'
```

## Remove first item

```javascript

var meals = ['breakfast', 'lunch', 'dinner']

meals.shift()
// 'breakfast'

meals
// ['lunch', 'dinner']
```

## Remove last item

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals.pop()
// 'dinner'

meals
// ['breakfast', 'lunch']
```

## Add new item(s) to beginning

```javascript
var meals = ['lunch', 'dinner']

meals.unshift('breakfast')
// 3 – the array length

meals
// ['breakfast', 'lunch', 'dinner']
```

## Add new item(s) to end

```javascript

var meals = ['breakfast', 'lunch', 'dinner']

meals.push('supper')
// 4 – the array length

meals
// ['breakfast', 'lunch', 'dinner', 'supper']
```

## Overwrite item at a specific index

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals[1] = 'brunch'
// ['breakfast', 'brunch', 'dinner']
```

Or
```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals.splice(1, 1, 'brunch')
// ['breakfast', 'brunch', 'dinner']
```

## Add new item(s) at a specific index

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals.splice(1, 0, 'brunch', 'more brunch')
// ['breakfast', 'brunch', 'more brunch', 'lunch', 'dinner']
```

## Remove single item at a specific index

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals.splice(1, 1)
// ['lunch']

meals
// ['breakfast', 'dinner']
```

## Remove several items

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals.splice(1, 2)
// ['lunch', 'dinner']

meals
// ['breakfast']
```

## Reverse an array

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

meals.reverse()
// ['dinner', 'lunch', 'breakfast']
```

## Delimit an array

```javascript

var meals = ['breakfast', 'lunch', 'dinner']

meals.join(' AND ')
// 'breakfast AND lunch AND dinner'
```

## Sort in alphabetical order

```javascript

var meals = ['dinner', 'supper', 'breakfast', 'lunch']

meals.sort()
// ['breakfast', 'dinner', 'lunch', 'supper']
```

## Sort in numerical order

```javascript
var numbers = [1438, 2605, 794, 3947, 6241, 11745, 2585]

numbers.sort(function(a, b) {
    return a - b
})
// [794, 1438, 2585, 2605, 3947, 6241, 11745]
```

## Join two arrays together

```javascript
var dayTimeMeals = ['breakfast', 'lunch']
var nightTimeMeals = ['merienda', 'dinner']

var allTheMeals = dayTimeMeals.concat(nightTimeMeals)
// ['breakfast', 'lunch', 'merienda', 'dinner']
```

## Copy specific item(s)

```javascript
var meals = ['breakfast', 'lunch', 'dinner', 'supper']

nightTimeMeals = meals.slice(2, 4)
// ['dinner', 'supper']
```

## Augment items within an array

```javascript
var meals = ['breakfast', 'lunch', 'dinner']
var type = ['king', 'prince', 'pauper']

meals.map(function(item, i) {
  return item + ' like a ' + type[i]
})
// ["breakfast like a king", "lunch like a prince", "dinner like a pauper"]
```

## Return true if every item meets a condition

```javascript
var meals = ['breakfast', 'lunch', 'dinner', 'supper']

meals.every(function(item){ return item.length > 0 })
// true

meals.every(function(item){ return item.length > 6 })
// false
```

## Return true if at least one item matches a condition

```javascript
var meals = ['breakfast', 'lunch', 'dinner', 'supper']

meals.some(function(item) {
  return item === 'lunch'
})
// true

meals.some(function(item) {
  return item === 'burgers!!'
})
// false
```

## Execute a function once per array item

```javascript
var meals = ['breakfast', 'lunch', 'dinner', 'supper']

meals.forEach(function(currentValue, index, arr){
  console.log(index, currentValue, arr)
})
```

## Filter an array

```javascript
var meals = ['breakfast', 'lunch', 'dinner', 'supper']

meals.filter(function(item) {
  return item !== 'breakfast'
})
// ['lunch', 'dinner', 'supper']
```
## Detect an array

### ES5 and above

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

Array.isArray(meals)
// true
```

### ES4 and below

```javascript
var meals = ['breakfast', 'lunch', 'dinner']

function isArray(arr) {
  return !!(Object.prototype.toString.call(arr) === '[object Array]')
}

isArray(meals)
// true
```

## Simple FIFO queue

```javascript
var meals = ['breakfast', 'elevenses', 'brunch']

meals.shift()
meals.push('lunch')

// ['elevenses', 'brunch', 'lunch']

meals.shift()
meals.push('afternoon tea')

// ['brunch', 'lunch', 'afternoon tea']
// ... and so on ...
```

## Find index of an item

## ES5 and above

```javascript
var meals = ['breakfast', 'elevenses', 'brunch']
meals.indexOf('brunch')
// 2
```

### ES4 and below

```javascript
var meals = ['breakfast', 'elevenses', 'brunch']

function inArray(arr, item){
  var found = -1,
      i = arr.length

  while(--i >= 0) {
    if(arr[i] === item){
      found = i
      break
    }
  }
  return found
}

inArray(meals, 'brunch')
// 2 - the index of the item in the array

inArray(meals, 'dinner')
// -1
```

## Randomise an array

```javascript
function randomiseArray(arr) {
    var buffer = [], start

    for(var i = arr.length i >= arr.length && i > 0i--) {
        start = Math.floor(Math.random() * arr.length)
        buffer.push(arr.splice(start, 1)[0])
    }

    return buffer
}

randomiseArray([0, 1, 2, 3, 4])
// [2, 1, 0, 3, 4]

randomiseArray([0, 1, 2, 3, 4])
// [3, 2, 1, 4, 0]

randomiseArray([0, 1, 2, 3, 4])
// [1, 2, 4, 0, 3]
```

# Chaining methods

```javascript
var meals = [
  {type: 'breakfast', name: 'Full English', calories: 1500},
  {type: 'breakfast', name: 'Colacao', calories: 260},
  {type: 'breakfast', name: 'Croissant and jam', calories: 520},
  {type: 'breakfast', name: 'Granola with Greek yoghurt and blueberries', calories: 680},
  {type: 'brinner', name: 'Shepherds Pie with strawberry yoghurt', calories: 915},
  {type: 'brinner', name: 'Milky Porridge with beef and green beans', calories: 875},
  {type: 'dinner', name: 'Phad Thai', calories: 750},
  {type: 'dinner', name: 'Chicken Katsu curry and rice', calories: 830},
]

function getMealsByMaxCalories(meals, maxCalories, dailyAllowance) {
  return meals
    .filter(function(meal) {
        return meal.calories <= maxCalories
    })
    .map(function(meal) {
        return {
            name: meal.name,
            calories: meal.calories,
            percentageOfDailyAllowance: meal.calories / dailyAllowance * 100
        }
    })
}

getMealsByMaxCalories(meals, 850, 2000)

/*
[
  {
    "name": "Colacao",
    "calories": 260,
    "percentageOfDailyAllowance": 13
  },
  {
    "name": "Croissant and jam",
    "calories": 520,
    "percentageOfDailyAllowance": 26
  },
  {
    "name": "Granola with Greek yoghurt and blueberries",
    "calories": 680,
    "percentageOfDailyAllowance": 34
  },
  {
    "name": "Phad Thai",
    "calories": 750,
    "percentageOfDailyAllowance": 37.5
  }
]
*/
```
