---
comments: true
layout: post
toc: false
title: Login
permalink: /login
description: Login to the database
type: hacks
courses: { compsci: { week: 13 } }
---

<style>
 .login-container {
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
<div class="login-container">

<form action="javascript:login_user()">
    <label for="uid"><b>Username</b></label>
    <input type="text" id="uid" placeholder="Enter Username" name="uid" required>
    <label for="password"><b>Password</b></label>
    <input type="password" id="password" placeholder="Enter Password" name="password" required>
    <button class='button'>Log in</button>
    <div>
    <span class="psw">Need an account? <a href="{{site.baseurl}}/newUser">  Sign Up</a></span>
    </div>

</form>
<script type="module">
    import { uri, options } from '{{site.baseurl}}/assets/js/api/config.js';
    function login_user(){
      var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
        const url = uri + '/api/users/authenticate';
        const body = {
            uid: document.getElementById("uid").value,
            password: document.getElementById("password").value,
        };
        const authOptions = { 
            method: 'POST', 
            cache: 'no-cache',
            headers: myHeaders,
            body: JSON.stringify(body)
        };
        fetch(url, authOptions)
        .then(response => {
            if (!response.ok) {
                const errorMsg = 'Login error: ' + response.status;
                console.log(errorMsg);
                return;
            }
            window.location.href = "data/database";
        })
        .catch(err => {
            console.error(err);
        });
    }
    window.login_user = login_user;
</script>