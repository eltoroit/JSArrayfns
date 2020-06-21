# Understand JavaScript Array Functions Using Emojis

As you may be aware, JavaScript has a large number of functions to work with arrays. But this makes it hard to keep track of them and to decide which one you can use to help you solve your use case. I have put this blog together to explain those functions and help you find the proper one. The examples use emojis to help explain them visually.

Before we go to the emoji samples, let's summarize the functions by their main intention.

## Use Search Functions

Use a function to search for elements within an array

| Safe? | Name                     | Purpose                              |
| :---: | ------------------------ | ------------------------------------ |
|  ✅   | **[every(fn)](#every)** | Does every element passes a test?    |
|  ✅   | **filter(fn)**           | Array with matching elements         |
|  ✅   | **find(fn)**             | Get first matching element           |
|  ✅   | **findIndex(fn)**        | Get index for first matching element |
|  ✅   | **some(fn)**             | Does any element passes a test?      |

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
|  ✅   | **[concat(elements)](#concat)**         | Append arrays or elements                              |
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

## Concat

|         |                                                                     |
| ------- | ------------------------------------------------------------------- |
| Syntax  | `array.concat([value1[, value2[, ...[, valueN]]]])`                 |
| Purpose | Returns a new array having concatenated arrays or values at the end |
| Safe?   | ✅                                                                  |

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

## Every

|         |                                                                                                        |
| ------- | ------------------------------------------------------------------------------------------------------ |
| Syntax  | `array.every(callback(element[, index[, array]])[, thisArg])`                                          |
| Purpose | Returns a boolean value indicating if every element passes a test implemented by the provided function |
| Safe?   | ✅                                                                                                     |

```
let array1 = [1, 30, 39, 29, 10, 13];
let output = array1.every(currentValue => currentValue < 25);
console.log(output); // false
```

```
let isAnimal = {' 🐄 ':true, ' 🌽 ':false, ' 🐔 ':true};
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.every(currentValue => isAnimal[currentValue]);
console.log(output); // false
```

## Filter

|         |                                                                                               |
| ------- | --------------------------------------------------------------------------------------------- |
| Syntax  | `array.filter(callback(element[, index, [array]])[, thisArg])`                                |
| Purpose | Creates a new array with all elements that pass the test implemented by the provided function |
| Safe?   | ✅                                                                                            |

```
let array1 = [1, 30, 39, 29, 10, 13];
let output = array1.filter(currentValue => currentValue > 25);
console.log(output); // [ 30, 39, 29 ]
```

```
let isAnimal = {' 🐄 ':true, ' 🌽 ':false, ' 🐔 ':true};
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.filter(currentValue => isAnimal[currentValue]);
console.log(output); // [ ' 🐄 ', ' 🐔 ' ]
```

## Find

|         |                                                                        |
| ------- | ---------------------------------------------------------------------- |
| Syntax  | `array.find(callback(element[, index[, array]])[, thisArg])`           |
| Purpose | Returns the first element that satisfies the provided testing function |
| Safe?   | ✅                                                                     |

```
let array1 = [5, 'Banana', 8, 130, 44];
let output = array1.find(element => typeof element === 'string');
console.log(output); // 'Banana'
```

```
let isAnimal = {' 🐄 ':true, ' 🌽 ':false, ' 🐔 ':true};
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.find(currentValue => isAnimal[currentValue]);
console.log(output); // ' 🐄 '
```

## FindIndex

|         |                                                                                                                                                                        |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Syntax  | `array.findIndex(callback( element[, index[, array]] )[, thisArg])`                                                                                                    |
| Purpose | Returns the index of the first element in the array that satisfies the provided testing function. Otherwise, it returns -1, indicating that no element passed the test |
| Safe?   | ✅                                                                                                                                                                     |

```
let array1 = [5, 12, 8, 130, 44];
let output = array1.findIndex(element => element > 15);
console.log(output); // 3
```

```
let isAnimal = {' 🐄 ':true, ' 🌽 ':false, ' 🐔 ':true};
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.findIndex(currentValue => isAnimal[currentValue]);
console.log(output); // 0
```

## forEach

|         |                                                                        |
| ------- | ---------------------------------------------------------------------- |
| Syntax  | `array.forEach(callback(currentValue [, index [, array]])[, thisArg])` |
| Purpose | Executes a provided function once for each array element               |
| Safe?   | ✅                                                                     |

```
let array1 = ['a', 'b', 'c'];
let output = array1.forEach(element => console.log(element));
console.log(output); // undefined
```

```
let cooked = [];
let foodFrom = {' 🐄 ': ' 🍔 ', ' 🌽 ': ' 🍿 ', ' 🥔 ': ' 🍟 ', ' 🐔 ': ' 🍗 '};
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.forEach(currentValue => {
  cooked.push(foodFrom[currentValue]);
});
console.log(output); // undefined
console.log(cooked); // [ ' 🍔 ', ' 🍿 ', ' 🍗 ' ]
```

## Includes

|         |                                                                                                                |
| ------- | -------------------------------------------------------------------------------------------------------------- |
| Syntax  | `array.includes(valueToFind[, fromIndex])`                                                                     |
| Purpose | Determines whether an array includes a certain value among its entries, returning true or false as appropriate |
| Safe?   | ✅                                                                                                             |

```
let array1 = ['a', 'b', 'c'];
let output = array1.includes('a');
console.log(output); // true
```

```
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

```
let array1 = ['a', 'b', 'c'];
let output = array1.indexOf('b');
console.log(output); // 1
```

```
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

```
let array1 = ['a', 'b', 'c'];
let output = array1.join('-');
console.log(output); // 'a-b-c'
```

```
let array1 = [' 🐄 ', ' 🍔 ', ' 💩 '];
let output = array1.join(' => ');
console.log(output); // ' 🐄  =>  🍔  =>  💩 '
```

## lastIndexOf

|         |                                                                                                       |
| ------- | ----------------------------------------------------------------------------------------------------- |
| Syntax  | `array.lastIndexOf(searchElement[, fromIndex])`                                                       |
| Purpose | Returns the last index at which a given element can be found in the array, or -1 if it is not present |
| Safe?   | ✅                                                                                                    |

```
let array1 = ['a', 'b', 'c'];
let output = array1.lastIndexOf('c');
console.log(output); // 2
```

```
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
| Safe?   | ✅ ❌                                                                                                               |

```
let array1 = [1, 4, 9, 16];
let output = array1.map(x => Math.sqrt(x));
console.log(output); // [ 1, 2, 3, 4 ]
```

```
let foodFrom = {' 🐄 ': ' 🍔 ', ' 🌽 ': ' 🍿 ', ' 🥔 ': ' 🍟 ', ' 🐔 ': ' 🍗 '};
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.map(currentValue => foodFrom[currentValue]);
console.log(output); // [ ' 🍔 ', ' 🍿 ', ' 🍗 ' ]
```

## pop

|         |                                                                |
| ------- | -------------------------------------------------------------- |
| Syntax  | `array.pop()`                                                  |
| Purpose | Removes the last element from an array, returning that element |
| Safe?   | ❌                                                             |

```
let array1 = ['a', 'b', 'c'];
let output = array1.pop();
console.log(output); // 'c'
```

```
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.pop();
console.log(output); // ' 🐔 '
```

## push

|         |                                                                                       |
| ------- | ------------------------------------------------------------------------------------- |
| Syntax  | `array.push(element1[, ...[, elementN]])`                                             |
| Purpose | Adds one or more elements to the end of an array, returns the new length of the array |
| Safe?   | ❌                                                                                    |

```
let array1 = ['a', 'b', 'c'];
let output = array1.push('d');
console.log(output); // 4
```

```
let array1 = [' 🐄 ', ' 🌽 ', ];
let output = array1.push(' 🐔 ');
console.log(output); // 3
console.log(array1); // [ ' 🐄 ', ' 🌽 ', ' 🐔 ' ]
```

## reduce

|         |                                                                                            |
| ------- | ------------------------------------------------------------------------------------------ |
| Syntax  | `array.reduce(callback( accumulator, currentValue[, index[, array]] )[, initialValue])`    |
| Purpose | Executes a reducer function on each element of the array, resulting in single output value |
| Safe?   | ✅                                                                                         |

```
let array1 = [1, 2, 3, 4];
let output = array1.reduce((accumulator, currentValue) => {
  return accumulator + currentValue;
}, 10);
console.log(output); // 20
```

```
let array1 = [' 💵  ', ' 💶  ', ' 💴  ', ' 💷 ']
let output = array1.reduce((accumulator, currentValue) => ' 💰 ');
console.log(output); // ' 💰 '
```

## reverse

|         |                   |
| ------- | ----------------- |
| Syntax  | `array.reverse()` |
| Purpose | Reverses an array |
| Safe?   | ❌                |

```
let array1 = ['a', 'b', 'c'];
let output = array1.reverse();
console.log('original:', array1); // 'original:' [ 'c', 'b', 'a' ]
console.log('reversed:', output); // 'reversed:' [ 'c', 'b', 'a' ]
```

```
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let array2 = array1.reverse();
console.log('original:', array1); // 'original:' [ ' 🐔 ', ' 🌽 ', ' 🐄 ' ]
console.log('reversed:', array2); // 'reversed:' [ ' 🐔 ', ' 🌽 ', ' 🐄 ' ]
```

## shift

|         |                                                                          |
| ------- | ------------------------------------------------------------------------ |
| Syntax  | `array.shift()`                                                          |
| Purpose | Removes the first element from an array and returns that removed element |
| Safe?   | ❌                                                                       |

```
let array1 = ['a', 'b', 'c'];
let output = array1.shift();
console.log(array1); // [ 'b', 'c' ]
console.log(output); // 'a'
```

```
let array1 = [' 🐄 ', ' 🌽 ', ' 🐔 '];
let output = array1.shift();
console.log(array1); // [ ' 🌽 ', ' 🐔 ' ]
console.log(output); // ' 🐄 '
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```

## XXXXX

|         |         |
| ------- | ------- |
| Syntax  | `XXXXX` |
| Purpose | XXXXXXX |
| Safe?   | ✅ ❌   |

```
XXXXX
```

```
XXXXX
```
