# Turing Patterns Explorer

## Overview
An interactive web application that simulates reaction-diffusion systems to generate Turing patterns—organic, maze-like structures that emerge from simple chemical interactions. Users can seed the simulation with mouse clicks and control various parameters to explore different pattern formations.

## Core Concept

### Reaction-Diffusion System
Based on the Gray-Scott model:
- **Chemical A (Activator)**: Spreads and activates growth
- **Chemical B (Inhibitor)**: Spreads faster, inhibits A
- Two coupled differential equations govern concentration changes
- Patterns emerge from the interplay of reaction and diffusion rates

### Mathematical Model
```
∂A/∂t = Dₐ∇²A - AB² + f(1-A)
∂B/∂t = Dᵦ∇²B + AB² - (k+f)B

Where:
- Dₐ, Dᵦ = Diffusion rates
- f = Feed rate (replenishes A)
- k = Kill rate (removes B)
```

## Visual Design

### Canvas
- Full viewport size
- Dark background (#0a0a0f)
- Chemical concentrations rendered as grayscale or color gradient
- Smooth, organic maze-like patterns

### Color Scheme Options
- **Classic**: Black (high B) to white (high A)
- **Heat**: Dark purple → blue → cyan → white
- **Organic**: Deep brown → tan → cream (biological feel)

## User Interactions

### Mouse/Touch Input
- **Click/Tap**: Add a burst of chemical B at cursor position
- **Click + Drag**: Paint chemical B along path
- **Brush size**: Configurable radius of effect

### Keyboard Shortcuts
- **Space**: Pause/Resume simulation
- **R**: Reset to initial state
- **C**: Clear canvas (reset chemicals)

## User Controls

### Control Panel
- Position: Fixed panel on the right side
- Style: Dark theme, matches aesthetic
- Collapsible on mobile

### Parameters

| Control | Range | Default | Description |
|---------|-------|---------|-------------|
| Feed Rate (f) | 0.01 - 0.1 | 0.055 | Rate chemical A is added |
| Kill Rate (k) | 0.01 - 0.1 | 0.062 | Rate chemical B is removed |
| Diffusion A | 0.5 - 2.0 | 1.0 | How fast A spreads |
| Diffusion B | 0.1 - 1.0 | 0.5 | How fast B spreads |
| Reaction Speed | 1 - 20 | 10 | Simulation steps per frame |
| Wall Thickness | 1 - 5 | 2 | Scales pattern density |
| Brush Size | 5 - 50 | 20 | Radius of mouse interaction |

### Preset Patterns
Different f/k combinations produce distinct patterns:
- **Mitosis**: Spots that divide (f=0.0367, k=0.0649)
- **Coral**: Branching coral-like growth (f=0.0545, k=0.062)
- **Maze**: Dense labyrinth patterns (f=0.029, k=0.057)
- **Holes**: Inverse spots/holes (f=0.039, k=0.058)
- **Waves**: Moving wave patterns (f=0.014, k=0.054)

### Additional Controls
- **Reset**: Clear and reinitialize
- **Pause/Play**: Toggle simulation
- **Seed Random**: Add random initial disturbances

## Technical Specifications

### Grid System
```
width: canvas.width / scale
height: canvas.height / scale
scale: Wall Thickness parameter (1-5)
```

### Data Structures
- Two 2D arrays for chemical A and B concentrations
- Double-buffered (current state + next state) to avoid read/write conflicts

### Simulation Loop
1. For each cell in grid:
   - Calculate Laplacian (diffusion) for A and B
   - Apply reaction equations
   - Update next state buffer
2. Swap buffers
3. Render to canvas
4. Repeat `reactionSpeed` times per frame

### Laplacian Kernel (3x3 convolution)
```
[ 0.05  0.2  0.05 ]
[ 0.2  -1.0  0.2  ]
[ 0.05  0.2  0.05 ]
```

### Boundary Conditions
- Wrap-around (toroidal) edges for seamless patterns

### Performance
- Target: 60 FPS rendering
- Use typed arrays (Float32Array) for concentration grids
- Batch pixel updates using ImageData
- Consider WebGL for larger grids (future enhancement)

## Initial State
- Chemical A: 1.0 everywhere
- Chemical B: 0.0 everywhere except small random seeds
- Seeds: Small clusters of B placed randomly or in center

## Stats Display
- FPS counter
- Grid resolution
- Simulation steps per second
- Current f/k values

## Responsive Design
- Canvas scales to viewport
- Control panel collapses to hamburger menu on mobile
- Touch-friendly controls

## File Structure
```
Turing/
├── index.html (single file containing all HTML, CSS, JS)
└── spec.md (this file)
```

## Future Enhancements (Optional)
- Multiple chemical species (3+ chemicals)
- Color mapping options
- Export pattern as image
- Load/save parameter presets
- WebGL compute shaders for performance
- Anisotropic diffusion for directional patterns
