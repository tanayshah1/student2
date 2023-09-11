---
toc: true
comments: true
layout: post
title: Snake Game
description: A Snake Game I coded using CSS, HTML, and JavaScript
courses: { compsci: {week: 1} }
type: hacks
---

# Snake Game

This is a snake game. Move the green square around with either the either keys or WASD keys. Try and eat the red apples that randomly spawn. I am currently working on add a counter/score keeper and making it closer to real snake game like on Google. 

<div id="container">
    <div id="game-container">
        <div id="snake" style="left: 0; top: 0;"></div>
        <div id="apple" style="left: 80px; top: 80px;"></div>
    </div>
</div>

<style>
    #container {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }

    #game-container {
        width: 400px;
        height: 400px;
        border: 1px solid #ccc;
        position: relative;
    }

    #snake {
        width: 40px;
        height: 40px;
        background-color: green;
        position: absolute;
    }

    #apple {
        width: 40px;
        height: 40px;
        background-color: red;
        position: absolute;
    }
</style>

<script>
    let snake = document.getElementById('snake');
    let apple = document.getElementById('apple');
    let x = 0;
    let y = 0;
    let appleX = 80;
    let appleY = 80;

    function updateSnakePosition() {
        snake.style.left = x + 'px';
        snake.style.top = y + 'px';
    }

    function updateApplePosition() {
        apple.style.left = appleX + 'px';
        apple.style.top = appleY + 'px';
    }

    function randomPosition() {
        appleX = Math.floor(Math.random() * 10) * 40;
        appleY = Math.floor(Math.random() * 10) * 40;
    }

    document.addEventListener('keydown', (event) => {
        switch (event.key) {
            case 'ArrowUp':
            case 'w':
                if (y > 0) y -= 40;
                break;
            case 'ArrowDown':
            case 's':
                if (y < 360) y += 40;
                break;
            case 'ArrowLeft':
            case 'a':
                if (x > 0) x -= 40;
                break;
            case 'ArrowRight':
            case 'd':
                if (x < 360) x += 40;
                break;
        }

        // Check for collision with the apple
        if (x === appleX && y === appleY) {
            randomPosition();
            updateApplePosition();
        }

        updateSnakePosition();
    });

    // Initialize the apple's position
    randomPosition();
    updateApplePosition();
</script>

