---
title: Basics of Javascript
hide: True
description: A Tech Talk on how to use javascript
type: ccc
permalink: /basics/javascript
author: Rohan Juneja
---

{% include nav_basics.html %}


# How to use javascript in any of your pages
- Simply add a ``<script></script>`` in your markdown or html files, like so:
- (Note: the %%html allows us to add HTML in a jupyter notebook, the outputted "site" will be shown below the code)


```python
%%html
<p>This is a page</p>
<script>
    console.log("our code is running!")
</script>

```


<p>This is a page</p>
<script>
    console.log("our code is running!");
</script>



# Writing text (see above example)
- `console.log` allows you to write text -- but you don't see any text above!
- The text written with `console.log` appears in the console -- access this by right click -> inspect element (try it on this blog!)
    - Safari users will need to enable developer settings before inspecting an element. To do this go to Safari settings -> advanced and check the box next to "Show develop menu in menu bar"
- This text must be wrapped in quotes (explained below)

# Trying everything out
- Keep your inspect element console open, you can run javascript code in here!
- Try to test out everything that is explained in this lesson

# Storing data
- one of the most important things in programming is how data is stored
- Think about what data you know: your name, age, whether today is a school day, etc.
  - All of this data can be stored inside javascript


# Types of data
- Javascript has a few basic types of data, which align with what the types of data you might know yourself
- For instance: your name = text, your age = a number, whether today is a school day = true/false
- In javascript, these types are formalized as:
  - text = "string", number = "number", true/false = "boolean"

# Labeling data
- When you think of something you know, it has a name, and a value:
  - For instance "your age" would be the name and 18 would be the value
- In javascript this can represented with the following: `var someName = value;`
  - The name cannot have spaces
  - Text values must be wrapped in single or double quotes to identify it as text (see exmaples below)
- Using the "var" syntax is called creating a `variable`


```python
%%html
<script>
var firstName = "Rohan"
var lastName = 'Juneja'
var age = 17;
var isSchoolDay = true; 
</script>
```


<script>
var firstName = "Rohan"
var lastName = 'Juneja'
var age = 17;
var isSchoolDay = true; 
</script>



# Accessing data
- To access data (the value of a variable), simply just use the name of the variable
- For example, we can use the values from previously in a `console.log`


```python
%%html
<script>
var firstName = "Rohan"
var lastName = 'Juneja'
var age = 17;
var isSchoolDay = true; 

// using the value of the variable
console.log(firstName)
</script>
```


<script>
var firstName = "Rohan"
var lastName = 'Juneja'
var age = 17;
var isSchoolDay = true; 

console.log(firstName)
</script>



# Operators
- "+" adds numbers together, or combines text together
- "-" subtracts numbers, "/" divides numbers, "*" multiples numbers
- "===" checks if two values are the same, if so it outputs `true`, otherwise `false`
  - "!==" is "not equal to" (opposite of equal to)
  - normal oeprators like "<", ">", ">=" (greater than or equal to), "<=" with numbers

# Assignment Operator
- "=" can be used to change the value of a variable
  - ie. if you already created "name1" you can do name1 = "New Name"


```python
%%html
<script>
var name1 = "Name"
var name2 = "Name"

console.log("Operators")
console.log("Messing with names")
console.log(name1 == name2)

// changing the value of name1
name1 = "New Name"

console.log(name1 + name2)

var age1 = 17
var age2 = 16
console.log("Age1 vs Age2 comparisons")
console.log(age1 == age2)
console.log(age2 > age1)
console.log(age2 < age1)

var age3 = age1 * age2
console.log("Two ages multipled")
console.log(age3)
</script>
```


<script>
var name1 = "Name"
var name2 = "Name"

console.log("Operators")
console.log("Messing with names")
console.log(name1 == name2)

// changing the value of name1
name1 = "New Name"

console.log(name1 + name2)

var age1 = 17
var age2 = 16
console.log("Age1 vs Age2 comparisons")
console.log(age1 == age2)
console.log(age2 > age1)
console.log(age2 < age1)

var age3 = age1 * age2
console.log("Two ages multipled")
console.log(age3)
</script>



# Conditional Statements
- Think about any actions that you take: you usually take them based on information you take in
  - If tommorow is a school day, set an alarm for tomorrow at 8am
- We can also add additional clauses at the end
  - If tommorow is a school day, set an alarm for tomorrow at 8am, otherwise (else) set an alarm for tommorow at 10am


```python
%%html
<script>
// the above example in code
console.log("Alarm Example")

var tommorowIsSchoolDay = false

if (tommorowIsSchoolDay) {
    // this code runs if tommorw is a school day
    console.log("Setting alarm for 8am")
} else {
    // this code runs if tommorow is not a school day
    console.log("Setting alarm for 10am")
}
</script>
```


<script>
// the above example in code
console.log("Alarm Example")

var tommorowIsSchoolDay = false

if (tommorowIsSchoolDay) {
    console.log("Setting alarm for 8am")
} else {
    console.log("Setting alarm for 10am")
}
</script>



# Conditional Statements + Operators
- Since many operators return a true/false value (equals, gerater than, etc.) we can use them inside "if" statements


```python
%%html
<script>
console.log("If statements + Operators")
var age1 = 16
var age2 = 17

if (age1 > age2) {
    // runs if age1 is more than age2
    console.log("age1 is more than age2")
}

if (age1 === age2) {
    // runs if age1 and age2 are the same
    console.log("age1 is the same as age2")
}

if (age1 < age2) {
    // runs if age2 is more than age1
    console.log("age1 is less than age2")
}
</script>
```


<script>
console.log("If statements + Operators")
var age1 = 16
var age2 = 17

if (age1 > age2) {
    // runs if age1 is more than age2
    console.log("age1 is more than age2")
}

if (age1 === age2) {
    // runs if age1 and age2 are the same
    console.log("age1 is the same as age2")
}

if (age1 < age2) {
    // runs if age2 is more than age1
    console.log("age1 is less than age2")
}
</script>



## My Display of Basics of Javascript: learning, editing, testing

> The basic idea of the code was to simply compare variables a and b, and print whichever number was greater or lesser or equal. I integrated this basic code into our team's passion being Geoguessr Themed, by having the population numbers of two countries be variables a and b, and running the code would tell you which country has a greater population. 

>For testing: Japan's population is about 125000000. South Korea's population is about 51000000.


```python
%%js
// put your javascript code here
var a = 51000000;
var b = 125000000;

if (a > b) {
  console.log("Variable A is Japan's population, which is larger than Variable B which is South Korea's population.");
} else if (a < b) {
  console.log("Variable A is South Korea's population, which is less than Variable B which is Japan's population.");
} else {
  console.log("The Variables are equal, so both variable A and B must be both Japan or South Korea's populatin.");
}

```


    <IPython.core.display.Javascript object>


## This is a more optimized version of the code above for the specific populations of Japan or South Korea. The code will prompt you to enter the proper populations in.


```python
%%js
// put your javascript code here
var a = 51000000;
var b = 125000000;

if (a === 51000000 && b === 125000000) {
  console.log("Variable A is Japan's population, which is larger than Variable B, which is South Korea's population.");
} else if (a === 125000000 && b === 51000000) {
  console.log("Variable A is South Korea's population, which is less than Variable B, which is Japan's population.");
} else {
  console.log("These aren't the populations goofy");
}

```


    <IPython.core.display.Javascript object>

