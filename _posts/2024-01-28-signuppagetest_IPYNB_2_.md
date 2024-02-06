---
layout: post
title: signup page test
description: e
toc: True
comments: True
categories: ['5.A', 'C4.1']
courses: {'csp': {'week': 19}}
type: tangibles
---

%%HTML
<div id="signup">
  <p><label>
      Name:
      <input type="text" name="name" id="name" required>
  </label></p>
  <p><label>
      User ID:
      <input type="text" name="uid" id="uid" required>
  </label></p>
  <p><label>
      Password:
      <input type="password" name="password" id="password" required>
  </label></p>
  <p>
      <button class="button" type="submit" onclick="signup()" >Sign Up</button>
  </p>
</div>

<script>
  function signup() {
       var name = document.getElementById('name').value;
       var uid = document.getElementById('uid').value;
       var password = document.getElementById('password').value;
       var requestBody = {
           name: name,
           uid: uid,
           password: password
       };
       fetch('http://127.0.0.1:8086/api/users/create', { //use your own port
           method: 'POST',
           headers: {
               'Content-Type': 'application/json',
           },
           body: JSON.stringify(requestBody),
       })
       .then(response => response.json())
       .then(data => {
           console.log('Sign Up successful:', data);
           window.location.href = "http://localhost:4200/Ryan-Blog-theREAL//5.a/c4.1/2024/01/28/loginpagetest_IPYNB_2_.html";
       })
       .catch(error => {
           console.error('Error:', error);
       });
   }
</script>

