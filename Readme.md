# Understand JavaScript Array Functions Using Emojis

As you may be aware, JavaScript has a large number of functions to work with arrays. But this makes it hard to keep track of those functions, specially when trying to decide which one to use when writing code.

I have put this blog together to help explain those functions, the examples use Emojis to help explain the concepts in a visual way. I have personally found out they do help understand the functionality better.

Before we go to the emoji samples, let's summarize the functions by their main intention. IF you want to go to the Emojis, just click on the links.

## Use Search Functions

Use a function to search for elements within an array

| Safe? | Name                            | Purpose                              |
| :---: | ------------------------------- | ------------------------------------ |
|  ✅   | **[every(fn)](#every)**         | Does every element passes a test?    |
|  ✅   | **[filter(fn)](#filter)**       | Array with matching elements         |
|  ✅   | **[find(fn)](#find)**           | Get first matching element           |
|  ✅   | **[findIndex(fn)](#findIndex)** | Get index for first matching element |
|  ✅   | **[some(fn)](#some)**           | Does any element passes a test?      |

## Find Elements

Look for the actual elements

| Safe? | Name                                     | Purpose                              |
| :---: | ---------------------------------------- | ------------------------------------ |
|  ✅   | **[includes(element)](#includes)**       | Does the array contain this element? |
|  ✅   | **[indexOf(element)](#indexOf)**         | Get first index for this element     |
|  ✅   | **[lastIndexOf(element)](#lastIndexOf)** | Get last index for this element      |

## Process Elements

Use a function process the elements of the array

| Safe? | Name                        | Purpose                            |
| :---: | --------------------------- | ---------------------------------- |
|  ✅   | **[forEach(fn)](#forEach)** | Executes function for each element |
|  ✅   | **[map(fn)](#map)**         | Transform each element of an array |

## Change Elements Order

These functions change the order of your elements, becareful because they are not safe.

| Safe? | Name                      | Purpose                        |
| :---: | ------------------------- | ------------------------------ |
|  ❌   | **[reverse()](#reverse)** | Reverses an array              |
|  ❌   | **[sort(fn)](#sort)**     | Sorts the elements of an array |

## Aggregate

Get a single value from all the elements

| Safe? | Name                         | Purpose                                                               |
| :---: | ---------------------------- | --------------------------------------------------------------------- |
|  ✅   | **[join(separator)](#join)** | Returns a new string by concatenating all of the elements in an array |
|  ✅   | **[reduce(fn)](#reduce)**    | Executes a reducer function on each element of the array              |

### Add, Change and Remove Elements:

These functions help you get an array with different elements. Warning: Most of these functions alter the original array!

<p align="center">
    <img src="Files/SlideModifiers.png?raw=true" width="40%"/>
</p>

| Safe? | Name                                                | Purpose                                                |
| :---: | --------------------------------------------------- | ------------------------------------------------------ |
|  ✅   | **[concat(elements)](#concat)**                     | Append arrays or elements                              |
|  ❌   | **[pop()](#pop)**                                   | Removes the last element from an array                 |
|  ❌   | **[push(elements)](#push)**                         | Adds one or more elements to the end of an array       |
|  ❌   | **[shift()](#shift)**                               | Removes the first element from an array                |
|  ❌   | **[unshift(elements)](#unshift)**                   | Adds one or more elements to the beginning of an array |
|  ✅   | **[slice(start, end)](#slice)**                     | Returns a shallow copy of a portion of an array        |
|  ❌   | **[splice(start, deleteCount, elements)](#splice)** | Change the contents of an array                        |

Functions that **add** values

| Safe? | Function                        | At Start | At End |
| :---: | ------------------------------- | :------: | :----: |
|  ✅   | **[concat(values)](#concat)**   |          |   ✅   |
|  ❌   | **[push(values)](#push)**       |          |   ✅   |
|  ❌   | **[unshift(values)](#unshift)** |    ✅    |        |

Functions that **remove** values

| Safe? | Function              | At Start | At End |
| :---: | --------------------- | :------: | :----: |
|  ❌   | **[pop()](#pop)**     |          |   ✅   |
|  ❌   | **[shift()](#shift)** |    ✅    |        |

Other functions

- The **[splice(start, deleteCount, values)](#splice)** function adds and removes elements, but be very careful because it's not safe (❌), it will make changes to your arrays!
- The **[slice(start, end)](#slice)** function gives you a new arraywith a subset (start to end-1) of the elements but it's safe (✅) because does not make changes to your array.

# Syntax and samples

## Helper functions

```JavaScript
function isAnimal(emoji) {
    return '🐄🐔'.includes(emoji.trim());
}
function cook(emoji) {
    let cooked = "";
    switch (emoji.trim()) {
        case '🐄': { cooked = '🍔'; break; }
        case '🌽': { cooked = '🍿'; break; }
        case '🥔': { cooked = '🍟'; break; }
        case '🐔': { cooked = '🍗'; break; }
        default: {
            alert(`I do not know how to cook ${emoji.trim()}`);
            break;
        }
    }
    return ` ${cooked} `;
}
```

## Concat

|         |                                                                     |
| ------- | ------------------------------------------------------------------- |
| Syntax  | `array.concat([value1[, value2[, ...[, valueN]]]])`                 |
| Purpose | Returns a new array having concatenated arrays or values at the end |
| Safe?   | ✅                                                                  |

```JavaScript
let array1 = ['a', 'b', 'c'];
let array2 = ['d', 'e', 'f'];
let output = array1.concat(array2);
console.log(output); // [ 'a', 'b', 'c', 'd', 'e', 'f' ]
```

```JavaScript
let array1 = [' 🐄 ', ' 🥔 ', ' 🐔 '];
let array2 = [' 🌽 ', ' 🍔 ', ' 🍟 '];
let output = array1.concat(array2);
console.log(output); // [ ' 🐄 ', ' 🥔 ', ' 🐔 ', ' 🌽 ', ' 🍔 ', ' 🍟 ']
```

## Every

|         |                                                                                                        |
| ------- | ------------------------------------------------------------------------------------------------------ |
| Syntax  | `array.every(callback(element[, index[, array]])[, thisArg])`                                          |
| Purpose | Returns a boolean value indicating if every element passes a test implemented by the provided function |
| Safe?   | ✅                                                                                                     |

```JavaScript
let array1 = [1, 30, 39, 29, 10, 13];
let output = array1.every(currentValue => currentValue < 25);
console.log(output); // false
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.every(currentValue => isAnimal(currentValue));
console.log(output); // false
```

## Filter

|         |                                                                                               |
| ------- | --------------------------------------------------------------------------------------------- |
| Syntax  | `array.filter(callback(element[, index, [array]])[, thisArg])`                                |
| Purpose | Creates a new array with all elements that pass the test implemented by the provided function |
| Safe?   | ✅                                                                                            |

```JavaScript
let array1 = [1, 30, 39, 29, 10, 13];
let output = array1.filter(currentValue => currentValue > 25);
console.log(output); // [ 30, 39, 29 ]
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.filter(currentValue => isAnimal(currentValue));
console.log(output); // [ ' 🐄 ', ' 🐔 ' ]
```

## Find

|         |                                                                        |
| ------- | ---------------------------------------------------------------------- |
| Syntax  | `array.find(callback(element[, index[, array]])[, thisArg])`           |
| Purpose | Returns the first element that satisfies the provided testing function |
| Safe?   | ✅                                                                     |

```JavaScript
let array1 = [5, 'Banana', 8, 130, 44];
let output = array1.find(element => typeof element === 'string');
console.log(output); // 'Banana'
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.find(currentValue => isAnimal(currentValue));
console.log(output); // ' 🐄 '
```

## FindIndex

|         |                                                                                                                                                                        |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Syntax  | `array.findIndex(callback( element[, index[, array]] )[, thisArg])`                                                                                                    |
| Purpose | Returns the index of the first element in the array that satisfies the provided testing function. Otherwise, it returns -1, indicating that no element passed the test |
| Safe?   | ✅                                                                                                                                                                     |

```JavaScript
let array1 = [5, 12, 8, 130, 44];
let output = array1.findIndex(element => element > 15);
console.log(output); // 3
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.findIndex(currentValue => isAnimal(currentValue));
console.log(output); // 0
```

## ForEach

|         |                                                                        |
| ------- | ---------------------------------------------------------------------- |
| Syntax  | `array.forEach(callback(currentValue [, index [, array]])[, thisArg])` |
| Purpose | Executes a provided function once for each array element               |
| Safe?   | ✅                                                                     |

```JavaScript
let array1 = ['a', 'b', 'c'];
let output = array1.forEach(element => console.log(element));
console.log(output); // undefined
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
array1.forEach(currentValue => {
    console.log(currentValue); // 🐄, 🌽, 🐔
});
```

## Includes

|         |                                                                                                                |
| ------- | -------------------------------------------------------------------------------------------------------------- |
| Syntax  | `array.includes(valueToFind[, fromIndex])`                                                                     |
| Purpose | Determines whether an array includes a certain value among its entries, returning true or false as appropriate |
| Safe?   | ✅                                                                                                             |

```JavaScript
let array1 = ['a', 'b', 'c'];
let output = array1.includes('a');
console.log(output); // true
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.includes(' 🐔 ');
console.log(output); // true
```

## IndexOf

|         |                                                                                                        |
| ------- | ------------------------------------------------------------------------------------------------------ |
| Syntax  | `array.indexOf(searchElement[, fromIndex])`                                                            |
| Purpose | Returns the first index at which a given element can be found in the array, or -1 if it is not present |
| Safe?   | ✅                                                                                                     |

```JavaScript
let array1 = ['a', 'b', 'c'];
let output = array1.indexOf('b');
console.log(output); // 1
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.indexOf(' 🐔 ');
console.log(output); // 2
```

## Join

|         |                                                                       |
| ------- | --------------------------------------------------------------------- |
| Syntax  | `array.join([separator])`                                             |
| Purpose | Returns a new string by concatenating all of the elements in an array |
| Safe?   | ✅                                                                    |

```JavaScript
let array1 = ['a', 'b', 'c'];
let output = array1.join('-');
console.log(output); // 'a-b-c'
```

```JavaScript
let array1 = [' 🐄 ', ' 🍔 ', ' 💩 '];
let output = array1.join(' => ');
console.log(output); // ' 🐄  =>  🍔  =>  💩 '
```

## LastIndexOf

|         |                                                                                                       |
| ------- | ----------------------------------------------------------------------------------------------------- |
| Syntax  | `array.lastIndexOf(searchElement[, fromIndex])`                                                       |
| Purpose | Returns the last index at which a given element can be found in the array, or -1 if it is not present |
| Safe?   | ✅                                                                                                    |

```JavaScript
let array1 = ['a', 'b', 'c'];
let output = array1.lastIndexOf('c');
console.log(output); // 2
```

```JavaScript
let array1 = [' 🐔 ', ' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.lastIndexOf(' 🐔 ');
console.log(output); // 3
```

## Map

|         |                                                                                                                     |
| ------- | ------------------------------------------------------------------------------------------------------------------- |
| Syntax  | `let new_array = arr.map(function callback( currentValue[, index[, array]]) {`                                      |
|         | `// return element for new_array`                                                                                   |
|         | `}[, thisArg])`                                                                                                     |
| Purpose | Creates a new array populated with the results of calling a provided function on every element in the calling array |
| Safe?   | ✅                                                                                                                  |

```JavaScript
let array1 = [1, 4, 9, 16];
let output = array1.map(x => Math.sqrt(x));
console.log(output); // [ 1, 2, 3, 4 ]
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.map(currentValue => cook(currentValue));
console.log(output); // [ ' 🍔 ', ' 🍿 ', ' 🍗 ' ]
```

## Pop

|         |                                                                |
| ------- | -------------------------------------------------------------- |
| Syntax  | `array.pop()`                                                  |
| Purpose | Removes the last element from an array, returning that element |
| Safe?   | ❌                                                             |

```JavaScript
let array1 = ['a', 'b', 'c'];
let output = array1.pop();
console.log(output); // 'c'
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.pop();
console.log(output); // ' 🐔 '
```

## Push

|         |                                                                                       |
| ------- | ------------------------------------------------------------------------------------- |
| Syntax  | `array.push(element1[, ...[, elementN]])`                                             |
| Purpose | Adds one or more elements to the end of an array, returns the new length of the array |
| Safe?   | ❌                                                                                    |

```JavaScript
let array1 = ['a', 'b', 'c'];
let output = array1.push('d');
console.log(output); // 4
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ];
let output = array1.push(' 🐔 ');
console.log(output); // 3
console.log(array1); // [ ' 🐄 ', ' 🌽 ', ' 🐔 ' ]
```

## Reduce

|         |                                                                                            |
| ------- | ------------------------------------------------------------------------------------------ |
| Syntax  | `array.reduce(callback( accumulator, currentValue[, index[, array]] )[, initialValue])`    |
| Purpose | Executes a reducer function on each element of the array, resulting in single output value |
| Safe?   | ✅                                                                                         |

```JavaScript
let array1 = [1, 2, 3, 4];
let output = array1.reduce((accumulator, currentValue) => {
  return accumulator + currentValue;
}, 10);
console.log(output); // 20
```

```JavaScript
let array1 = [' 💵  ', ' 💶  ', ' 💴  ', ' 💷 ']
let output = array1.reduce((accumulator, currentValue) => ' 💰 ');
console.log(output); // ' 💰 '
```

## Reverse

|         |                   |
| ------- | ----------------- |
| Syntax  | `array.reverse()` |
| Purpose | Reverses an array |
| Safe?   | ❌                |

```JavaScript
let array1 = ['a', 'b', 'c'];
let output = array1.reverse();
console.log('original:', array1); // 'original:' [ 'c', 'b', 'a' ]
console.log('reversed:', output); // 'reversed:' [ 'c', 'b', 'a' ]
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let array2 = array1.reverse();
console.log('original:', array1); // 'original:' [ ' 🐔 ', ' 🌽 ', ' 🐄 ' ]
console.log('reversed:', array2); // 'reversed:' [ ' 🐔 ', ' 🌽 ', ' 🐄 ' ]
```

## Shift

|         |                                                                          |
| ------- | ------------------------------------------------------------------------ |
| Syntax  | `array.shift()`                                                          |
| Purpose | Removes the first element from an array and returns that removed element |
| Safe?   | ❌                                                                       |

```JavaScript
let array1 = ['a', 'b', 'c'];
let output = array1.shift();
console.log(array1); // [ 'b', 'c' ]
console.log(output); // 'a'
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.shift();
console.log(array1); // [ ' 🌽 ', ' 🐔 ' ]
console.log(output); // ' 🐄 '
```

## Slice

|         |                                                                                                  |
| ------- | ------------------------------------------------------------------------------------------------ |
| Syntax  | `array.slice([start[, end]])`                                                                    |
| Purpose | Returns a shallow copy of a portion of an array selected from start (included) to end (excluded) |
| Safe?   | ✅                                                                                               |

```JavaScript
let array1 = ['a', 'b', 'c', 'd', 'e'];
let output = array1.slice(2, 4);
console.log(output); // [ 'c', 'd' ]
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.slice(1,2);
console.log(output); // [ ' 🌽 ' ]
```

## Some

|         |                                                                                                      |
| ------- | ---------------------------------------------------------------------------------------------------- |
| Syntax  | `array.some(callback(element[, index[, array]])[, thisArg])`                                         |
| Purpose | Tests whether at least one element in the array passes the test implemented by the provided function |
| Safe?   | ✅                                                                                                   |

```JavaScript
let array1 = ['a', 'b', 'c', '4', 'e'];
let output = array1.some(element => element % 2 === 0);
console.log(output); // true
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.some(currentValue => isAnimal(currentValue));
console.log(output); // true
```

## Sort

|         |                                             |
| ------- | ------------------------------------------- |
| Syntax  | `array.sort([callback(firstEl, secondEl)])` |
| Purpose | Sorts the elements of an array              |
| Safe?   | ❌                                          |

```JavaScript
let array1 = ['a', 'd', 'c', 'b'];
let output = array1.sort();
console.log(array1); // [ 'a', 'b', 'c', 'd' ]
console.log(output); // [ 'a', 'b', 'c', 'd' ]
```

```JavaScript
let array1 = [4, 2, 5, 1, 3];
let output = array1.sort((a, b) => (a < b ? -1 : 1));
console.log(array1); // [1, 2, 3, 4, 5]
console.log(output); // [1, 2, 3, 4, 5]
```

```JavaScript
// This settles down the debate!
let array1 = [' 🥚 ', ' 🐔 '];
let whatWasFirst = array1.sort();
console.log(whatWasFirst); // [ ' 🐔 ', ' 🥚 ' ]
```

## Splice

|         |                                                                                |
| ------- | ------------------------------------------------------------------------------ |
| Syntax  | `let arrDeleted = array.splice(start[, deleteCount[, item1[, item2[, ...]]]])` |
| Purpose | Changes the contents of an array                                               |
| Safe?   | ❌                                                                             |

**Notes:**

The changes to the array include:

- Removing elements
- Replacing existing elements
- Adding new elements in place.

The parameters for this function are:

- Start
  - The index at which to start changing the array
  - `start > array.length`: No elements will be deleted but elements could be appended to the array
  - `start < 0`: Begins at the end (array.length - n)
  - `array.length + start < 0`: begin from index 0
- deleteCount
  - An integer indicating the number of elements in the array to remove from start
  - If _deleteCount_ is omitted or id `deleteCount > array.length - start` then all the elements from start to the end of the array will be deleted
  - `deleteCount = 0` (or negative): no elements are removed
- item1, item2, …
  - Elements to add to the array, beginning from the `start` position

This function returs an array containing the deleted elements

```JavaScript
let output;
let array1 = ['A0', 'B1', 'B2', 'B3', 'C4', 'F5'];
output = array1.splice(2, 2); // Remove Elements ('B2', 'B3')
console.log('1 => ' + JSON.stringify(output)); // 1 => ['B2','B3']
console.log(array1); // [ 'A0', 'B1', 'C4', 'E5', 'F6' ]
output = array1.splice(2, 1, 'C2'); // Replace Elements ('C4' => 'C2')
console.log('2 => ' + JSON.stringify(output)); // 2 => ['C4']
console.log(array1); // [ 'A0', 'B1', 'C2', 'E5', 'F6' ]
output = array1.splice(3, 0, 'D3', 'E4'); // Adding new elements ('D3', ''E4')
console.log('3 => ' + JSON.stringify(output)); // 3 => []
console.log(array1); // [ 'A0', 'B1', 'C2', 'D3', 'E4', 'F5' ]
```

```JavaScript
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.splice(1, 1, ' 🐶 ');
console.log(array1); // [ ' 🐄 ', ' 🐶 ', ' 🐔 ' ]
console.log(output); // [ ' 🌽 ' ]
```

## Unshift

|         |                                                                                                |
| ------- | ---------------------------------------------------------------------------------------------- |
| Syntax  | `array.unshift(element1[, ...[, elementN]])`                                                   |
| Purpose | Adds one or more elements to the beginning of an array and returns the new length of the array |
| Safe?   | ❌                                                                                             |

```JavaScript
let array1 = [4, 5, 6];
let output = array1.unshift(1, 2, 3);
console.log(output); // 6
console.log(array1); // [ 1, 2, 3, 4, 5, 6 ]
```

```JavaScript
let array1 = [' 🌽 ', ' 🍔 ', ' 🍟 '];
let output = array1.unshift(' 🐄 ', ' 🥔 ', ' 🐔 ');
console.log(array1); // [ ' 🐄 ', ' 🥔 ', ' 🐔 ', ' 🌽 ', ' 🍔 ', ' 🍟 ']
console.log(output); // 6
```
