---

---

# What is JWT
JWT (JSon Web tokens) is a compact url safe means of representing claims bewtween two parties

# Parts of JWT

- Header: The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA. This part is base64Url encoded.

- Payload: Contains the claims, which are statements about an entity (typically, the user) and additional data. There are three types of claims: registered, public, and private claims. This part is also base64Url encoded.

- Signature: used to verify that the sender of the JWT is who it says it is and to ensure that the message wasn't changed along the way. The signature is appended to the encoded header and payload. This part is used to verify the integrity of the token.

## Encoded JWT:

eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c

- looks like hectic scramble of letters because of encription
- Result of applying Base64Url encoding to the JWT’s header, payload, and signature
    - String of three parts concatenated with dots: encoded header, payload, and signature
    - Purpose: makes JWT compact, URL-sage, and easy to transmit over networks
- Compact, used for transmission

Decoded JWT:{ “sub”: “1234567890”, “name”: “John Doe”, “iat”: 1516239022 }

# Implementing JWT into Flask Project

**CORS Configuration:**

The code below allows for cross origin resource sharing. This is needed for the front end to be able to access the backend when they are running on different domains. With suports_credentials set to true, credentials with requests are included allowing for authenticatin.



```python
cors = CORS(app, supports_credentials=True)
```

**Dynamic Allowed Origins:**

The code below only allows specified origins to access the backend. Using the list of allowed origins, the code checks if the origin of the request is in the list of allowed origins. If it is, the origin is added to the response headers. If it is not, the origin is not added to the response headers.




```python

@app.before_request
def before_request():
    allowed_origin = request.headers.get('Origin')
    if allowed_origin in ['http://localhost:4100', 'http://127.0.0.1:4100', 'https://nighthawkcoders.github.io']:
        cors._origins = allowed_origin
```

**SameSite Attribute in set_cookie:**

- The samesite='None' allows for the cookie to be sent with cross-site requests.
- token: The value of the cookie.
- max_age=3600: The maximum age of the cookie in seconds (1 hour in this case).
- secure=True: Specifies that the cookie should only be sent over HTTPS connections.
- httponly=True: Ensures that the cookie is only accessible through HTTP requests and not through client-side scripts.
- path='/: Specifies the path for which the cookie is valid (in this case, the root path '/').



```python

resp.set_cookie(
    "jwt",
    token,
    max_age=3600,
    secure=True,
    httponly=True,
    path='/',
    samesite='None'
)
```

**Nginx Preflighted Requests Configuration:**

First the code checks if the request method is OPTIONS.

If the condition is met (OPTIONS request), the following actions are taken:
- add_header "Access-Control-Allow-Credentials" "true" always;: server supports credentials such as cookies in CORS requests

- add_header "Access-Control-Allow-Origin" "https://nighthawkcoders.github.io" always;: Specifies the allowed origin for the cross-origin request.

- add_header "Access-Control-Allow-Methods" "GET, POST, PUT, OPTIONS, HEAD" always;: gives a list of HTTP methods that are allowed to access the resource.

- add_header "Access-Control-Allow-MaxAge" 600 always;: Specifies the maximum time (in seconds) the results of a preflight request can be cached.

- add_header "Access-Control-Allow-Headers" "Authorization, Origin, X-Requested-With, Content-Type, Accept" always;: Lists the allowed headers for the actual request.

- return 204;: Responds with a 204 No Content status code, indicating that the preflight request was successful and there is no need to send the actual request.


```python

if ($request_method = OPTIONS) {
    add_header "Access-Control-Allow-Credentials" "true" always;
    add_header "Access-Control-Allow-Origin"  "https://nighthawkcoders.github.io" always;
    add_header "Access-Control-Allow-Methods" "GET, POST, PUT, OPTIONS, HEAD" always;
    add_header "Access-Control-Allow-MaxAge" 600 always;
    add_header "Access-Control-Allow-Headers" "Authorization, Origin, X-Requested-With, Content-Type, Accept" always;
    return 204;
}
```

# Installation

1. Install JWT extension or Flask-JWT-Extended extension


```python
pip install pyJWT
```

2. Create Flask app and initialize JWT


```python
from flask import Flask
from pyJWT import JWTManager

app = Flask(__name__)
app.config['JWT_SECRET_KEY'] = 'your-secret-key'  # Replace with a strong secret key
jwt = JWTManager(app)
```

3. Create a login endpoint to generate tokens:


```python
@app.route('/login', methods=['POST'])
def login():
    # Verify user credentials
    if verify_credentials():  # Replace with your authentication logic
        user_id = get_user_id()
        access_token = create_access_token(identity=user_id)  # JWT creation
        return jsonify({'access_token': access_token})
    else:
        return jsonify({'error': 'Invalid credentials'}), 401
```

4. Protect routes with jwtrequired decorator


```python
@app.route('/protected')
@jwt_required
def protected():
    current_user = get_jwt_identity()  # Access user information from token
    return jsonify({'message': 'Hello, {}!'.format(current_user)})
```

## Validation of JWT Cookie

Validating JWT cookies ensures the integrity and authenticity of user sessions, guarding against tampering, expiration, and unauthorized access in web applications. 

Validating a JWT takes multiple steps. Below is a simple Python script using the PyJWT library to demonstrate JWT validation. 

<br>
<br>
<br>

Make sure to install the library first 


```python
pip install PyJWT
```

After that, run this python script using the PyJWT library to demonstrate JWT validation


```python
import jwt
from datetime import datetime, timedelta

SECRET_KEY = 'your_secret_key_here'

def create_jwt():
    payload = {
        'user_id': 123,
        'username': 'john_doe',
        'exp': datetime.utcnow() + timedelta(hours=1)
    }
    token = jwt.encode(payload, SECRET_KEY, algorithm='HS256')
    return token
def validate_jwt(token):
    try:
        payload = jwt.decode(token, SECRET_KEY, algorithms=['HS256'])
        print("JWT Validation Successful!")
        print("Payload:", payload)
    except jwt.ExpiredSignatureError:
        print("JWT has expired. Please obtain a new token.")
    except jwt.InvalidTokenError:
        print("Invalid JWT. Authentication failed.")

if __name__ == "__main__":
    jwt_token = create_jwt()
    print("Generated JWT:", jwt_token)

    validate_jwt(jwt_token)
```

    Generated JWT: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxMjMsInVzZXJuYW1lIjoiam9obl9kb2UiLCJleHAiOjE3MDU5NDQ5MjF9.EFt_W-nQPIn9k4IKyuVWJz-6yKgDcUTDNX9jix5AmaQ
    JWT Validation Successful!
    Payload: {'user_id': 123, 'username': 'john_doe', 'exp': 1705944921}


In this Python script, the jwt library is employed to handle JSON Web Tokens (JWTs) for user authentication. The create_jwt function generates a JWT with a payload containing user information, including a user ID, username, and an expiration time set to one hour from the current time. The jwt.encode function combines this payload with a secret key using the HMAC SHA256 algorithm to create a secure token. 

The validate_jwt function takes a JWT as input, attempts to decode it using the same secret key, and checks for validity. If successful, it prints the decoded user details; otherwise, it handles expired or invalid tokens by raising specific exceptions. The script demonstrates the creation and validation of JWTs for secure user authentication.

# JWT Cookies

Cookies are pieces of information that are used to be sent to from a server to a browser and stored on the device it has been sent to. They are then sent back to the server with data about the user's interactions with the site which will help the server store the user's preferences and info throughout the website. Cookies can also help keep users authenticated on servers by storing authentication tokens to the server. 

# Anatomy of Flask

- main.py: This Python source file serves as the entry point for running, testing, and debugging your project. It is the central script for project execution.


- Dockerfile and docker-compose.yml: These files facilitate running and testing your project within a Docker container, allowing simulation of deployment scenarios on servers like AWS. They ensure project functionality consistency across diverse environments.


- instances: This directory serves as the base location for storing persistent data files on the server. Files stored here persist through web application restarts, contrasting with other areas that get recreated during restarts.


- static: This directory acts as the base location for files, such as images or JavaScript files, intended to be stored and cached by the web server. It is typically used for static content that remains constant during web server execution.


- api: This directory holds code responsible for receiving and responding to requests from external servers. It functions as the interface connecting the external world with the logic and code in the rest of your project.


- model: Within this directory, files implement backend functionality, including direct interactions with the database. It serves as a crucial component supporting the code in the api directory.


- templates: This directory, along with its subdirectories, contains files supporting the home and error pages of your project's site, providing the necessary structure for rendering these pages.

![Screenshot 2024-01-21 at 11.06.03 PM.png](<attachment:Screenshot 2024-01-21 at 11.06.03 PM.png>)
