---
comments: True
layout: post
toc: True
title: Login Page test
description: True
type: tangibles
courses: {'compsci': {'week': 19}}
---

```python
%%HTML
<div id="login">
    <p><label>
        User ID:
        <input type="text" name="uid" id="uid" required>
    </label></p>
    <p><label>
        Password:
        <input type="password" name="password" id="password" required>
    </label></p>
    <p>
        <button class="button" type="submit">Log in</button>
    </p>
</div>
<script>
    document.getElementById('login').addEventListener('submit', function(event) {
             event.preventDefault(); 
             const uid = document.getElementById('uid').value;
             const password = document.getElementById('password').value;
             const loginData = {
                 uid: uid,
                 password: password
             };
             fetch('http://127.0.0.1:8086/api/users/login', { // use your own port please
                 method: 'POST',
                 headers: {
                     'Content-Type': 'application/json'
                 },
                 body: JSON.stringify(loginData)
             })
             .then(response => {
                 if (response.ok) {
                     return response.json();
                 } else {
                     if (response.status === 401) {
                         throw new Error('Wrong username or password. Please retype.');
                     } else if (response.status === 404) {
                         throw new Error('Username or password not found. Please register first.');
                     } else {
                         throw new Error('Login failed');
                     }
                 }
             })
             .then(data => {
                 console.log('it worked!');
             })
             .catch(error => {
                 console.error('Error:', error.message);
                 alert(error.message);
             });
         });
     </script>
```
