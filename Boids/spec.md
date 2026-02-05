# Boids Ant Colony Simulation

## Overview
An interactive webpage that simulates flocking behavior using Craig Reynolds' Boids algorithm. The boids are visualized as ants, creating the appearance of an ant colony moving in coordinated patterns.

## Core Behaviors

### 1. Separation
- Boids steer away from nearby flockmates to avoid crowding
- Prevents collisions between individual ants
- Weight controllable by user (0 to 5)

### 2. Alignment
- Boids steer toward the average heading of nearby flockmates
- Creates coordinated movement direction
- Weight controllable by user (0 to 5)

### 3. Cohesion
- Boids steer toward the average position of nearby flockmates
- Keeps the flock together as a group
- Weight controllable by user (0 to 5)

## Visual Design

### Ant Appearance
- Body: Three connected ovals (head, thorax, abdomen)
- Color: Dark brown/black (#2d1b0e or similar)
- Antennae: Two thin lines extending from the head
- Legs: Six small lines (3 per side) on the thorax
- Size: Approximately 10-15 pixels in length
- Rotation: Ant faces the direction of movement

### Canvas
- Full viewport size
- Background: Light tan/sand color (#f4e4bc) to simulate ground/dirt
- Subtle texture or gradient optional

## User Controls

### Control Panel
- Position: Fixed panel on the left or right side
- Style: Semi-transparent, minimal design
- Collapsible on mobile

### Sliders

| Control | Range | Default | Step |
|---------|-------|---------|------|
| Separation | 0 - 5 | 1.5 | 0.1 |
| Alignment | 0 - 5 | 1.0 | 0.1 |
| Cohesion | 0 - 5 | 1.0 | 0.1 |
| Neighbor Radius | 20 - 200 | 50 | 5 |
| Boid Count | 10 - 500 | 100 | 10 |

### Additional Controls
- Reset button: Returns all values to defaults
- Pause/Play button: Toggles simulation

## Technical Specifications

### Boid Properties
```
position: { x, y }
velocity: { x, y }
acceleration: { x, y }
maxSpeed: 4
maxForce: 0.1
```

### Simulation Loop
1. For each boid:
   - Find neighbors within radius
   - Calculate separation force
   - Calculate alignment force
   - Calculate cohesion force
   - Apply weights to each force
   - Update acceleration
   - Update velocity (clamp to maxSpeed)
   - Update position
   - Wrap around screen edges

### Edge Behavior
- Toroidal wrapping (exit right, enter left, etc.)

### Performance
- Target: 60 FPS
- Use spatial partitioning if needed for large boid counts
- RequestAnimationFrame for smooth animation

## Responsive Design
- Canvas scales to viewport
- Control panel stacks vertically on narrow screens
- Touch-friendly slider controls

## File Structure
```
Boids/
├── index.html (single file containing all HTML, CSS, JS)
└── spec.md (this file)
```

## Future Enhancements (Optional)
- Mouse interaction (attract/repel boids)
- Predator avoidance
- Food sources that attract ants
- Pheromone trails
- Day/night color themes
