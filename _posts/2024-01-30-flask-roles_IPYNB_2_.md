---
comments: True
layout: notebook
title: Flask JWT Roles for User / Admin user
type: tangibles
toc: True
courses: {'compsci': {'week': 4}}
---

# Goal
- This team teach will show you how to add roles to users when they create their account

- Roles are like Google Doc sharing permissions: you can give someone Viewer, Commenter, or Editor permissions
- Roles can be used in your code to restrict access to certain actions and pages 

- If you want to follow along, go to the [users.py](https://files.slack.com/files-pri/TUDAF53UJ-F06GVLB0A72/users.png) file of your cpt project that you cloned.


```python
class User(db.Model):
    # ... (existing code)


#-------------------------------------------------------------------------------------------------------------------------------------------------#
    # Goes into your users.py file. This will create a column dedicated for roles
    _role = db.Column(db.String(20), default="User", nullable=False)
    
#-------------------------------------------------------------------------------------------------------------------------------------------------#



    def __init__(self, name, uid, password="123qwerty", dob=date.today(), role="User"):
        # ... (existing code)
        self._role = role



#-------------------------------------------------------------------------------------------------------------------------------------------------#
    # With this property, you can access the user's role using user_instance.role instead of user_instance._role.
    @property
    def role(self):
        return self._role
#-------------------------------------------------------------------------------------------------------------------------------------------------#



#-------------------------------------------------------------------------------------------------------------------------------------------------#
    # With this setter, you can update the user's role using the assignment syntax: user_instance.role = "NewRole".
    @role.setter
    def role(self, role):
        self._role = role
#-------------------------------------------------------------------------------------------------------------------------------------------------#



#-------------------------------------------------------------------------------------------------------------------------------------------------#
    # This method returns True if the user's role is "Admin" and False otherwise.
    def is_admin(self):
        return self._role == "Admin"
#-------------------------------------------------------------------------------------------------------------------------------------------------# 
  
  
  
    # ... (existing code)

    # CRUD read converts self to dictionary
    # returns dictionary
    def read(self):
        return {
            "id": self.id,
            "name": self.name,
            "uid": self.uid,
            "dob": self.dob,
            "age": self.age,
    #-------------------------------------------------------------------------------------------------------------------------------------------------#
            # When you GET/read the endpoint, it will also return the user's role
            "role": self.role,
    #-------------------------------------------------------------------------------------------------------------------------------------------------#
            "posts": [post.read() for post in self.posts]
        }

```

Popcorn Hack 1: What is the function of CRUD read (Check comments)?
Answer: 


```python
def initUsers():
    with app.app_context():
        """Create database and tables"""
        db.create_all()
        """Tester data for table"""
        #-------------------------------------------------------------------------------------------------------------------------------------------------#
        # When you create the test users for the database, you can add a role for them. In this case, Thomas Edison has the role "Admin"
        u1 = User(name='Thomas Edison', uid='toby', password='123toby', dob=date(1847, 2, 11), role="Admin")
        #-------------------------------------------------------------------------------------------------------------------------------------------------#

# ... (existing code)
```

- This file is [user.py](https://files.slack.com/files-pri/TUDAF53UJ-F06G3UZQHSR/user.png)(not users.py which was the file above) of your cpt project that you cloned.


```python
    class _Security(Resource):
        def post(self):
            try:
                body = request.get_json()
                if not body:
                    return {
                        "message": "Please provide user details", #After attempting to retrieve JSON data, this block checks if the body is empty or None. 
                        #If there's no JSON data in the request, the function returns a JSON response indicating that the user should provide user details, along with a status code of 400 (Bad Request). 
                        #This is a common practice to handle cases where the expected data is missing or improperly formatted.
                        "data": None,
                        "error": "Bad request"
                    }, 400
                ''' Get Data '''
                uid = body.get('uid') #checks for UID
                if uid is None:
                    return {'message': f'User ID is missing'}, 400
                password = body.get('password') #checks and looks if possible password is there.
                
                ''' Find user '''
                user = User.query.filter_by(_uid=uid).first()
                if user is None or not user.is_password(password):
                    return {'message': f"Invalid user id or password"}, 400
                if user:
                    try:
                #-------------------------------------------------------------------------------------------------------------------------------------------------# 
                        # The only change you're making is that you include the user's role when they get authenticated
                        token_payload = {
                            "_uid": user._uid,
                            "role": user.role  # Add the role information to the token
                        }
                #-------------------------------------------------------------------------------------------------------------------------------------------------# 

                        token = jwt.encode(
                            token_payload,
                            current_app.config["SECRET_KEY"],
                            algorithm="HS256"
                        )
# ... (existing code)

```



- This file is [auth_middleware.py](https://files.slack.com/files-pri/TUDAF53UJ-F06GVLAT32L/auth-middleware.png) of your cpt project that you cloned.


```python
from functools import wraps
import jwt
from flask import request, abort
from flask import current_app
from model.users import User

#-------------------------------------------------------------------------------------------------------------------------------------------------# 
# Whenver you call this function in your code, you can add an argument like Roles="Admin" to only allow admins to access a certan part.
def token_required(roles=None):
#-------------------------------------------------------------------------------------------------------------------------------------------------# 
    def decorator(f):
        @wraps(f)
        def decorated(*args, **kwargs):
            token = request.cookies.get("jwt")
            if not token:
                return {
                    "message": "Authentication Token is missing!",
                    "data": None,
                    "error": "Unauthorized"
                }, 401
            try:
                data = jwt.decode(token, current_app.config["SECRET_KEY"], algorithms=["HS256"])
                current_user = User.query.filter_by(_uid=data["_uid"]).first()
                if current_user is None:
                    return {
                        "message": "Invalid Authentication token!",
                        "data": None,
                        "error": "Unauthorized"
                    }, 401
            #-------------------------------------------------------------------------------------------------------------------------------------------------# 
                # Check if roles are provided and user has the required role
                if roles and current_user.role not in roles:
                    return {
                        "message": "Insufficient permissions. Required roles: {}".format(roles),
                        "data": None,
                        "error": "Forbidden"
                    }, 403
            #-------------------------------------------------------------------------------------------------------------------------------------------------# 

            except Exception as e:
                return {
                    "message": "Something went wrong",
                    "data": None,
                    "error": str(e)
                }, 500

            return f(current_user, *args, **kwargs)

        return decorated

    return decorator
```

**Popcorn Hack 2:** What is the purpose of "def token_required(roles=None):" ?
Answer: 


- Here's a[Freeform Diagram](https://www.icloud.com/freeform/0c8SFCHzE4hcs14rPpq0h4LNQ#User_Flow) to help you better understand each file
![Freeform Diagram](../../../images/Freeform Diagram.png)


