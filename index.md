---
layout: default
title: Student Blog
---


## Build your Home Page here 
This is about your journey. Start now!!!

## Overview of Hacks, Study and Tangibles
Blogging in GitHub pages is a way to learn and code at the same time. 

## Hi, I'm Ryan Liao. This is my first ever GitHub Webpage! 

-Dates: 

8/20/23: I set up all of my programs.

8/21/23: Running into errors with bundle install, I reinstalled all softwares but still could not get progress.

8/22/23: This morning I finally got bundle install to work! Not only that, but the localhost works as well. The only issue I've encountered today is jupyter kernelspec list not being seen as a command in wsl. However, everything works for now. I am going to go through the process of pushing my first ever changes to github from VSCode. I sure hope nothing goes wrong! 

8/23/23: Today was much less stressful, and I learned how to customize my github page. I added an image, a schedule for myself, and even a video player; however, I realized that having a clickable video on localhost isn't something I can learn and do within a day. It'll definitely be a work in progress I will learn to do over the trimester. 

8/24/23: 

| Week   | Jobs Finished |
| -------- | ------- |
| 0  |  Tools and Equipment Overview; VSCode, GitHub Pages Setup   | 
| 1 |      |
|  2  |     |
|  3   |     |

<img src="https://media.discordapp.net/attachments/1081856159855677464/1144158764040196118/image.png?width=732&height=364">

<img src="https://i1.sndcdn.com/artworks-t7I8MnGT22aUwxEL-pOTXZw-t500x500.jpg">

<input type="file" accept="video/*" />
<video controls autoplay></video>

<script src="https://code.jquery.com/jquery-2.2.4.min.js"></script>
<script>
$('input').on('change', changeEvent => {
  var reader = new FileReader();
  reader.onload = onLoadEvent => $('video').attr('src', onLoadEvent.target.result).play();
  reader.readAsDataURL(changeEvent.currentTarget.files[0]);
});
</script>

