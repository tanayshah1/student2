---
comments: true
layout: post
toc: false
title: Team Review 
description: Our final thoughts
type: hacks
courses: { compsci: { week: 13 } }
---

Our Team's idea for the CPT was to recreate spotify to learn skills that are applicable to the real world, and in a working product. We wanted to get the biggest feature of spotify, the playing songs feature, to work, and hoped to add in a few of our own kicks to the project.



## What Everyone Did:

Shubhay: Worked on a mixture of Front and Bakend. On the Frontend he developed the dynamic javascript and making the website resemble spotify. The Dynamics worked to reflexivly map through the lists of songs to make creating new songs easy. On the backend he devloped his portion of the songs model and api. Which was used to gain a list of songs, images, and song links that the API could map through.

Tanvi: Worked on playing the songs. By developing the stucture of the songs database, she was able to get the song links to work properly and fetched them onto the frontend using their respective ID's. By developing the second half of the songs api, which was the /api/songs/[id] page we were able to individually grab the songs ID and play them when needed. Finnaly on the individual songs pages she grabbed the indivdual data of the song, and used it to create a play button that plays or stops the song depending on the user.


Tanay: Worked on the login page and frontend animations. On the frontend he made all the pages properly link together and used javascript to automatically pagnate the songs depending on how many songs their were. He used javascript to design all of the animations when clicking the songs. On the backend he developed the entire login functionality, and used it to spur future functionalities like liking and creating.

Pranavi: Worked on the songs individualistic pages, and the create function. Using a mix of javascript, and python she made it so when clicking on a song it automatically created a new web page with only that songs details being used. By using the songs indivdual id's and the /api/song/[id] page the songs were able to indivually display themselves, and grabbed all the neccsary data. On the create function she made a form that users can fill and it posts to the songs database. 



# Feature Description:


**Spotify Clone Features:**

1. **Dynamic Frontend Development:**
- Implemented dynamic JavaScript for a Spotify-like user interface.
- Enabled reflexive mapping through song lists, simplifying new song additions.
- Contributed to the frontend design for a visually appealing resemblance to Spotify.

2. **Songs Database and Playback:**
- Structured the songs database for proper song link functionality.
- Developed the /api/songs/[id] endpoint for individual song retrieval.
- Created pages for individual songs with play and pause functionality.

3. **Login Page and Frontend Animations:**
- Linked all pages for seamless navigation.
- Dynamically paginated song lists based on quantity.
- Designed frontend animations for an enhanced user interaction.
- Spearheaded backend development of the login functionality.

4. **Individualistic Song Pages and Create Functionality:**
- Implemented individual representation of songs using JavaScript and Python.
- Automatically generated dedicated web pages for each song using unique IDs and /api/song/[id].
- Introduced a creation function allowing users to fill out a form for easy song additions to the database.
