# Understand JavaScript Array Functions Using Emojis

As you may be aware, JavaScript has a large number of functions to work with arrays. But this makes it hard to keep track of them and to decide which one you can use to help you solve your use case. I have put this blog together to explain those functions and help you find the proper one. The examples use emojis to help explain them visually.

Before we go to the emoji samples, let's summarize the functions by their main intention.

## Use Search Functions [x][#concat]

Use a function to search for elements within an array

| Safe? | Name              | Purpose                              |
| :---: | ----------------- | ------------------------------------ |
|  ✅   | **every(fn)**     | Does every element passes a test?    |
|  ✅   | **filter(fn)**    | Array with matching elements         |
|  ✅   | **find(fn)**      | Get first matching element           |
|  ✅   | **findIndex(fn)** | Get index for first matching element |
|  ✅   | **some(fn)**      | Does any element passes a test?      |

## Find Elements

Look for the actual elements

| Safe? | Name                     | Purpose                              |
| :---: | ------------------------ | ------------------------------------ |
|  ✅   | **includes(element)**    | Does the array contain this element? |
|  ✅   | **indexOf(element)**     | Get first index for this element     |
|  ✅   | **lastIndexOf(element)** | Get last index for this element      |

## Process Elements

Use a function process the elements of the array

| Safe? | Name            | Purpose                            |
| :---: | --------------- | ---------------------------------- |
|  ✅   | **forEach(fn)** | Executes function for each element |
|  ✅   | **map(fn)**     | Transform each element of an array |

## Change Elements Order

These functions change the order of your elements, becareful because they are not safe.

| Safe? | Name          | Purpose                        |
| :---: | ------------- | ------------------------------ |
|  ❌   | **reverse()** | Reverses an array              |
|  ❌   | **sort(fn)**  | Sorts the elements of an array |

## Aggregate

Get a single value from all the elements

| Safe? | Name                | Purpose                                                               |
| :---: | ------------------- | --------------------------------------------------------------------- |
|  ✅   | **join(separator)** | Returns a new string by concatenating all of the elements in an array |
|  ✅   | **reduce(fn)**      | Executes a reducer function on each element of the array              |

### Add/Change/Remove Elements:

These functions help you get an array with different elements. Warning: Most of these functions alter the original array!

| Safe? | Name                                     | Purpose                                                |
| :---: | ---------------------------------------- | ------------------------------------------------------ |
|  ✅   | **concat(elements)**                     | Append arrays or elements                              |
|  ❌   | **pop()**                                | Removes the last element from an array                 |
|  ❌   | **push(elements)**                       | Adds one or more elements to the end of an array       |
|  ❌   | **shift()**                              | Removes the first element from an array                |
|  ✅   | **slice(start, end)**                    | Returns a shallow copy of a portion of an array        |
|  ❌   | **splice(start, deleteCount, elements)** | Change the contents of an array                        |
|  ❌   | **unshift(elements)**                    | Adds one or more elements to the beginning of an array |

Functions that **add** values

| Safe? | Function            | At Start | At End |
| :---: | ------------------- | :------: | :----: |
|  ✅   | **concat(values)**  |          |   ✅   |
|  ❌   | **push(values)**    |          |   ✅   |
|  ❌   | **unshift(values)** |    ✅    |        |

Functions that **remove** values

| Safe? | Function    | At Start | At End |
| :---: | ----------- | :------: | :----: |
|  ❌   | **pop()**   |          |   ✅   |
|  ❌   | **shift()** |    ✅    |        |

Other functions

-   The **splice(start, deleteCount, values)** function adds and removes elements, but be very careful because it's not safe (❌), it will make changes to your arrays!
-   The **slice(start, end)** function gives you a new arraywith a subset (start to end-1) of the elements but it's safe (✅) because does not make changes to your array.

# Syntax and samples

## concat

|         |                                                                     |
| ------- | ------------------------------------------------------------------- |
| Safe?   | ✅                                                                  |
| Syntax  | `array.concat([value1[, value2[, ...[, valueN]]]])`                 |
| Purpose | Returns a new array having concatenated arrays or values at the end |

```
let array1 = ['a', 'b', 'c'];
let array2 = ['d', 'e', 'f'];
let output = array1.concat(array2);
console.log(output); // [ 'a', 'b', 'c', 'd', 'e', 'f' ]
```

```
let array1 = [' 🐄 ', ' 🥔 ', ' 🐔 '];
let array2 = [' 🌽 ', ' 🍔 ', ' 🍟 '];
let output = array1.concat(array2);
console.log(output); // [ ' 🐄 ', ' 🥔 ', ' 🐔 ', ' 🌽 ', ' 🍔 ', ' 🍟 ']
```

|

:
:
:
:
:

x

x

x

x

x

❌✅

```

```
