---
toc: True
comments: True
layout: post
title: Html and Javascript for User Profiles
description: None
type: hacks
courses: {'compsci': {'week': 17}}
---

## CRUD Operations
CRUD stands for create, read, update, and delete which are the 4 basic functions for managing data in a database or storage system.

Procedures:
- **CREATE**
    - Adds new data to the system
    - Usually completed by an operation like an insert statement by creating a new record or new object
- **READ**
    - Retrieves and reads existing data
    - Usually used for querying and fetching data information
- **UPDATE**
    - Makes changes to existing data
    - In this case, it would be if the user wants to update or change parts of their user profile like username, password, name, etc.
- **DELETE**
    - Removes data from the system
    - Deletes a record or object

CRUD operations are important for interacting with databases and controlling data in software applications. These functions set the foundations for data management and are used in many systems, no matter how minor or complex. They provide a standardized way to handle data throughout its lifecycle from its creation to modification to elimination.

The code below is a simple format of creating or updating user profiles in html.


```python
%%HTML
<div id="profile">
    <label for="name">Name:</label>
    <input type="text" id="name" required>
  
    <label for="uid">User ID:</label>
    <input type="text" id="uid" required>
  
    <label for="password">Password:</label>
    <input type="password" id="password" required>
  
    <button type="submit" onclick="createProfile()">Create Profile</button>
  </div>
```


<div id="profile">
    <label for="name">Name:</label>
    <input type="text" id="name" required>

    <label for="uid">User ID:</label>
    <input type="text" id="uid" required>

    <label for="password">Password:</label>
    <input type="password" id="password" required>

    <button type="submit" onclick="createProfile()">Create Profile</button>
  </div>



Once you have the html format of the user profile page, you can establish the CRUD procedures like in the example below.


```python
// In-memory data structure
  let users = [];

  // CREATE operation
  function createProfile() {
    const name = document.getElementById('name').value;
    const uid = document.getElementById('uid').value;
    const password = document.getElementById('password').value;

    if (uid.length > 0) {
      const existingUser = users.find(user => user.uid === uid);

      if (existingUser) {
        // Update existing user
        const updatedUser = updateUser(existingUser.id, name, uid, password);
        console.log('Updated User:', updatedUser);
      } else {
        // Create new user
        const newUser = createUser(name, uid, password);
        console.log('Created User:', newUser);
      }

      // Reset form fields
      document.getElementById('name').value = '';
      document.getElementById('uid').value = '';
      document.getElementById('password').value = '';

    } else {
      console.log('Invalid input. User ID is required.');
    }
  }

  // READ operation
  function getAllUsers() {
    return users.map(user => ({ ...user }));
  }

  // UPDATE operation
  function updateUser(id, name, uid, password) {
    const userIndex = users.findIndex(user => user.id === id);
    if (userIndex !== -1) {
      users[userIndex] = {
        ...users[userIndex],
        name,
        uid,
        password,
      };
      return { ...users[userIndex] };
    }
    return null;
  }

  // DELETE operation
  function deleteUser(id) {
    const initialLength = users.length;
    users = users.filter(user => user.id !== id);
    return users.length !== initialLength;
  }
```

Here is another [sample](https://github.com/nighthawkcoders/devOps/blob/main/api/user.py) to use when creating these functions in your own user login and profile page.

## Sample User Interface
(image)

Sample code for the form:
- The code creates an HTML form, and when it's submitted, a JavaScript function named submitForm is called. This function can be customized to handle the form submission in a specific way. Typically, it includes preventing the default form submission behavior to enable custom processing.
- main labels for this sample:
    - Github username, full name, password, and submit button
    


```python
%%HTML
<form onsubmit="submitForm(event)">
    <!-- GitHub Username Input -->
    <label for="githubUsername">GitHub Username:</label>
    <input type="text" id="githubUsername" name="githubUsername" required /><br /><br />

    <!-- Full Name Input -->
    <label for="fullName">Full Name:</label>
    <input type="text" id="fullName" name="fullName" required /><br /><br />

    <!-- Password Input -->
    <label for="password">Password:</label>
    <input type="password" id="password" name="password" required /><br /><br />

    <!-- Submit Button -->
    <input type="submit" value="Submit" />
</form>
```


<form onsubmit="submitForm(event)">
    <!-- GitHub Username Input -->
    <label for="githubUsername">GitHub Username:</label>
    <input type="text" id="githubUsername" name="githubUsername" required /><br /><br />

    <!-- Full Name Input -->
    <label for="fullName">Full Name:</label>
    <input type="text" id="fullName" name="fullName" required /><br /><br />

    <!-- Password Input -->
    <label for="password">Password:</label>
    <input type="password" id="password" name="password" required /><br /><br />

    <!-- Submit Button -->
    <input type="submit" value="Submit" />
</form>



This code defines a JavaScript constant (apiUrl) with a value representing the base URL for making API requests to manage users. It also initializes an array (users) that is intended to store user data retrieved from the API.


```python
//Sample
const apiUrl = "https://devops.nighthawkcodingsociety.com/api/users/";
	// const apiUrl = "http://localhost:8180/api/users/";
	let users = [];
```

The code down below is used after defining the apiUrl and it features the function fetchUsers() which is a function that fetches user data from an API, then dynamically populates an HTML table with user information, and adds "Edit" and "Delete" buttons for each user. The dynamically created buttons also have associated event listeners to handle user interactions.
- Event listeners are code that "listen" for specific actions/events to occur on a webpage. When the specified event occurs, the code (a callback function) is executed.


```python
function fetchUsers() {
    fetch(apiUrl)
        .then((response) => response.json())
        .then((response) => {
            users = response;

            const table = document.getElementById("userTable");
            users.forEach((user, idx) => {
                const row = table.insertRow();

                row.setAttribute("data-id", user.id);
                ["name", "uid"].forEach(
                    (field) => {
                        const cell = row.insertCell();
                        if (user[field] === "none") {
                            users[idx][field] = "";
                        }
                        cell.innerText = users[idx][field];
                    }
                );

                const editCell = row.insertCell();
                const editButton = document.createElement("button");
                editButton.innerHTML = "Edit";
                editButton.addEventListener("click", editUser);
                editCell.appendChild(editButton);

                const deleteCell = row.insertCell();
                const deleteButton = document.createElement("button");
                deleteButton.innerText = "Delete";
                deleteButton.addEventListener("click", () => deleteUser(user.id, row));
                deleteCell.appendChild(deleteButton);
            });
        });
}
```

## User Authentication and Token Generation

Authentication in code often involves the use of tokens. Tokens are a way to verify the identity of a user or a system and grant access to specific resources. Token-based authentication is commonly used in web applications, APIs, and other distributed systems. Here's a brief overview of how token-based authentication works:

1. When a user logs in, they provide their credentials (such as username and password) to the authentication server.The authentication server validates the credentials, and if they are correct, it generates a token.

2. The token is a piece of data that contains information about the user (or system) and their permissions.This token is then signed by the authentication server using a secret key to ensure its integrity.

After importing all necessary statements and Blueprint/API setup we can move on to UserAPI Class Definition.



```python
class UserAPI:
    # …
```

This class contains two inner classes: _CRUD and _Security
While _CRUD handles Create (POST) and Read (GET) operations for user data
_Security handles user authentication and token generation

These are your _CRUD Operations: 


```python
class _CRUD(Resource):
    @token_required
    def post(self, current_user):
        # ... (Code for user creation)
    
    @token_required
    def get(self, current_user):
        # ... (Code for reading all users)
```

@token_required ensuring that the user is authenticated before executing these methods (post and get)

Now as for token generation:


```python
class _Security(Resource):
    def post(self):
        # ... (Code for user authentication and token generation)
```

The post method takes user credentials from the request, validates them against the database, and issues a JWT token if authentication is successful.
The token is then set as a cookie in the response.

After authentication and token generation, we can conclude with the REST API Endpoint Setup:


```python
api.add_resource(_CRUD, '/')
api.add_resource(_Security, '/authenticate')
```

This just adds the _CRUD and _Security classes as resources to the Flask-RESTful API.

Overall, the code represents the implementation of a RESTful API for user management, including user creation, reading all users, and user authentication with token generation.


```python
<form onsubmit="submitForm(event)">
	<label for="githubUsername">GitHub Username:</label>
	<input type="text" id="githubUsername" name="githubUsername" required /><br /><br />

	<label for="fullName">Full Name:</label>
	<input type="text" id="fullName" name="fullName" required /><br /><br />

	<label for="password">Password:</label>
	<input type="password" id="password" name="password" required /><br /><br />

	<label>Need Server:</label>
	<input type="radio" id="yes" name="serverNeeded" value="Yes" required />
	<label for="yes">Yes</label>
	<input type="radio" id="no" name="serverNeeded" value="No" required />
	<label for="no">No</label><br /><br />

	<input type="submit" value="Submit" />
</form>

<script>
	const apiUrl = "https://devops.nighthawkcodingsociety.com/api/users/";
	// const apiUrl = "http://localhost:8180/api/users/";
	let users = [];

	function fetchUsers() {
		fetch(apiUrl)
			.then((response) => response.json())
			.then((response) => {
				users = response;

				const table = document.getElementById("userTable");
				users.forEach((user, idx) => {
					const row = table.insertRow();

					row.setAttribute("data-id", user.id);
					["name", "uid", "server_needed"].forEach(
						(field) => {
							const cell = row.insertCell();
							if (user[field] === "none") {
								users[idx][field] = "";
							}
							cell.innerText = users[idx][field];
						}
					);

					const editCell = row.insertCell();
					const editButton = document.createElement("button");
					editButton.innerHTML = "Edit";
					editButton.addEventListener("click", editUser);
					editCell.appendChild(editButton);

					const deleteCell = row.insertCell();
					const deleteButton = document.createElement("button");
					deleteButton.innerText = "Delete";
					deleteButton.addEventListener("click", () => deleteUser(user.id, row));
					deleteCell.appendChild(deleteButton);
				});
			});
	}

	function submitForm(event) {
		event.preventDefault();
		const formData = new FormData(event.target);
		const name = formData.get("fullName");
		const uid = formData.get("githubUsername");
		const password = formData.get("password");
		const serverNeeded = formData.get("serverNeeded") === "Yes";

		const payload = {
			name,
			uid,
			password,
			server_needed: serverNeeded,
		};

		fetch(apiUrl, {
			method: "POST",
			headers: {
				"Content-Type": "application/json",
			},
			body: JSON.stringify(payload),
		})
			.then((response) => {
				if (response.ok) {
					return response.json();
				} else {
					alert("server error");
					throw new Error("server");
				}
			})
			.then((data) => {
				const table = document.getElementById("userTable");
				const row = table.insertRow();
				row.setAttribute("data-id", data.id);
				[
					data.name,
					data.uid,
					data.server_needed,
				].forEach((value) => {
					const cell = row.insertCell();
					cell.innerText = value;
				});

				const editCell = row.insertCell();
				const editButton = document.createElement("button");
				editButton.innerHTML = "Edit";
				editButton.addEventListener("click", editUser);
				editCell.appendChild(editButton);

				const deleteCell = row.insertCell();
				const deleteButton = document.createElement("button");
				deleteButton.innerText = "Delete";
				deleteButton.addEventListener("click", () => deleteUser(user.id, row));
				deleteCell.appendChild(deleteButton);

				users.push(data);
				alert("Created sucessfully!");
			})
			.catch((error) => console.error("Error:", error));
	}

	function editUser(event) {
		const id = event.currentTarget.parentElement.parentElement.getAttribute("data-id");
		document.getElementById("editId").value = id;

		const form = document.getElementById("editForm");
		const user = users.find((u) => u.id == id);

		form.querySelector("#editGithubUsername").value = user.uid;
		form.querySelector("#editFullName").value = user.name;

		document.getElementById("editYes").checked = user.server_needed;
		document.getElementById("editNo").checked = !user.server_needed;


		document.getElementById("editModalBackdrop").style.display = "block";
	}

	// Fetch users and ensure close modal interaction
	document.addEventListener("DOMContentLoaded", function () {
		fetchUsers();
		document.getElementById("closeModal").addEventListener("click", function () {
			document.getElementById("editModalBackdrop").style.display = "none";
		});
	});

	function submitEdit(event) {
		event.preventDefault();
		const formData = new FormData(event.target);
		const id = formData.get("editId");
		const name = formData.get("editFullName");
		const uid = formData.get("editGithubUsername");
		const serverNeeded = formData.get("editServerNeeded") === "Yes";

		const payload = {
			id,
			name,
			uid,
			server_needed: serverNeeded,
		};

		fetch(`${apiUrl}${id}`, {
			method: "PUT",
			headers: {
				"Content-Type": "application/json",
			},
			body: JSON.stringify(payload),
		}).then((response) => {
			if (response.ok) {
				// Update the corresponding row in the table
				const row = document.querySelector(`tr[data-id='${id}']`);
				row.cells[0].innerText = name;
				row.cells[1].innerText = uid;
				row.cells[2].innerText = serverNeeded;

				// Show an alert indicating success
				alert("User information updated successfully.");
			}
		});

		document.getElementById("editModalBackdrop").style.display = "none";
	}

	function deleteUser(id, row) {
		const confirmation = prompt('Type "DELETE" to confirm.');
		if (confirmation === "DELETE") {
			fetch(`${apiUrl}${id}`, {
				method: "DELETE",
			})
				.then(() => {
					row.remove();
					alert("User deleted successfully");
				})
				.catch((error) => {
					console.error("Error:", error);
				});
		}
	}
</script>

<hr style="margin-top: 10px" />

<h2>Current Records</h2>
<table id="userTable">
	<tr>
		<th>Full Name</th>
		<th>GitHub Username</th>
		<th>Server Needed</th>
		<th>Edit</th>
		<th>Delete</th>
	</tr>
</table>

<div id="editModalBackdrop" class="modal-backdrop">
	<div id="editModal" onsubmit="submitEdit(event)" class="modal-content">
		<button id="closeModal" class="close-modal">X</button>
		<form id="editForm">
			<input type="hidden" id="editId" name="editId" />

			<label for="editGithubUsername">GitHub Username:</label>
			<input type="text" id="editGithubUsername" name="editGithubUsername" /><br /><br />

			<label for="editFullName">Full Name:</label>
			<input type="text" id="editFullName" name="editFullName" /><br /><br />

			<label>Need Server:</label>
			<input type="radio" id="editYes" name="editServerNeeded" value="Yes" />
			<label for="editYes">Yes</label>
			<input type="radio" id="editNo" name="editServerNeeded" value="No" />
			<label for="editNo">No</label><br /><br />
			<input type="submit" value="Update" />
		</form>
	</div>
</div>

<style>
	.modal-backdrop {
		display: none;
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.7);
		z-index: 1;
	}

	.modal-content {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		background: #272726;
		padding: 40px;
		z-index: 2;
	}

	.close-modal {
		position: absolute;
		top: 10px;
		right: 10px;
		cursor: pointer;
		background: none;
		border: none;
		font-size: 24px;
		color: white;
	}

	.wrapper,
	section {
		max-width: 900px;
	}
</style> explain individual aspects of code

```

### HTML Form:
- The HTML form contains input fields for capturing information about a user, such as their GitHub username, full name, password, and whether they need a server.
- It includes checkboxes and radio buttons for whether a server is needed.
There's a submit button to submit the form.
### JavaScript Functions:
fetchUsers():
- This function fetches the list of users from a specified API endpoint (apiUrl) and populates a table (userTable) with the retrieved user data.
- For each user, it adds an "Edit" and "Delete" button to their respective rows in the table.
#### submitForm(event):
- This function is called when the form is submitted.
- It prevents the default form submission behavior (event.preventDefault()) and extracts form data using FormData.
- Then, it constructs a JSON payload with the form data and sends a POST request to the API endpoint to create a new user.
- If successful, it adds the new user to the table and alerts the user of successful creation.
#### editUser(event):
- This function is called when the "Edit" button for a user is clicked.
- It extracts the user's ID from the table row, populates the edit form with the user's data, and displays the edit modal.
#### submitEdit(event):
- This function is called when the edit form is submitted.
- It prevents the default form submission behavior, extracts form data, constructs a JSON payload, and sends a PUT request to update the user's - information.
- If successful, it updates the corresponding row in the table with the edited data and alerts the user of successful update.
#### deleteUser(id, row):
- This function is called when the "Delete" button for a user is clicked.
- It prompts the user for confirmation and sends a DELETE request to the API endpoint to delete the user.
- If successful, it removes the user's row from the table and alerts the user of successful deletion.

- [Example login appearance](https://nighthawkcoders.github.io/teacher_portfolio//2024/01/08/python-jwt-login.html)
- [Backend user.py code](https://github.com/nighthawkcoders/cpt/blob/main/api/user.py#L17)
