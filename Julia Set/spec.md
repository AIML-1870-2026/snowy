# Julia Set Explorer

## Overview
An interactive web application that renders Julia set fractals in real-time. Users can explore the infinite complexity of these mathematical structures by adjusting parameters and customizing the visual appearance through color schemes.

## Core Concept

### Mathematical Background
The Julia set is defined by iterating the complex function:
```
z(n+1) = z(n)² + c
```
Where:
- z is a complex number (x + yi)
- c is a constant complex parameter that defines the shape
- Points that remain bounded after iteration are part of the set

### Rendering Algorithm
For each pixel:
1. Map pixel coordinates to complex plane
2. Iterate the function up to max iterations
3. Color based on escape time (iterations until |z| > 2)
4. Points that never escape are colored as "inside" the set

## Visual Design

### Canvas
- Full viewport size
- Dark background (#0a0a0f)
- Smooth gradient coloring based on iteration count

### Color Schemes
| Scheme | Description |
|--------|-------------|
| **Electric** | Deep purple → blue → cyan → white |
| **Fire** | Black → red → orange → yellow → white |
| **Ocean** | Dark blue → teal → aqua → white |
| **Monochrome** | Black → white gradient |
| **Rainbow** | Full hue spectrum based on iteration |
| **Neon** | Black → magenta → pink → white |

## User Controls

### Control Panel
- Position: Fixed panel on the right side
- Style: Dark theme, matches aesthetic
- Collapsible on mobile

### Parameter Sliders

| Control | Range | Default | Description |
|---------|-------|---------|-------------|
| Real (c) | -2.0 to 2.0 | -0.7 | Real component of constant c |
| Imaginary (c) | -2.0 to 2.0 | 0.27015 | Imaginary component of c |
| Max Iterations | 50 - 500 | 100 | Detail level (higher = more detail) |
| Zoom | 0.5 - 100 | 1.0 | Zoom level into the fractal |
| Center X | -2.0 to 2.0 | 0 | Horizontal pan position |
| Center Y | -2.0 to 2.0 | 0 | Vertical pan position |

### Color Controls
- **Color Scheme**: Dropdown selector for preset palettes
- **Inside Color**: Color picker for points inside the set
- **Invert Colors**: Toggle to invert the color mapping

### Preset Parameters
Famous Julia set configurations:
- **Dendrite**: c = 0 + 1i (tree-like branching)
- **San Marco**: c = -0.75 + 0i (dragon-like)
- **Siegel Disk**: c = -0.391 - 0.587i (spiral patterns)
- **Douady Rabbit**: c = -0.123 + 0.745i (rabbit ears)
- **Galaxy**: c = -0.7 + 0.27015i (swirling arms)

### Alternative Formulas
In addition to the standard z² + c iteration, support for rational Julia sets:

| Formula | Name | Description |
|---------|------|-------------|
| **(1 - z³/6) / (z - z²/2)² + c** | Newton Fractal | Complex rational function producing intricate spiral and web-like patterns |

#### Newton Fractal Parameters
Recommended c values for the rational formula:
- **Web**: c = 0 + 0i (symmetric web pattern)
- **Spiral Arms**: c = 0.1 + 0.1i (asymmetric spirals)
- **Shattered**: c = -0.2 + 0.3i (fragmented structures)

### Additional Controls
- **Reset View**: Return to default zoom and position
- **Reset All**: Return all parameters to defaults
- **Animate**: Toggle automatic c parameter animation

## User Interactions

### Mouse/Touch Input
- **Click + Drag**: Pan around the fractal
- **Scroll/Pinch**: Zoom in and out
- **Double-click**: Zoom in at clicked point

### Keyboard Shortcuts
- **Arrow keys**: Pan the view
- **+/-**: Zoom in/out
- **R**: Reset view
- **Space**: Toggle animation
- **1-6**: Quick select color schemes

## Technical Specifications

### Rendering
- Use HTML5 Canvas with ImageData for pixel manipulation
- Render at canvas resolution for crisp details
- Smooth coloring using escape-time algorithm with fractional iteration count

### Performance
- Target: 30+ FPS during interaction
- Use requestAnimationFrame for smooth updates
- Consider Web Workers for heavy computation
- Adaptive resolution during pan/zoom for responsiveness

### Coordinate Mapping
```
complexX = (pixelX - width/2) / (zoom * width/4) + centerX
complexY = (pixelY - height/2) / (zoom * height/4) + centerY
```

## Stats Display
- Current c value (real, imaginary)
- Zoom level
- Iteration count
- FPS counter
- Render time (ms)

## Responsive Design
- Canvas scales to viewport
- Control panel collapses to hamburger menu on mobile
- Touch-friendly controls with larger hit areas

## File Structure
```
Julia Set/
├── index.html (single file containing all HTML, CSS, JS)
└── spec.md (this file)
```

## Future Enhancements (Optional)
- Mandelbrot set mode (where c varies per pixel)
- Higher precision rendering for deep zoom
- Save/export current view as image
- Share parameters via URL
- GPU acceleration with WebGL
- Orbit trap coloring methods
- Animation path recording
