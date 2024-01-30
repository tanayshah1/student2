---
layout: post
title: Edit Users
description: Edit user information in the database.
permalink: /edit-users
type: tangibles
#courses: { compsci: {week: 13} }
hide: true
---

# Edit Users

This page allows you to edit user information in the database. Please make sure you are authorized before making any changes.

## User List

<!-- HTML table layout for user list. The table will be filled by JavaScript below. -->
<table>
  <thead>
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Age</th>
      <th>Action</th>
    </tr>
  </thead>
  <tbody id="userList">
    <!-- JavaScript generated user list -->
  </tbody>
</table>

## Edit User

<!-- Form for editing user information -->
<form id="editUserForm">
  <label for="userId">User ID:</label>
  <input type="text" id="userId" name="userId" required>

  <label for="userName">Name:</label>
  <input type="text" id="userName" name="userName" required>

  <label for="userAge">Age:</label>
  <input type="number" id="userAge" name="userAge" required>

  <button type="submit">Save Changes</button>
</form>

<!-- JavaScript code for fetching and displaying user list -->
<script type="module">
  // Import URI and options from your configuration file
  import { uri, options } from '{{site.baseurl}}/assets/js/api/config.js';

  // Set Users endpoint (list of users)
  const userListUrl = uri + '/api/users/';

  // Set Edit User endpoint
  const editUserUrl = uri + '/api/edit-user/';

  // Prepare HTML container for user list
  const userListContainer = document.getElementById("userList");

  // Fetch user list from the API
  fetch(userListUrl, options)
    .then(response => {
      if (response.status !== 200) {
        console.error('Error fetching user list:', response.status);
        return;
      }
      return response.json();
    })
    .then(users => {
      for (const user of users) {
        const tr = document.createElement("tr");
        tr.innerHTML = `<td>${user.uid}</td><td>${user.name}</td><td>${user.age}</td><td><button onclick="editUser(${user.uid})">Edit</button></td>`;
        userListContainer.appendChild(tr);
      }
    })
    .catch(error => console.error('Error fetching user list:', error));

  // Function to handle user editing
  function editUser(userId) {
    // Fetch user details for the selected user
    fetch(`${editUserUrl}${userId}`, options)
      .then(response => {
        if (response.status !== 200) {
          console.error('Error fetching user details:', response.status);
          return;
        }
        return response.json();
      })
      .then(userDetails => {
        // Populate the edit form with user details
        document.getElementById("userId").value = userDetails.uid;
        document.getElementById("userName").value = userDetails.name;
        document.getElementById("userAge").value = userDetails.age;
      })
      .catch(error => console.error('Error fetching user details:', error));
  }

  // Function to handle form submission (updating user information)
  document.getElementById("editUserForm").addEventListener("submit", function (event) {
    event.preventDefault();

    const formData = new FormData(this);

    // Perform the update request to the API
    fetch(editUserUrl, {
      method: 'PUT',
      headers: {
        'Content-Type': 'application/json',
        'Authorization': `Bearer ${getAuthToken()}`
      },
      body: JSON.stringify({
        userId: formData.get("userId"),
        userName: formData.get("userName"),
        userAge: formData.get("userAge")
      })
    })
      .then(response => {
        if (response.status === 200) {
          console.log('User information updated successfully');
          // Optionally, you can update the displayed user list or show a success message
        } else {
          console.error('Error updating user information:', response.status);
          // Optionally, you can show an error message
        }
      })
      .catch(error => console.error('Error updating user information:', error));
  });

  // Function to get the authentication token from cookies
  function getAuthToken() {
    return document.cookie.replace(/(?:(?:^|.*;\s*)jwt\s*=\s*([^;]*).*$)|^.*$/, "$1");
  }
</script>
