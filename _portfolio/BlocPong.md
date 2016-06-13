---
layout: post
title: Bloc Pong
short-description: Bloc Pong is a pong replica created using javascript and the HTML5 canvas element.

---

## Summary

Bloc pong was an assignment I chose to do for my Bloc.io Frontend course. It uses javascript and the HTML5 canvas element for all the animation and game logic. This project provided me with my first opportunity to write a complex javascript program that didn't rely on frameworks to exist and provide core functionality.

## Explanation

As part of the Bloc.io course I was given numerous assignments to choose from. While working on the frontend section of the course I completed a few assigments who's primary focus was using Angular to create frontend apps. I chose to do the Pong project because it required me to create more of the program from the ground up, and not have to work within a rigid framework. The goal of the assignment was to create Pong in the browser using the HTML5 canvas element. 

## Problem

The primary challenge when writing this was my lack of familiarity with javascript and how HTML5 and the canvas element work. I would need to research how the canvas element and context worked as well as gain a clear conceptual understanding of Pong. This meant gaining an understanding of rendering shapes, tracking shape position, resolving collisions, moving shapes on user input, and implementing basic AI.

## Solution

My lack of experience became apparent almost immediately as I couldn't get the canvas element to display on the screen. Inspecting the page in the browser revealed that while the canvas element was showing up on the final page, it wasn't being rendered. I realized that setting the canvas size in the CSS file instead of on the HTML element caused javascript to assume a default size for it that caused the canvas to render off the screen. That was fixed by adding the height and width to the HTML tag for the canvas element and removing it from the CSS properties for the canvas. I also had an issue making the paddles move in response to player input, with the paddles movement being too jerky and slow. This turned out to be caused by improperly using the event listener. Initially I had it set up so that when the event listener fired the paddle position would be updated immediately. This caused player input to have a lag as the rendering function wasn't checking to see if the player moved each frame. This was fixed by creating a hash variable that mapped each input key to a boolean and changed based on keyup and keydown events. By using a variable instead of directly changing the position the render function was able to accurately detect whether the paddle position was fixed or moving on each frame.

## Results