# Snake Game Specification

## Overview
A classic Snake game with a twist: the snake hunts mice while navigating around obstacles. Built with HTML, CSS, and JavaScript in a single file.

## Core Gameplay

### The Snake
- Starts as a small snake (3 segments) in the center of the play area
- Moves continuously in the current direction
- Controlled via arrow keys or WASD
- Grows by one segment each time it eats a mouse
- Dies on collision with walls, obstacles, or itself

### The Mice
- One mouse appears on the board at a time
- Spawns in a random empty cell (not on snake, obstacles, or walls)
- Each mouse eaten awards points and grows the snake
- New mouse spawns immediately after one is eaten

### Obstacles
- Static obstacles placed on the board
- Snake dies on collision with any obstacle
- Obstacles increase in number as the player progresses
- New obstacles appear at score thresholds (e.g., every 50 points)

## Visual Design

### Game Board
- Grid-based play area (20x20 cells recommended)
- Clear visual boundary/walls
- Subtle grid lines or checkered pattern for spatial reference

### Snake Appearance
- Distinct head segment (eyes or directional indicator)
- Body segments with slight color gradient (darker toward tail)
- Smooth or pointed tail segment

### Mouse Appearance
- Small, recognizable mouse icon or shape
- Subtle idle animation (wiggle or twitch)
- Visual feedback when eaten (small particle burst)

### Obstacles
- Visually distinct from snake and mice
- Could be rocks, blocks, or themed hazards
- Clear contrast against the background

## Game States

### Start Screen
- Game title
- "Press SPACE to Start" prompt
- High score display (if any)

### Playing
- Active game board
- Current score display
- Current level/difficulty indicator

### Paused
- "PAUSED" overlay
- Press SPACE or P to resume

### Game Over
- "GAME OVER" message
- Final score display
- High score update notification (if applicable)
- "Press SPACE to Restart" prompt

## Controls

| Key | Action |
|-----|--------|
| Arrow Keys | Change direction |
| WASD | Change direction (alternative) |
| SPACE | Start / Restart |
| P | Pause / Resume |

## Scoring

- Each mouse eaten: **10 points**
- Bonus points for speed (optional): faster difficulty = higher multiplier
- High score saved to localStorage

## Difficulty Progression

| Level | Score Threshold | Snake Speed | Obstacles |
|-------|-----------------|-------------|-----------|
| 1 | 0 | Slow | 0 |
| 2 | 50 | Medium | 3 |
| 3 | 100 | Medium | 5 |
| 4 | 200 | Fast | 7 |
| 5+ | 300+ | Fast | 10+ |

## Technical Requirements

### Single File Structure
- All HTML, CSS, and JavaScript in one `index.html` file
- No external dependencies or libraries
- No images required (use CSS shapes, emojis, or canvas drawing)

### Rendering
- Canvas-based rendering recommended for smooth animation
- Alternatively, DOM-based grid with CSS styling

### Game Loop
- Consistent tick rate with `requestAnimationFrame` or `setInterval`
- Speed controlled by tick interval (faster = shorter interval)

### Local Storage
- Persist high score between sessions
- Key: `snakeGameHighScore`

## Optional Enhancements

These can be added if time permits:

- [ ] Sound effects (eat, die, level up)
- [ ] Screen shake on collision
- [ ] Snake color/skin selection
- [ ] Multiple mice at higher levels
- [ ] "Golden mouse" worth bonus points (rare spawn)
- [ ] Particle effects on eating
- [ ] Mobile touch controls

## File Structure

```
Assignment-05/
├── index.html    (complete game)
└── spec.md       (this file)
```
