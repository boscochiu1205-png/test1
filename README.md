#  TUT 6 Yan Cheuk Chiu
# Traffic SIM
> A fast-paced 2D traffic survival game made with **Microsoft MakeCode Arcade (Python mode)**.  
> Dodge traffic, collect stars, and survive as long as possible!  
> 🎮 [Play it live here](https://arcade.makecode.com/S32807-12175-78104-56154) 

---

## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Features](#features)
* [Screenshots](#screenshots)
* [Setup](#setup)
* [Usage](#usage)
* [Project Status](#project-status)
* [Room for Improvement](#room-for-improvement)
* [Acknowledgements](#acknowledgements)
* [Contact](#contact)

---

## General Information
- **Traffic SIM** is a reflex-based arcade game where the player must **dodge oncoming cars and collect stars** to survive.
- The goal is simple: **stay alive as long as possible** while keeping your health bar from reaching zero.  
- Each collected star adds to your score and restores a small amount of health.
- The project was created for a **MakeCode Arcade coding project**, to learn about sprite management, events, and collisions.
- It demonstrates how randomness, sprite kinds, and event-driven programming can create engaging gameplay even with simple logic.

---

## Technologies Used
- **Microsoft MakeCode Arcade** – Python mode
- **Arcade Status Bar extension**
- **Scroller extension** – for background motion
- **Built-in MakeCode Sprite & Scene APIs**

---

## Features
- Smooth **W A S D / arrow-key controls**
- **Scrolling background** to simulate movement
- **Randomised traffic spawns** with multiple vehicle types
- **Collectible stars** that heal and increase score
- **Health bar** with game-over state
- **Camera shake** feedback when hit
- **Intro sequence and countdown** before gameplay starts
- **Dynamic difficulty** – faster cars appear as score increases

---

## Screenshots
*(Add yours here once captured)*
![Gameplay Screenshot](./img/traffic-sim-gameplay.png)

---

## Setup
1. Go to [MakeCode Arcade](https://arcade.makecode.com/).  
2. Click **New Project → Python**.
3. Copy and paste the `main.py` code from this repository.
4. If using locally, ensure the following extensions are added:
   - `statusbars` (for HP bar)
   - `scroller` (for moving background)
5. Click **Play** ▶️ to test.

---

## Usage
- **Move:** W A S D or Arrow Keys  
- **Collect:** Stars to gain score + HP  
- **Avoid:** Traffic cars – each hit loses 1 HP  
- **Speed Control:**  
  - Press **←** to drive slower (background scroll −50 x)  
  - Press **→** to drive faster (background scroll −100 x)

**Gameplay Objective:**  
Survive as long as possible, keep your HP above 0, and try to beat your high score!

---

## Project Status
Project is: _complete_ ✅ (with room for polish).  
Future updates may add improved visuals, sound effects, and new difficulty levels.

---

## Room for Improvement
**Possible Enhancements:**
- Add background music and sound effects.
- Introduce traffic lanes or random direction cars.
- Implement a leaderboard (store high scores).
- Add new obstacle types after higher scores.

**To Do:**
- [ ] Add “hard mode” cars at score ≥ 10  
- [ ] Include visual effects when player speeds up  
- [ ] Create menu + restart screen  

---

## Acknowledgements
- Inspired by classic endless runner and dodging games.  
- Built using **Microsoft MakeCode Arcade**’s Python engine.  
- Special thanks to the MakeCode community tutorials on sprite collisions and scrolling backgrounds.

---

## Contact
Created by **[Yan Cheuk Chiu]  
---

<!--
## License
This project is open source and available under the MIT License.
-->


#LINK:
https://arcade.makecode.com/S32807-12175-78104-56154 
