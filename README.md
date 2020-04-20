
![Cover](Assets/readme/cover.png)

---

![optimized](https://user-images.githubusercontent.com/6860637/79353473-60ad7580-7f3b-11ea-8bc7-411bab23032e.gif)

---

## Table of Contents

- [Godot 3.2.1 - Tutorial - Creating a mobile game](#godot-321---tutorial---creating-a-mobile-game)
  - [Where are the tutorials?](#where-are-the-tutorials)
  - [Branches: `master`, `develop` and `video`](#branches-master-develop-and-video)
  - [Prerequisites](#prerequisites)
  - [Contents](#contents)
    - [1. Introduction](#1-introduction)
    - [2. Configure Godot and Android SDK](#2-configure-godot-and-android-sdk)
    - [3. Testing performances on the smartphone](#3-testing-performances-on-the-smartphone)
    - [4. Touchscreen input with `_input()` and `InputEvents`](#4-touchscreen-input-with-input-and-inputevents)
    - [5. Creating a game level](#5-creating-a-game-level)
    - [6. Projectile & Enemies](#6-projectile--enemies)
    - [7. Implementing the `Slingshot`](#7-implementing-the-slingshot)
    - [8. Calculating and drawing the trajectory](#8-calculating-and-drawing-the-trajectory)
    - [9. Obstacles](#9-obstacles)
    - [10. Score system & Obstacles](#10-score-system--obstacles)
    - [11. TODO - Camera](#11-todo---camera)
    - [12. TODO - Debugging a mobile App](#12-todo---debugging-a-mobile-app)
    - [13. TODO - Possible game improvements](#13-todo---possible-game-improvements)
  - [What now?](#what-now)
  - [Credits](#credits)
  - [Thanks](#thanks)
  - [Support me](#support-me)

# Godot 3.2.1 - Tutorial - Creating a mobile game

This repository contains a work in progress game inspidred by **Angry Birds**, reimplemented with Godot Engine 3.2.1.

Source code is MIT licensed. Feel free to read it, modify it and reuse it in your projects.

## Where are the tutorials?

- 🎥 [Video tutorial playlist](https://www.youtube.com/playlist?list=PLaCq3HqKQR6rNyqulBsbca-6wzxp8H52r)

Source code and comments are in English. *Commentary is in Italian.*

## Branches: `master`, `develop` and `video`
- `develop` branch contains the complete project. I do experiments in here. It may be unstable.
- `master` branch will be in sync with video tutorials releases on my YouTube channel.
- `videoX/start` branches contains the code to follow the tutorial number `X`. Example:
  - `video5/start` contains the code to follow the [video tutorial 5](https://youtu.be/SVuOYKzTwxw) on YouTube.

## Prerequisites

The tutorials require basic Godot understanding about Scenes, GDScript, 2D Nodes such as Sprite2D, CollisionShape2D, Area2D.

You can learn these topics by:

- reading the [official documentation](https://docs.godotengine.org/en/3.1/getting_started/step_by_step/intro_to_the_editor_interface.html)
- following my [video tutorial series](https://www.youtube.com/watch?v=AY1zuH2mHQ0&list=PLaCq3HqKQR6rlPpf2GAOXp52ddt0V71Yl) on Godot 3 basics (*only in Italian*)

## Contents

### 1. Introduction

- 🎥 [YouTube - 1. Introduzione](https://youtu.be/x0emyyXC_sM)

This tutorial series will focus on creating a simple mobile game
using Godot 3.2.

I choose to make an Angry Birds clone because:

1. it is short to recreate (without adding polish) 
2. it allows to stress Godot performances on the worst case scenario: intense game (physics based) on a low-power device (smartphone)

I'm creating this tutorials using Manjaro Linux (Arch Linux derivative), but similar steps can be done on other operating systems as well.

Currently I don't have an Apple device and I cannot develop/test iOS/OSX games. I'll try to provide instructions for other OS, but help here is really appreciated (especially if you are a Debian, Ubuntu, Windows or OSX user).

### 2. Configure Godot and Android SDK

- 🎥 [YouTube - 2. Configurare Linux](https://youtu.be/xFia7zG8NGA)
- 🎥 [YouTube - 3. Configurare Windows](https://youtu.be/PNj8YmXjj-A)
  
> How do I configure my computer for Android development?

- Install `android-tools` and `jdk-openjdk`
- Create debug keystore
- Configure Godot
- Download export templates
- **Create the first APK**
  - Install the APK manually from the phone
  - Install the APK from command line using `adb`
  - Install the APK from Godot with one click
- Export a simple scene to the device

### 3. Testing performances on the smartphone

- 🎥 [YouTube - 4. Creare il livello](https://youtu.be/VZS0pv14--s)
- 🎥 [YouTube - 5. Creare la scena StressTest (pt1)](https://youtu.be/SVuOYKzTwxw)
- 🎥 [YouTube - 6. Stress test (pt.2) - Debugger e profiler](https://youtu.be/s4jSWPtqR8M)

![Stress test scene screen](Assets/readme/stress-test.png)

> If we include all the physics elements and we create hundreds of game objects, is the game playable?

1. Create a stress test scene
2. Add background sprites, tilemap
3. Add physics objects: enemies, static bodies, rigid bodies
4. Create an object spawner script 
5. Use debugger and profiler to check game performances

### 4. Touchscreen input with `_input()` and `InputEvents`

- Detect the touch position
- Detect drag
- Detect release
- Difference between `_input()` and `on_<CollisionObject2D>_input_event()` ?
- Simulate touch with mouse for faster development
  - `pointing/emulate_touch_from_mouse=true`
  - `pointing/emulate_mouse_from_touch=false`

### 5. Creating a game level

![Image level screen](Assets/readme/level.png)

- `TileMap`, background and collisions
- Layout for mobile games
- Taking multiple resolutions into account
- How to force landscape/portrait

### 6. Projectile & Enemies

- Game objects with `Sprite`, `RigidBody` and `CollisionShape`
- Basic Physics concepts
- Mass, gravity and Godot Physics

### 7. Implementing the `Slingshot`

- Grab mechanig
  - Skeleton Mesh deform?
- Elastic force
- Take the Projectile as input with `export` keyword
- Launch the projectile

### 8. Calculating and drawing the trajectory

- Create a `TrajectoryDrawer` node
- Basic Physics concepts
- Measurement unit, velocity, impulse vs force
  -  https://en.wikipedia.org/wiki/Impulse_(physics)
- Projectile motion
- `_draw` method
- Is the trajectory correct?
  - Set the correct damping factor

### 9. Obstacles

- Create an obstacle
- Add obstacles to the level
- Implement obstacle destruction

### 10. Score system & Obstacles 

- Scores
  - https://www.macobserver.com/tmo/article/angry_birds_the_all-purpose_guide_to_three_stars_part_1
- Detect when the game is over
- Create and show end-game screen

### 11. TODO - Camera 

- Camera pan across the level
- Pinch to zoom?
  
### 12. TODO - Debugging a mobile App

> How to debug errors and performances on a mobile device?

- Remote debugger
- https://stackoverflow.com/questions/6854127/filter-logcat-to-get-only-the-messages-from-my-application-in-android

### 13. TODO - Possible game improvements

- Add audio sfx
- Improve the slingshot
- Particles, debris

## What now?

This tutorial covers only a small subset of mobile game development topics.

There are a lot of areas that can be explored, like:

- Deploying on Google Play Store
- Responsive layout
- Responsive gameplay
- Double tap, drag 'n drop, panning, pinch to zoom,...
- Using Sensors (GPS, accelerometer, light sensor, ...). Godot Android module, Java Singleton
- Bluetooth
- ...

Some of these topics may be covered on [my YouTube channel](https://www.youtube.com/c/CrystalBit)
as separated videos.

Keep an eye on the [Crystal Bit Github organization](https://github.com/crystal-bit) as well, because
all the source code for my tutorials will be uploaded here.

## Credits

- **Kenney** for most of the game assets - https://www.kenney.nl/
- **Hanabi** for the slingshot sprites

## Thanks

- My community for the support on YouTube, Telegram and in person 🙋
- Gameloop.it community for the Harvard [CS50 gamedev course](https://github.com/GameLoop-it/cs50_course_materials)
- [YouAreUto](http://youareuto.com/) game & team - My first mobile game as a freelance game developer
- Godot Engine community for the excellent documentation and software 
- [Godot Engine Italia](https://godotengineitalia.com/) 🍕

## Support me

I love creating free game projects and tutorials. If you want to help me, I really appreciate! You can:

- Star this repository
- Test the game and report issues
- Open PRs (please get in touch before)
- Retweet the project
- Talk to your friends about this project

Right now I don't have any donation page setup. If you are considering this, feel free to reach me out on vitrumbit@gmail.com
