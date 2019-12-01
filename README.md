# Functional Programming Code Snippets
Code Snippets for Functional Programming in JS

* Keeps functions & data separate
* Avoids state change & mutable data
* Treats functions as first-class citizens


# Code Snippets


## Assigning function to a variable
```json

var num = increement(10); //Here number will be 11 bcz compiler shifts func automatically on the top

function increment(val){ 
  return val += 1;
}

var func_inc = increement //This means num is now a function but it should be delared after function only

```

## Passing Functions as an argument


```json
const x = 1

function doIf(condition, func){
  if(condition){
    func();
  }
}

doIf(x === 1,sayXis1);
doIf(x === "Bananas",sayXisBananas);
doIf(x < 10 && x > 0,sayXisBetween0And10);


function sayXis1() { console.log("x is equal to 1") }

function sayXisBananas() { console.log("x is equal to 'Bananas'") }

function sayXisBetween0And10() { console.log("x is between 0 and 10") }

```

## Closures & Returning Functions
```json
function increment_val(count){
  return {
    current : function(){
      return count;
    },
    increment : function () {
        return count += 1;
    }
  };
}

var incValue = increment_val(5);

console.log(incValue.current());
```

## High Order Functions
```json
function doIfSafe(func) {
  return function(n,message)
    {
      if (n != null && typeof n === 'number') {
        if (message != null && typeof message === 'string') {
          return func(n, message)
        }
      }
    }
}

function printMessageNTimes(n, message) {
  for (var i = 0; i < n; i++) { console.log(message) }
}

var printmessagesafe =   doIfSafe(printMessageNTimes) // prints "Banana Banana Banana Banana"
printmessagesafe(4, "Banana");
```

## Maps(Lodash)
Maps doesn't return the original array. We have to assign the result into something.
```json
var _ = require("lodash");

var numbers = [ 1, 2, 3, 4, 5 ]
var numbersSquare = _.map(numbers,function(number){
    return number * number;
});

console.log(numbersSquare);
```

## Filter(Lodash)
```json
var _ = require("lodash");

var employees = [
  { name: "John",  salary: 50000  },
  { name: "Susan", salary: 60000  },
  { name: "Greg",  salary: 100000 },
  { name: "Mary",  salary: 120000 }
]

var dueForARaise = _.filter(employees, function (employee) {
    if(employee.salary < 100000){
      return true
    }
});

console.log(dueForARaise);
```

## Some & Every
```json
var _ = require("lodash");

var numbers = [ 2, 3, 6, 8, 10, 12 ]

var arrayContainsEven =  _.some(numbers, function(number){
  return number%2 === 0;
});

var arrayIsAllEven = _.every(numbers, function(number){
  return number%2 === 0;
});

console.log("arrayContainsEven - ", arrayContainsEven); //Should return true bcz some of the values are even
console.log("arrayIsAllEven - ", arrayIsAllEven); //Should return false bcz some of the values are odd
```

## Reduce
```json
var _ = require("lodash");

var shoppingList = [
  { name: "Eggs",    price: 4.99 },
  { name: "Milk",    price: 3.99 },
];


var totalval  = _.reduce(shoppingList,function (val,item) {
    return val += item.price;
},0);

console.log(totalval);
```


## Learnings
* Compilers move function automatically on the top when declared in file


## Basic Prerequisites
* node
* npm
* Lodash


## Learning Reference
* [Linkedin Course on Functional Programming JS](https://www.linkedin.com/learning/learning-functional-programming-with-javascript/)
