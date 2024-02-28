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

<img src = "https://media.discordapp.net/attachments/1212280374705651772/1212280747348598834/daf8f635dd638b4806cce9fe67ae0d73.png?ex=65f1436d&is=65dece6d&hm=be8e33a801a01800c4f4ef97fb6e76d2f77703660c22ee2035803745163ee277&=&format=webp&quality=lossless">

First, the user must login before accessing the comments page. In this login page, there is a button to store the UID, and the button to proceed to the commenting page. When the user enters in their credentials, then clicks to store the UID, their UID will be stored in localstorage. This allows data to persist through a redirect that will happen when proceeding without needing to follow CORS.

<img src = "https://media.discordapp.net/attachments/1212280374705651772/1212282173818798120/image.png?ex=65f144c1&is=65decfc1&hm=cafa963e34a2e428c4a94c4367a04139ebb72cd55a4e9e950536e7c2ff6fd04c&=&format=webp&quality=lossless&width=742&height=418">

 I also ensured that before proceeding, the UID must be stored, and also made sure that the account is valid and within the user database. 


After redirect, the catalogue is displayed. 

<img src = "https://media.discordapp.net/attachments/1212280374705651772/1212282387845877780/image.png?ex=65f144f4&is=65decff4&hm=9c761e72fae0cb8b6a9e08258e88462cab3d950ea98466e63767d7ee10c242df&=&format=webp&quality=lossless">

<img src = "https://media.discordapp.net/attachments/1212280374705651772/1212282518649180181/image.png?ex=65f14513&is=65ded013&hm=302147c64068881983b71256a8e7bd851c050f42552eb354a33e59505dd14a2f&=&format=webp&quality=lossless&width=893&height=418">

When you click the button to submit the comment, the text in the "restaurant", the number in the "rating", and the current user's UID are grouped together to be a "newComment" which is formatted in JSON to be inserted into localstorage. The page is reset, and the comments in localstorage will then display in the actual page. 

# Meeting CPT Requirements through Collegeboard 

| Requirements   | What I did |
| -------- | ------- |
| Instructions for input from one of the following: the user, a device, an online datas stream, a file.  | User inputs text into a catalogue, text is saved in localstorage   |
| Use of at least one list (or other collection type) to represent a collection of data that is stored and used to manage program complexity and help fulfill the users purpose. | Localstorage is used as a local database specific to the device   |
| At least one procedure that contributed to the program’s intended purpose where you have defined: the name, return type, one or more parameters:    | <img src = "https://media.discordapp.net/attachments/1212280374705651772/1212282634634403922/image.png?ex=65f1452f&is=65ded02f&hm=2beaea1bdd21a3acac46508247190d35aafc911950984df963bbf917384050ea&=&format=webp&quality=lossless"> name of the function is redirect, forces user to store UID or else code will return an error message, parameter is "data" which is the name, uid, and password, used to verify the user is in the user.py database |
| An algorithm that includes sequencing, selection, and iteration that is in the body of the selected procedure | <img src = "https://media.discordapp.net/attachments/1212280374705651772/1212282879057465344/image.png?ex=65f14569&is=65ded069&hm=de41804cf2b2ac8ae5b24f8d44da2dd4360cdebba0b6fa73eea6879a39f5f688&=&format=webp&quality=lossless"> SubmitComment defines a comment as the stored uid from the above code, restaurant, rating, and it also specifically adds the new comment to the catalogue. page refreshes and the update can be visually seen  |
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
