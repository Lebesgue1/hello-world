## Some Common Array Methods

### .forEach()
As we have just seen, the `forEach()` method is another way of iterating through an array. It takes a callback function as an argument and calls the function on each element of the array. 

```javascript
var array1 = ['a', 'b', 'c'];
array1.forEach(function(element) {
  console.log(element);
});
```

### .filter()
 
We use the `filter()` method to find the elements of an array that satisfy a certain condition. The `filter()` method accepts a callback function as a parameter that return a truthy value as an argument and returns a new array of elements that return true. For example if you wanted to find the elements of an array with a length of greater than 5 you could use `filter()`.

```javascript
var words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(function(word){ return word.length > 5});

console.log(result);
```

### .map()
 
The `map()` method creates a new array with the results of calling a provided function on every element in the calling array. For example, you could use `map()` to square each element in an array of numbers.
 
```javascript
var array1 = [1, 2, 3, 4];

// pass a function to map
const map1 = array1.map(function(x){return x ** 2});

console.log(map1);
```

### .reduce()
 
According to the documentation, the `reduce()` method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value.

This one is a bit trickier than the other methods we've seen so far, so let's take a look at an example to see exactly what this means.

```javascript
const array1 = [1, 3, 5, 7];
const reducer = function(prev, next) {
    return prev + next;
}

// 1 + 3 + 5 + 7
console.log(array1.reduce(reducer));
// expected output: 16

// 5 + 1 + 3 + 5 + 7
console.log(array1.reduce(reducer, 5));
// expected output: 21
```
The `reduce()` method takes two parameters, a callback function (in this case `reducer()`) and an initial value. The callback function takes the parameters `prev` and `next` and returns their sum. In the first example there is no initial value set so `prev` will initially refer to the first element of the array, `1`, and `next` will refer to the second element of the array, `3`. These two elements get added together to make `4`, which is passed to `prev` in the next iteration. `next` will then refer to the next element of the array, `5`. These two elements then get added together to make `9`, which is passed to `prev` in the next iteration and so on. When there is an initial value set, `prev` will initially refer to the initial value, and `next` will initially refer to the first element of the array.

### Instructions
___
#### 1. Use the `forEach()` method to rewrite the for loop inside of the function `printInventory()`.

**Inital Code Snippet:**

```javascript
//Print an entire inventory
function printInventory(inv){
	for(var i = 0; i < inv.length; i++){
		console.log("Instrument: " + inv[i].model + " " + inv[i].instrument + 
                    ", Count: " + inv[i].count + 
                    ", Price: " + inv[i].price)
	}
}
```
**Completed Code Snippet:**

```javascript
//Print an entire inventory
function printInventory(inv){
	inv.forEach(function(item){
		console.log("Instrument: " + item.model + " " + item.instrument + 
                    ", Count: " + item.count + 
                    ", Price: " + item.price)
		})
}
```
___
#### 2. Use the `filter()` method to rewrite the `needToOrder()` function.
 
**Inital Code Snippet:**

```javascript
//List each instrument with less than two in stock so they can be ordered
function needToOrder(){
	var order = []
	for(var i = 0; i < inventory.length; i++){
		if(inventory[i].count < 2){
			order.push(inventory[i])
		}
	}
	return order
}
```
**Completed Code Snippet:**

```javascript
//List each instrument with less than two in stock so they can be ordered
function needToOrder(){
	return inventory.filter(function(item){
		return item.count < 2
	})
}
```
___

#### 3. Use the `map()` method to rewrite the `sale()` function.

**Initial Code Snippet:**

```javascript
//Have a sale and reduce the price of each item by percentOff percent.
function sale(percentOff){
	for(i = 0; i < inventory.length; i++){
		inventory[i].price *= (1 - percentOff / 100)
	}
}
```

**Completed Code Snippet:**

```javascript
//Have a sale and reduce the price of each item by percentOff percent.
function sale(percentOff){
	inventory.map(function(item){item.price *= (1 - percentOff / 100)})
}
```
___
#### 4. Use the `reduce()` method to rewrite the `totalValue()` function.

**Initial Code Snippet:**

```javascript
//Get the total value of all the instruments in the store
function totalValue(){
	var totalVal = 0;
	for(var i = 0; i < inventory.length; i++){
			totalVal += inventory[i].count * inventory[i].price
	}
	return totalVal
}
```

**Completed Code Snippet:**

```javascript
//Get the total value of all the instruments in the store
function totalValue(){
	return inventory.reduce(function(prev, next){prev + next.price * next.count}, 0)
}
```
___
#### 5. Great Work! Press 'next' when you are ready to continue.
**Full Initial Code:**

```javascript
var inventory = [{"instrument":"Oud", "model":"Amateur", "price":180, "count":6},
                 {"instrument":"Oud", "model":"Pro", "price":540, "count":1}, 
                 {"instrument":"Banjo", "model":"Amateur", "price":220, "count":3}, 
                 {"instrument":"Banjo", "model":"Pro", "price":850, "count":0}, 
                 {"instrument":"Accordian", "model":"Amateur", "price":280, "count":4}, 
                 {"instrument":"Accordian", "model":"Pro", "price":680, "count":4},
                 {"instrument":"Sitar", "model":"Amateur", "price":350, "count":1}, 
                 {"instrument":"Sitar", "model":"Pro", "price":1260, "count":1},
                 {"instrument":"Guitar", "model":"Amateur", "price":240, "count":0},
                 {"instrument":"Guitar", "model":"Pro", "price":620, "count":1}]

//Print the entire inventory
function printInventory(inv){
	for(var i = 0; i < inv.length; i++){
		console.log("Instrument: " + inv[i].model + " " + inv[i].instrument + 
                    ", Count: " + inv[i].count + 
                    ", Price: " + inv[i].price)
	}
}

//List each instrument with less than two in stock so they can be ordered
function needToOrder(){
	var order = []
	for(var i = 0; i < inventory.length; i++){
		if(inventory[i].count < 2){
			order.push(inventory[i])
		}
	}
	return order
}

//Have a sale and reduce the price of each item by percentOff percent.
function sale(percentOff){
	for(i = 0; i < inventory.length; i++){
		inventory[i].price *= (1 - percentOff / 100)
	}
}

//Get a count of each instrument type
function totalValue(){
	var totalVal = 0;
	for(var i = 0; i < inventory.length; i++){
			totalVal += inventory[i].count * inventory[i].price
	}
	return totalVal
}

printInventory(inventory)
printInventory(needToOrder())
sale(20)
printInventory(inventory)
console.log(totalValue())
```

**Full Completed Code:**

```javascript
var inventory = [{"instrument":"Oud", "model":"Amateur", "price":180, "count":6},
                 {"instrument":"Oud", "model":"Pro", "price":540, "count":1}, 
                 {"instrument":"Banjo", "model":"Amateur", "price":220, "count":3}, 
                 {"instrument":"Banjo", "model":"Pro", "price":850, "count":0}, 
                 {"instrument":"Accordian", "model":"Amateur", "price":280, "count":4}, 
                 {"instrument":"Accordian", "model":"Pro", "price":680, "count":4},
                 {"instrument":"Sitar", "model":"Amateur", "price":350, "count":1}, 
                 {"instrument":"Sitar", "model":"Pro", "price":1260, "count":1},
                 {"instrument":"Guitar", "model":"Amateur", "price":240, "count":0},
                 {"instrument":"Guitar", "model":"Pro", "price":620, "count":1}]

//Print the entire inventory
function printInventory(inv){
	inv.forEach(function(item){
		console.log("Instrument: " + item.model + " " + item.instrument + 
                    ", Count: " + item.count + 
                    ", Price: " + item.price)
		})
}

//List each instrument with less than two in stock so they can be ordered
function needToOrder(){
	return inventory.filter(function(item){
		return item.count < 2
	})
}

//Have a sale and reduce the price of each item by percentOff percent.
function sale(percentOff){
	inventory.map(function(item){
	                item.price *= (1 - percentOff / 100)
	             });
}

//Get a count of each instrument type
function totalValue(){
	return inventory.reduce(function(prev, next){return (prev + next.price * next.count);}, 0);
}

printInventory(inventory)
printInventory(needToOrder())
sale(20)
printInventory(inventory)
console.log(totalValue())
```