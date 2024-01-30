---
comments: True
layout: post
toc: false
title: Delete Account
permalink: /delete
description: This page will delete an account 
type: hacks
#courses: { compsci: {week: 13} }
---

<style>
 .delete-container {
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
<div class="delete-container">

<form action="javascript:delete_user()">
    <label for="uid"><b>Username</b></label>
    <input type="text" id="uid" placeholder="Enter Username" name="uid" required>
    <label for="password"><b>Password</b></label>
    <input type="password" id="password" placeholder="Enter Password" name="password" required>
    <button class='button'>Delete Account</button>
    <div>


<script type="module">
    import { uri, options } from '{{site.baseurl}}/assets/js/api/config.js';
    function delete_user() {
        var myHeaders = new Headers();
        myHeaders.append("Content-Type", "application/json");
        const url = uri + '/api/users/delete';
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
                return null;
            }
            const contentType = response.headers.get('Content-Type');
            if (contentType && contentType.includes('application/json')) {
                return response.json();
            } else {
                return response.text();
            }
        })
        .then(data => {
            if (data !== null) {
                console.log('Response:', data);
            }
            window.location.href = "{{site.baseurl}}/data/database";
        })
        .catch(err => {
            console.error('Fetch error:', err);
        });
    }
    window.delete_user = delete_user;

</script>