---
layout: post
title: 1.4 Correcting errors
description: Practice with identifying and correcting code blocks
type: ccc
author: Safin Singh and Rohan Juneja
permalink: /basics/js-debug
hide: True
---

{% include nav_basics.html %}

[College Board Big Idea 1](https://apclassroom.collegeboard.org/103/home?unit=1)

## Identifying and Correcting Errors (Unit 1.4)

> Become familiar with types of errors and strategies for fixing them

- Review CollegeBoard videos and take notes on blog
- Complete assigned MCQ questions if applicable

# Code Segments

Practice fixing the following code segments!

## Segment 1: Alphabet List

Intended behavior: create a list of characters from the string contained in the variable `alphabet`

### Code:


```python
%%js

var alphabet = "abcdefghijklmnopqrstuvwxyz";
var alphabetList = [];

for (var i = 0; i < 10; i++) {
	alphabetList.push(alphabet[i]);
}

console.log(alphabetList);

```


    <IPython.core.display.Javascript object>


### What I Changed

I changed "alphabetList.push(i)" to "alphabetList.push(alphabet[i]) which pushed the first 10 lowercase letters of the alphabet string into the alphabetlist array. Before, the console would log numbers 0-9 which are the first 10 numbers. The code did this because the code didn't recognize the alphabet list and rather just took the first 10 variables of the "for var i = 0" part.

## Segment 2: Numbered Alphabet

Intended behavior: print the number of a given alphabet letter within the alphabet. For example:
```
"_" is letter number _ in the alphabet
```

Where the underscores (_) are replaced with the letter and the position of that letter within the alphabet (e.g. a=1, b=2, etc.)

### Code:


```python
%%js

var alphabet = "abcdefghijklmnopqrstuvwxyz";
var alphabetList = [];

for (var i = 0; i < 10; i++) {
	alphabetList.push(alphabet[i]);
}

console.log(alphabetList);
var alphabet = "abcdefghijklmnopqrstuvwxyz";
var alphabetList = [];

for (var i = 0; i < 10; i++) {
	alphabetList.push(alphabet[i]);
}

let letterNumber = 5;

for (var i = 0; i < alphabetList.length; i++) {
	if (i === letterNumber - 1) { // Subtract 1 because the alphabet is 0-based
		console.log(alphabetList[i] + " is letter number " + letterNumber + " in the alphabet");
	}
}

```


    <IPython.core.display.Javascript object>


### What I Changed

I changed the loop from looping through alphabetlist to alphabetlist.length because we want a specific length or for the code to identify a specific part of the string rather than the string itself. I subtracted 1 from "letterNumber" because javascript is 0-based. Therefore, although e is definitely the fifth letter in the alphabet, it's recognized as "4" by javascript. I also used "alphabetlist[i]" to get the letter at the current index, which allows the code to pinpoint the 4 or as we know it the fifth number in the alphabet being e.

## Segment 3: Odd Numbers

Intended behavior: print a list of all the odd numbers below 10

### Code:


```python
%%js

let odds = [];
let i = 1;

while (i <= 10) {
  odds.push(i);
  i += 2;
}

console.log(odds);
```


    <IPython.core.display.Javascript object>


### What I Changed

I changed the "evens" in the code to odds, and I let i = 1 instead of 0 because 1 is the first odd number. 

# BELOW NOT EDITED

The intended outcome is printing a number between 1 and 100 once, if it is a multiple of 2 or 5 
- What values are outputted incorrectly. Why? Many of the numbers are being duplicated. To fixx this, change the "push" to "add"s and use a Set to store unique numbers. This ensures that the code will not print a duplicate number if a number that has already been printed appears again.

- Make changes to get the intended outcome.


```python
%%js

var numbers = [];
var newNumbers = new Set(); // Use a Set to store unique numbers
var i = 0;

while (i < 100) {
    numbers.push(i);
    i += 1;
}

for (var i of numbers) {
    if (numbers[i] % 5 === 0)
        newNumbers.add(numbers[i]);
    if (numbers[i] % 2 === 0)
        newNumbers.add(numbers[i]);
}

// Convert the Set back to an array
var uniqueNumbers = Array.from(newNumbers);

console.log(uniqueNumbers);

```


    <IPython.core.display.Javascript object>


# Challenge

This code segment is at a very early stage of implementation.
- What are some ways to (user) error proof this code?
- The code should be able to calculate the cost of the meal of the user

Hint:
- write a “single” test describing an expectation of the program of the program
- test - input burger, expect output of burger price
- run the test, which should fail because the program lacks that feature
- write “just enough” code, the simplest possible, to make the test pass

Then repeat this process until you get program working like you want it to work.


```python
%%js

var menu =  {"burger": 3.99,
         "fries": 1.99,
         "drink": 0.99}
var total = 0

//shows the user the menu and prompts them to select an item
console.log("Menu")
for (var item in menu) {
    console.log(item + "  $" + menu[item].toFixed(2)) //why is toFixed used?
}
//ideally the code should support mutliple items
var item = "burger"

//code should add the price  of yes
console.log(total)
```

## Hacks
- Fix the errors in the first three segments in this notebook and say what you changed in the code cell under "What I Changed" (Challenge is optional)
