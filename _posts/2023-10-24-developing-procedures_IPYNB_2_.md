---
layout: post
title: Developing Procedures
description: College Board 3.12 and 3.13
toc: True
comments: True
type: hacks
courses: {'csp': {'week': 9}}
---

## What is a procedure?
A procedure is a named group of programming instructions with a purpose and is called to perform a task based on the commands. 


It is extremely important to name the procedure something that describes the purpose, method, or function because it makes it easier for others to read your code and for yourself when you revisit old code. Additionally, when there is an effefctively named procedure, it is much simpler to correct bugs and errors.

### Which code is better?
<img src="https://media.discordapp.net//attachments/909575347773775953/1166199627083698217/namingprocedures.png?ex=65499f0a&is=65372a0a&hm=6a7d0bf546b51e54837e3cd8d5993063d9ab28ac4f19bd6e49b6a540424a30a5&">

### Hack 1: Naming Procedures
Rename the procedure below with a name that better describes the purpose of the procedure. 

The procedure is currently just called "procedure." It compares the current grade with the existing quiz grade and replaces the original score if the current is higher.


```python
def quizgradecalculator(quiz_grade, current_points, total_points):
    # calculate current grade
    current_grade = (current_points / total_points) * 100

    if current_grade > quiz_grade:
        quiz_grade = current_grade

    return quiz_grade

quiz_grade = 85  # Initial quiz grade
current_points = 90  # Current points earned
total_points = 100  # Total points for the quiz

new_quiz_grade = quizgradecalculator(quiz_grade, current_points, total_points)

print(f"Old quiz grade: {quiz_grade}")
print(f"New quiz grade: {new_quiz_grade}")

```

    Old quiz grade: 85
    New quiz grade: 90.0


## Function Parameters
A function can have one or more parameters that can be passed into the function as local variables to use in the procedural function. The variables that can be passed in the function are called parameters. The data passed in when the function is called are called arguments.


Parameters: input values of a procedure


Arguments: specify the parameter values when a procedure is called


```python
def triangle_area(length, width): # parameters passed in two variables: length and width, returns area
    area = 1/2 * length * width # calculates area from the length and width
    print("length:", length)
    print("width:", width)
    return area # returns area

# examples
print(triangle_area(3, 4)) # the arguments here are 3 and 4, which becomes the parameters length and width respectively
print(triangle_area(6, 8))
print(triangle_area(12, 89))
```

    length: 3
    width: 4
    6.0
    length: 6
    width: 8
    24.0
    length: 12
    width: 89
    534.0


## Procedure Algorithm / How Procedures Work
Remember that procedures are essentially a set of programming instructions, or lines of code, that accomplish a goal. When executed, each line of code is executed in order (step after step after step) to get to the goal.

### Regular code/Python


```python
# Procedure called "applyTax" that applies a percent tax to a price
def applyTax(price, percentTax): # When writing a procedure, first decide what parameters you will need to accomplish your goal
    # Step 1: Calculate the amount taxed
    taxAmount = price * percentTax/100

    # Step 2: Add the amount taxed to the price to get the end amount
    endAmount = price + taxAmount

    return endAmount

# Use procedure to apply a 50% tax to a price of $10
cost = applyTax(10, 50)
print(cost)
```

    15.0


### CollegeBoard Pseudo-Code
- Note that the pseudo-code below has the exact same purpose as the actual code above. Ignore the breaks and spaces since they are used for formatting.
> Differences between prseudo-code and Python:
- Pseudo-code uses "PROCEDURE" instead of "def"
- Pseudo-code uses "<--" instead of "="
- Pseudo-code uses "{}" instead of ":" to mark where a procedure starts and ends
<br>

> Pseudo-code example <br>

PROCEDURE applyTax (price, percentTax) <br>
{ <br>
&nbsp;&nbsp;&nbsp;&nbsp;taxAmount <-- price * percentTax/100 <br>
&nbsp;&nbsp;&nbsp;&nbsp;endAmount <-- price + taxAmount <br>
&nbsp;&nbsp;&nbsp;&nbsp;return endAmount <br>
}

### Hack 2: Robot Pseudo-Code
<img src="https://media.discordapp.net/attachments/1143438030749847604/1165903186473783317/image.png?ex=65488af5&is=653615f5&hm=349a4cfef60546b6f85e59a2448ac85ed4fd0181d63f70456904909e46401d74&=">

> Instructions:
- The blue triangle represents a robot that moves in a grid of squares. The tip of the triangle indicates where the robot is facing.
- Write a procedure that allows the robot to make a detour around a block by moving to the left.

> Commands
- MOVE_FORWARD() - Moves the robot forward one square
- MOVE_BACKWARD() - Moves the robot backward one square
- ROTATE_LEFT() - Rotates the robot 90 degrees left
- ROTATE_RIGHT() - Rotates the robot 90 degrees right

> Your code here:

PROCEDURE robotmove()
{
    ROTATE_LEFT()
    MOVE_FORWARD()
    ROTATE_RIGHT()
    MOVE_FORWARD()
    ROTATE_RIGHT()
    MOVE_FORWARD()
}

## Procedure Return Values
When a procedure is run, it executes a series of calculations or commands and at some point and needs to provide a useful result. The return statement is what allows us to return a useful value back to the calling code. The returns statement can return various types of values such as booleans, integers, strings, etc.

## Procedure Calls
Calling: This involves specifying the function name followed by parentheses, and passing any required arguments inside the parentheses.


When a function is called, the program control jumps to the function definition, and the statements inside the function are executed.
After the function completes its task, the control returns to the point where the function was called.

### Hack 3: Create and Call a Procedure
Define a function named calculate_grade that takes a student's score as a parameter and returns 'Pass' if the score is 50 or more, and 'Fail' otherwise.


```python
# your code here
def calculate_grade(score):
    if (score <= 50):
        print("you suck")
    if (score > 50):
        print("yippe");

score = calculate_grade(56)

    
```

    yippe


# Homework
## Instructions
There are two total problems:
1.  An easy regular code (Python) problem
2.  A medium pseudo-code problem
3. A hard regular code (Python) problem


Completing question 1 and 2 gets you 0.9/1 if you do it correctly. Completing/attempting question 3, adding creativity, and adding good comments will potentially raise you above 0.9.

### Question 1
Write a procedure to apply a percent discount to a set price. See the example about applying tax if you're stuck.


```python
# your code here
def taxing(taxamount, totalprice):

    taxamount = totalprice * .02 

    return taxamount

cost = taxing(10, 50) + 50
print(cost)

    
```

    51.0


### Question 2
Create your own robot problem! Include a picture with a square grid to represent the map and triangle to represent the robot. Add a flag to a square to represent the end-point and a shaded-in block to represent a detour. Write a procedure in pseudo-code to move the robot from the start, past the detour, and to the end point.

Add your image here by adding the link between the "" and removing the comment formatting:
<!-- <img src=""> -->

# your code here
<img src="https://cdn.discordapp.com/attachments/1081856159855677464/1171001709187842099/zIwfXAAAAAElFTkSuQmCC.png?ex=655b1753&is=6548a253&hm=9b836df7809fa28808fcc993c7cfbce07ec656cbbab4517810b9260c255c2bea&">

# MOVE_FORWARD() - Moves the robot forward one square
# MOVE_BACKWARD() - Moves the robot backward one square
# ROTATE_LEFT() - Rotates the robot 90 degrees left
# ROTATE_RIGHT() - Rotates the robot 90 degrees right

# Objective is to get the robot to the gray box

PROCEDURE graybox
{
    MOVE_FORWARD()
    MOVE_FORWARD()
    ROTATE_RIGHT()
    MOVE_FORWARD()
    MOVE_FORWARD()
    MOVE_FORWARD()
    MOVE_FORWARD()
    ROTATE_LEFT()
    MOVE_FORWARD()
    MOVE_FORWARD()
}

#yippe

### Question 3
Create a program that asks for user input of an integer *n*, and return an array that contains all the prime numbers up to the number *n* (inclusive). Remember to use multiple different functions to better organize the code and increase efficiency.


```python
def primes(n):
  # your code here
    # An empty list to store prime numbers
    primelist = []

    # Iterates through numbers from 2 to n (inclusive) because 2 is the first prime number
    for i in range(2, n+1):
        # Assumes the number is prime until proven otherwise
        is_prime = True

        # Check for factors from 2 to the square root of i
        for i2 in range(2, int(i**0.5) + 1):
            # If i is divisible by i2, it is not a prime number
            if i % i2 == 0:
                is_prime = False # If the number is not prime, change is_prime to false
                break  # Exit the loop if a factor is found

        # If no factors were found, i is a prime number
        if is_prime: #so if is_prime is still true, that means that the number is prime
            # adding the prime number to the list
            primelist.append(i)

    # Return the list of prime numbers up to n
    return primelist



# tests
print(primes(5))
print(primes(12))
print(primes(35))


```

    [2, 3, 5]
    [2, 3, 5, 7, 11]
    [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31]

