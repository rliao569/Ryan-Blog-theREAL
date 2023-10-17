---
toc: True
comments: True
layout: post
title: BOOLEAN IF
type: hacks
courses: {'csp': {'week': 8}}
---

# Boolean

- A Boolean value is either true or false.
- A Boolean expression produces a Boolean value (true or false) when evaluated.

## <mark>Conditional ("if") statements</mark>

- Affect the sequential flow of control by executing different statements based on the value of a Boolean expression.


```python
IF (condition)
{
	<block of statements>
}

The code in <block of statements> is executed if the Boolean expression condition evaluates to true; no action is taken if condition evaluates to false.

IF (condition)
{
	<block of statements>
}
ELSE
{
	<second block of statements>
}

The code in the first <block of statements> is executed if the Boolean expression condition evaluates to true; otherwise, the code in <second block of statements> is executed.
```

<b>Example:</b> Calculate the sum of 2 numbers. If the sum is greater than 10, display 10; otherwise, display the sum.


```python
num1 = INPUT
num2 = INPUT
sum = num1 + num2
IF (sum > 10)
{
	DISPLAY (10)
}
ELSE
{
	DISPLAY (sum)
}
```

# Hack 1

- Add a variable that represents an age.

- Add an 'if' and 'print' function that says "You are an adult" if your age is greater than or equal to 18.

- Make a function that prints "You are a minor" with the else function.


```python
## YOUR CODE HERE

age = 18

if age >= 18:
    print("you are an adult")
else:
    print("you are a minor")
```

## <mark><b>Relational operators:</b></mark> 
- Used to test the relationship between 2 variables, expressions, or values. These relational operators are used for comparisons and they evaluate to a Boolean value (true or false).

<b>Ex.</b> a == b evaluates to true if a and b are equal, otherwise evaluates to false

- a == b (equals)	
- a != b (not equal to)
- a > b (greater than)
- a < b (less than)
- a >= b (greater than or equal to)
- a <= b (less than or equal to)

<b>Example:</b> The legal age to work in California is 14 years old. How would we write a Boolean expression to check if someone is at least 14 years old?

age >= 14

<b>Example:</b> Write a Boolean expression to check if the average of height1, height2, and height3 is at least 65 inches.

(height1 + height2 + height3) / 3 >= 65

# Hack 2

- Make a variable called 'is_raining' and set it to 'True".

- Make an if statement that prints "Bring an umbrella!" if it is true

- Make an else statement that says "The weather is clear".


```python
## YOUR CODE HERE

is_raining=True

if is_raining is True:
    print ("Bring an Umbrella!")
else:
    print ("It is not raining")

```

## <mark><b>Logical operators:</b></mark>
Used to evaluate multiple conditions to produce a single Boolean value.

- <b>NOT</b>	evaluates to true if condition is false, otherwise evaluates to false
- <b>AND</b>	evaluates to true if both conditions are true, otherwise evaluates to false
- <b>OR</b>	evaluates to true if either condition is true or if both conditions are true, otherwise evaluates to false

<b>Example:</b> You win the game if you score at least 10 points and have 5 lives left or if you score at least 50 points and have more than 0 lives left. Write the Boolean expression for this scenario.

(score >= 10 AND lives == 5) OR (score == 50 AND lives > 0)

## <mark><b>Relational and logical operators:</b></mark>

<b>Example:</b> These expressions are all different but will produce the same result.

- age >= 16
- age > 16 OR age == 16
- NOT age < 16

# Hack 3

- Make a function to randomize numbers between 0 and 100 to be assigned to variables a and b using random.randint

- Print the values of the variables

- Print the relationship of the variables; a is more than, same as, or less than b


```python
## YOUR CODE HERE

import random 

a = random.randint[0, 100]
b = random.randint[0, 100]
print[a]
print[b]

if a>b:
    print("a is greater than b")
else:
    print ("b is greater than a")


```

## <b>Homework</b>

### Criteria for above 90%:
- Add more questions relating to Boolean rather than only one per topic (ideas: expand on conditional statements, relational/logical operators)
- Add a way to organize the user scores (possibly some kind of leaderboard, keep track of high score vs. current score, etc. Get creative!)
- Remember to test your code to make sure it functions correctly.


```python
#HOMEWORK


# The quiz contains questions related to Boolean values, Boolean expressions,
# conditional statements, relational operators, and logical operators.

# Import necessary modules
import getpass  # Module to get the user's name
import sys  # Module to access system-related information

# Function to ask a question and get a response
def question_with_response(prompt):
    # Print the question
    print("Question: " + prompt)
    # Get user input as the response
    msg = input()
    return msg

# Define the number of questions and initialize the correct answers counter
questions = 9
correct = 0

# Personalized greeting message
# Collect the student's name
user_name = input("Enter your name: ")
print('Hello, ' + user_name + " running " + sys.executable)
print("You will be asked " + str(questions) + " questions.")
answer = input("Are you ready to take a test?")

# Question 1: Boolean Basics 
# Ask a question about Boolean values and check the response
# Provide feedback based on the correctness of the response
def ask_boolean_question1():
    global correct

    response = input("Do Boolean values represent a truth value? (Enter 'True' or 'False'): ")
    print(response)
    if response.lower() == 'true':
        print("Correct!")
        correct += 1
    elif response.lower() == 'false':
        print("Incorrect.")
    else:
        print("Invalid response. Please enter 'True' or 'False'.")

ask_boolean_question1()

# Question 2: Boolean Expressions
# Ask a question about Boolean expressions and their importance in programming
# Provide feedback based on the correctness of the response

def ask_boolean_question2():
    global correct
    response = input("is (x>y && x>z) a boolean expression? (Enter 'True' or 'False'): ")
    print(response)
    if response.lower() == 'true':
        print("Correct!")
        correct += 1
    elif response.lower() == 'false':
        print("Incorrect.")
    else:
        print("Invalid response. Please enter 'True' or 'False'.")

ask_boolean_question2()
# Question 3: Conditional Statements
# Ask a question about the purpose of conditional (if-else) statements in programming
# Provide feedback based on the correctness of the response

def ask_boolean_question3():
    global correct
    response = input("is elif the same as else if? (Enter 'True' or 'False'): ")
    print(response)
    if response.lower() == 'true':
        print("Correct!")
        correct += 1
    elif response.lower() == 'false':
        print("Incorrect.")
    else:
        print("Invalid response. Please enter 'True' or 'False'.")

ask_boolean_question3()

# Question 4: Relational Operators
# Ask a question about common relational operators in programming and provide examples
# Provide feedback based on the correctness of the response

def ask_boolean_question4():
    global correct
    response = input("is a=b equals? (Enter 'True' or 'False'): ")
    print(response)
    if response.lower() == 'false':
        print("Correct!")
        correct += 1
    elif response.lower() == 'true':
        print("Incorrect.")
    else:
        print("Invalid response. Please enter 'True' or 'False'.")

ask_boolean_question4()

# Question 5: Logical Operators
# Ask a question about the use of logical operators in programming and provide examples
# Provide feedback based on the correctness of the response

def ask_boolean_question5():
    global correct
    response = input("The only logical operators are AND and OR (Enter 'True' or 'False'): ")
    print(response)
    if response.lower() == 'false':
        print("Correct!")
        correct += 1
    elif response.lower() == 'true':
        print("Incorrect.")
    else:
        print("Invalid response. Please enter 'True' or 'False'.")

ask_boolean_question5()

def ask_boolean_question6():
    global correct
    response = input("The != operator in programming checks whether two values are not equal. (Enter 'True' or 'False'): ")
    print(response)
    if response.lower() == 'true':
        print("Correct!")
        correct += 1
    elif response.lower() == 'false':
        print("Incorrect.")
    else:
        print("Invalid response. Please enter 'True' or 'False'.")

ask_boolean_question6()

def ask_boolean_question7():
    global correct
    response = input("The && operator in programming represents the logical OR operation. (Enter 'True' or 'False'): ")
    print(response)
    if response.lower() == 'false':
        print("Correct!")
        correct += 1
    elif response.lower() == 'true':
        print("Incorrect.")
    else:
        print("Invalid response. Please enter 'True' or 'False'.")

ask_boolean_question7()

def ask_boolean_question8():
    global correct
    response = input("The >= operator checks if the value on the left is greater than or equal to the value on the right. (Enter 'True' or 'False'): ")
    print(response)
    if response.lower() == 'true':
        print("Correct!")
        correct += 1
    elif response.lower() == 'false':
        print("Incorrect.")
    else:
        print("Invalid response. Please enter 'True' or 'False'.")

ask_boolean_question8()

def ask_boolean_question9():
    global correct
    response = input("The else if statement in programming is used to handle multiple conditions sequentially. (Enter 'True' or 'False'): ")
    print(response)
    if response.lower() == 'true':
        print("Correct!")
        correct += 1
    elif response.lower() == 'false':
        print("Incorrect.")
    else:
        print("Invalid response. Please enter 'True' or 'False'.")

ask_boolean_question9()


# Display the final score
# Calculate the percentage of correct answers and provide feedback
print(user_name + ", you scored " + str(correct) + "/" + str(questions))
```

    Hello, ryan liao running /bin/python
    You will be asked 9 questions.
    true
    Correct!
    true
    Correct!
    true
    Correct!
    false
    Correct!
    false
    Correct!
    true
    Correct!
    false
    Correct!
    true
    Correct!
    true
    Correct!
    ryan liao, you scored 9/9

