---
toc: true
comments: true
layout: post
title: Individual review
description: Individual review
courses: { compsci: {week: 17} }
type: tangibles
---

# Individual Final

## What is our Project:
We created a music streaming software replicating Spotify. As more people are creating and listening to music now than ever, other big companies are just wanting to make money with ill intetions towards their users. Our goal was to create a platform that allowed people to stream their own music, create and upload their own music; add music to a liked playlist, and more. It cuts out bigger companies that just want to make money. 

## My Feature
1. **Reply**
    - My feature was to create an SQLite DB that housed both users, the songs, and each users liked songs. We wanted the DB to be open to independent and individual CRUD features on each DB. 
    - In addition to creating the backend DB, I created both our frontend and backend code for the login page. We wanted to make sure that only registered users are allwoed to stream music. 


## Code + CPT Requirements added.

| Requirement | Code/Work |
|-------------|-----------|
| Instructions for input from one of the following: the user, a device, an online data stream, a file. (Ours will take input from a user) | Our project allows users to upload data or use the upladed data to add them to a liked playlist that is shown on the main dashboard. |
| Use of at least one list (or other collection type) to represent a collection of data that is stored and used to manage program complexity and help fulfill the program’s purpose | Our information is stored into the backend repository where every song that is sent is uploaded into the SQLite DB. This is useful for us as a user will be able to listen to a previously listened song|

| <img src="https://i.ibb.co/8cdbpFG/Screenshot-2024-02-28-at-9-53-03-PM.png" width = 800> | ![image 2](https://i.ibb.co/BBQwjDT/Screenshot-2024-02-28-at-9-54-50-PM.png) |
|:---:|:---:|
| SQLite DB containing all the users | SQLite DB containing all the songs |


| An algorithm that includes sequencing, selection, and iteration that is in the body of the selected procedure | The create method sequentially adds the current instance to the database session, commits the changes to the database, and returns the current instance, facilitating the persistence of the object in the database. 

| <img src="https://github.com/aashrayr/student2/assets/68722712/aec42345-95a0-40fd-a6ac-7d135e3c73be" alt="image" width="800">|

### Code of what I did: 

| Frontend Calling Login CRUD Function (User) | Corresponding Login CRUD Backend Function (User) |
|:---:|:---:|
| <img src="https://i.ibb.co/X8wW5Y3/Screenshot-2024-02-28-at-10-10-02-PM.png" width = 800> | ![image 2](https://i.ibb.co/tbpZf8n/Screenshot-2024-02-28-at-10-09-29-PM.png) |

| Frontend Calling Read CRUD Function (songs) | Corresponding Read CRUD Backend Function (song) |
|:---:|:---:|
| <img src="https://i.ibb.co/vjLSTBm/Screenshot-2024-02-28-at-10-13-41-PM.png" width = 800> | ![image 2](https://i.ibb.co/hcGKyvt/Screenshot-2024-02-28-at-10-14-05-PM.png) |

| Frontend Calling Delete CRUD Function (User) | Corresponding Delete CRUD Backend Function (User) |
|:---:|:---:|
| <img src="https://i.ibb.co/pLwbJxg/Screenshot-2024-02-28-at-10-17-08-PM.png" width = 800> | ![image 2](https://i.ibb.co/TPrjDqB/Screenshot-2024-02-28-at-10-16-45-PM.png) |

| Instructions for output (tactile, audible, visual, or ) based on input and program functionality | Fetch function that eventually displays the reply into the main dashboard. 

## Component B: Video.

[My Video](https://drive.google.com/file/d/1PPLb68riJv86Rz_7mVDVptTQm4ahSi0F/view?usp=sharing)

| Requirement | Video |
|------------------|------------------|
| Input to program  | Seen in video, sending reply and message  |
| At least one aspect of the functionality of your program | The ability for the reply feature to be able to be seen by all users, and shows up as its own message.  |
| Output produced by program:  | New Reply message shown underneath the original  |
| My video does not have: | Any voice/audio, and in detail information  |
| My video is | A .mp4, under 1 minute, and under 30mb.  |