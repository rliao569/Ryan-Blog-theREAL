---
comments: True
layout: post
toc: True
title: Signup Page test
description: True
type: tangibles
courses: {'compsci': {'week': 19}}
---

```python
class _Create(Resource):
        def post(self):
            body = request.get_json()
            name = body.get('name')
            uid = body.get('uid')
            password = body.get('password')
            if uid is not None:
                new_user = User(name=name, uid=uid, password=password)
            user = new_user.create()
            if user:
                return user.read()
            return {'uid is possibly a dupe'}, 400
 api.add_resource(_Create, '/create')
```


```python
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
       fetch('http://localhost:8086/api/users/create', { //use your own port
           method: 'POST',
           headers: {
               'Content-Type': 'application/json',
           },
           body: JSON.stringify(requestBody),
       })
       .then(response => response.json())
       .then(data => {
           console.log('Sign Up successful:', data);
           window.location.href = "{{site.baseurl}}/login";
       })
       .catch(error => {
           console.error('Error:', error);
       });
   }
</script>

```
