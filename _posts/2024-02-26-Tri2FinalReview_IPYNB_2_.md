---
layout: post
title: Tri 2 Final Review
description: Tri 2 final review...
toc: True
comments: True
categories: ['5.A', 'C4.1']
courses: {'csse': {'week': 8}, 'csp': {'week': 24, 'categories': ['6.B']}, 'csa': {'week': 9}}
type: tangibles
---

Below is a journey of temporary suffering and eternal glory.


# Our Project

Team Wakao's project is based around chinese food. We collectively agreed that it is inconvenient finding good chinese food near us. So, we decided to make a website that helps you find and learn about chinese food. We have the following features:

- User login and signup
- Chinese food informational chart
- Restuarants comments/catalogue
- Food finder (IN PROGRESS)

# My Main Feature: Resutaurant Comments/reviews

This allows users to leave comments/reviews for restaurants on a page. 

![image.png](https://gyazo.com/daf8f635dd638b4806cce9fe67ae0d73)

First, the user must login before accessing the comments page. In this login page, there is a button to store the UID, and the button to proceed to the commenting page. When the user enters in their credentials, then clicks to store the UID, their UID will be stored in localstorage. This allows data to persist through a redirect that will happen when proceeding without needing to follow CORS.

![image-2.png](https://gyazo.com/0a449d3e8df3a20596afc22bae80330f)

![image-3.png](https://gyazo.com/9e52d1d09e71860a6e80f4891f269a6c)

 I also ensured that before proceeding, the UID must be stored, and also made sure that the account is valid and within the user database. 


After redirect, the catalogue is displayed. 

![image-2.png](https://gyazo.com/7b6ffa969b1dac2f4a5177fe7a81719a)

![image-4.png](https://gyazo.com/4dfa340147457716a4759214fa1a4d13)

When you click the button to submit the comment, the text in the "restaurant", the number in the "rating", and the current user's UID are grouped together to be a "newComment" which is formatted in JSON to be inserted into localstorage. The page is reset, and the comments in localstorage will then display in the actual page. 

# Meeting CPT Requirements through Collegeboard 

| Requirements   | What I did |
| -------- | ------- |
| Instructions for input from one of the following: the user, a device, an online datas stream, a file.  | User inputs text into a catalogue, text is saved in localstorage   |
| Use of at least one list (or other collection type) to represent a collection of data that is stored and used to manage program complexity and help fulfill the users purpose. | Localstorage is used as a local database specific to the device   |
| At least one procedure that contributed to the program’s intended purpose where you have defined: the name, return type, one or more parameters:    | ![image-3.png](https://gyazo.com/52de04f04f55ddbd380e147c01051097) name of the function is redirect, forces user to store UID or else code will return an error message, parameter is "data" which is the name, uid, and password, used to verify the user is in the user.py database |
| An algorithm that includes sequencing, selection, and iteration that is in the body of the selected procedure | ![image.png](https://gyazo.com/cc32e004ba6915353111083cc344a20d) SubmitComment defines a comment as the stored uid from the above code, restaurant, rating, and it also specifically adds the new comment to the catalogue. page refreshes and the update can be visually seen  |
| Calls to your student-developed procedure: | In progress, once real api is developed |
| Instructions for output (tactile, audible, visual, or ) based on input and program functionality | seen above in "an algorithm that includes sequencing..." |

# Video

[Link to my video](https://drive.google.com/file/d/1JvF_CvnWhmDdI3q7-54aVI-e6YiHaI-F/view?usp=sharing)

| CB REQUIREMENTS | WHAT I DID |
| -------- | ------- |
| Input to program | entered text |
| At least one aspect of the functionality of your program | login functionality, text is stored in localstorage |
| Output produced by program: | form is resubmitted, new localstorage table is displayed on page |
| My video does not have: | voice or captions |
| My video is: | a .webmb, less than 1 minute in length, less than 30MB in file size. |
