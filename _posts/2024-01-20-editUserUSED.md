---
comments: True
layout: post
title: Edit User
description: cooking
#courses: { compsci: {week: 13} }
type: tangibles
permalink: /editUser
hide: true
---

<style>
 .edit-container {
  border: 1px solid #c0e56b;
  max-width: 400px;
  margin: 0 auto;
  padding: 16px;
  text-align: center;
}

.input-container {
  text-align: center; /* Center the text within the input boxes */
}

input[type=text], input[type=password] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

button {
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
}

span.psw {
  display: block;
  text-align: center;
  margin: 16px 0;
}

@media screen and (max-width: 300px) {
  span.psw {
    display: block;
    float: none;
  }
  .cancelbtn {
    width: 100%;
  }
}

</style>


<div class="edit-container">
    <form id="username" action="javascript:edit_user()">
        <p><label>
            User Name:
            <input class="userInput" type="text" name="name" id="uid" required>
        </label></p>
        <p><label>
            Name:
            <input class="userInput" type="text" id="name" required>
        </label></p>
        <p><label>
            Password:
            <input class="userInput" type="text" id="password" required>
        </label></p>
        <p><label>
            Date of Birth:
            <input class="userInput" type="text" id="dob" required>
        </label></p>
        <p><label>
            Email:
            <input class="userInput" type="text" id="email" required>
        </label></p>
        <p>
            <button onclick="edit_user()">Submit</button>
        </p>
    </form>
</div>


<!-- 
Below JavaScript code is designed to handle user authentication in a web application. It's written to work with a backend server that uses JWT (JSON Web Tokens) for authentication.

The script defines a function when the page loads. This function is triggered when the Login button in the HTML form above is pressed. 
 -->
<script type="module">
    // uri variable and options object are obtained from config.js
    import { uri, options } from '{{site.baseurl}}/assets/js/api/config.js';
    
    function edit_user(){
        // Set Authenticate endpoint
        const url = uri + '/api/users/update';

        // Set the body of the request to include login data from the DOM
        const body = {
            uid: document.getElementById("uid").value,
            name: document.getElementById("name").value,
            password: document.getElementById("password").value,
            dob: document.getElementById("dob").value,
            email: document.getElementById("email").value,
        };

        // Change options according to Authentication requirements
        const authOptions = {
            ...options, // This will copy all properties from options
            method: 'PUT', // Override the method property
            cache: 'no-cache', // Set the cache property
            headers: {
                'Content-Type': 'application/json', // Example header
                'uid': localStorage.getItem('uid') // Set the uid as a header
            },
            body: JSON.stringify(body),
        };

        console.log(url);
        console.log(authOptions);
        console.log(body);
        // Fetch JWT
        fetch(url, authOptions)
        .then(response => {
            // handle error response from Web API
            if (!response.ok) {
                const errorMsg = 'Edit User error: ' + response.status;
                console.log(errorMsg);
                return;
            }
            window.location.href = "{{site.baseurl}}/data/database";
        })
        // catch fetch errors (ie ACCESS to server blocked)
        .catch(err => {
            console.error(err);
        });
    }

    // Attach login_user to the window object, allowing access to form action
    window.edit_user = edit_user;
</script>