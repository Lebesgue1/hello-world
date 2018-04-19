# Array Methods
______
## Introduction to Array Methods

As you have seen in previous lessons, there are many ways to iterate through an array in JavaScript. One that most beginning programmers learn first is the `for` loop.

```javascript
for (var i = 0; i < numberArray.length; i++) {
	console.log(numberArray[i]);
}
```

The previous code will iterate through an array of numbers and print out each number in the array. However, as of ES5 (now supported by roughly 98% of browsers), JavaScript supplies a number of built-in methods for array iteration. One such method is `forEach()`.

```javascript
numberArray.forEach(function(number) {
	console.log(number);
});
```

This code executes the same as the for loop but has been rewritten using the built-in `forEach()` method. The `forEach()` method takes a callback function as a parameter which will be called on each element of the array.

There are a number of other built-in array methods. In this lesson we will take a look at several commonly used array methods but a complete list of methods can be found at https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/. It is important for learners to be able to both identify the use cases of the most important iteration methods as well as be able to find new ones using documentation.

There are many benefits to using array methods, some of which are listed below.

- **More readable**: The choice of built-in method clearly demonstrates the intended purpose of the loop, in the case of `forEach()` we want to iterate through an array without creating a new one.
- **Less boilerplate**: Writing `for` loops is unnecessarily monotonous and obfuscates the intention of the code.
- **Less room for error**: Using a built-in method ensures the loop will occur as intended, whereas a `for` loop is prone to typos.
- **Less scope pollution**: Each `for` loop (using `var`) will declare a variable for its loop; this variable enters the function's scope, adding unnecessary values and potentially overwriting existing variable values.

### Instructions
___
#### 1. Add an array of numbers to the code and press run to see that the two methods produce the same output. Then press next when you are ready to continue.
 
**Initial Code:**
```javascript
//Add an array of numbers here

for (var i = 0; i < numberArray.length; i++) {
	console.log("Result using a \"for\" loop: "numberArray[i]);
}

numberArray.forEach(function(number) {
	console.log("Result using the .forEach method: " + number);
});
```
 
**Completed Code:**
```javascript
//Add an array of numbers here
var numberArray = [1, 1, 2, 3, 5, 8, 13, 21, 34]

for (var i = 0; i < numberArray.length; i++) {
	console.log("Result using a \"for\" loop: "numberArray[i]);
}

numberArray.forEach(function(number) {
	console.log("Result using the .forEach method: " + number);
});
```