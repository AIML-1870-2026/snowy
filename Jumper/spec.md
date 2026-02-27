# Jumper

## Overview
An endless runner game set in the jungle. The player controls a monkey who must jump over snakes to survive as long as possible while collecting bananas for points.

## Theme
- **Setting:** Jungle environment
- **Player Character:** Monkey
- **Obstacles:** Snakes on the ground
- **Collectibles:** Bananas

## Gameplay
- The monkey runs automatically from left to right
- Snakes appear on the ground at random intervals
- The player must time their jumps to avoid the snakes
- Bananas appear sporadically throughout the game
  - **Ground bananas:** Can be collected while running
  - **Air bananas:** Can only be collected by jumping
- Collecting bananas increases the player's score
- The game ends when the monkey collides with a snake
- Base score increases the longer the player survives

## Controls
- **Spacebar:** Jump

## Sound Effects
- **Jump:** Audio plays when the monkey jumps

## Difficulty Progression
- Game starts at a base speed and spawn rate
- Every 10 seconds, difficulty increases:
  - Game speed increases slightly
  - Snake spawn frequency increases
  - Snake movement speed increases
- Visual or audio cue when difficulty increases (optional)
- No maximum difficulty cap (true endless challenge)

## High Score Persistence
- High score saved to browser localStorage
- High score displayed on start screen and game over screen
- New high score celebration when beaten
- High score persists between browser sessions

## Animations
- **Running:** Monkey running animation while on ground
- **Jumping:** Monkey jump animation while airborne
- **Death:** Monkey falls and collapses onto the ground when hitting a snake

## Pattern Library Chunks

### 1. Game Canvas
The main canvas element and rendering context setup for drawing all game elements.

### 2. Game Loop
The core update/render cycle using `requestAnimationFrame` that drives the game at 60fps.

### 3. Player Character (Monkey)
The player object with properties for position, velocity, dimensions, and state (running, jumping, dead).

### 4. Jump Mechanics
Handles spacebar input, applies upward velocity, and uses gravity to bring the player back down.

### 5. Ground & Scrolling Background
Parallax scrolling jungle background layers that create the illusion of movement.

### 6. Obstacle Spawner (Snakes)
Randomly generates snake obstacles at intervals, with increasing frequency over time.

### 7. Collectible Spawner (Bananas)
Spawns bananas at random positions - some on ground level, some in the air requiring jumps.

### 8. Collision Detection
Rectangle-based collision checking between the monkey and snakes (death) or bananas (collect).

### 9. Score System
Tracks and displays points from survival time and banana collection with UI overlay.

### 10. Game State Manager
Handles game states: start screen, playing, game over. Controls transitions and restart logic.

### 11. Audio Manager
Handles loading and playing sound effects (jump sound) using the Web Audio API or HTML5 Audio.

### 12. Difficulty Manager
Tracks elapsed time, calculates current difficulty level, and adjusts game speed and spawn rates.

### 13. High Score Manager
Reads/writes high score to localStorage, compares current score, and triggers celebration on new records.

## Technical Requirements
- Single HTML file with embedded CSS and JavaScript
- No external dependencies required
- Smooth animations for running, jumping, and death
- Collision detection between monkey and snakes
- Collision detection between monkey and bananas
- localStorage for high score persistence
- Web Audio API or HTML5 Audio for sound effects

## Features
- Endless scrolling jungle background
- Increasing difficulty over time (faster snakes, more frequent spawns)
- Score tracking (time survived + bananas collected)
- High score saved locally and displayed
- Jump sound effect
- Game over screen with final score, high score, and restart option
