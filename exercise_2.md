## Mia's Music Store

Mia runs a world music store with a simple inventory system to track the current numbers and prices of each model in her stock. The code she is using to change her inventory is rather unreadable and unnecessarily  long. Let's see if we can use some array methods to help clean up the code.

### Instructions
___
#### 1. Take some time to understand the code by calling the functions with different parameters, then hit next when you are ready to move on.

**Code:**
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
                 {"instrument":"Guitar", "model":"Pro", "price":620, "count":1}];

//Print an inventory
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

//Get the total value of the inventory
function totalValue(){
	var totalVal = 0;
	for(var i = 0; i < inventory.length; i++){
			totalVal += inventory[i].count * inventory[i].price
	}
	return totalVal
}

printInventory(inventory);
printInventory(needToOrder());
sale(20);
printInventory(inventory);
console.log(totalValue());
```