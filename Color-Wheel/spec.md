# Color Wheel Specification

## Overview
An interactive visualization of color theory as it applies to **light mixing**. Users explore how colored stage lights combine and interact by selecting spotlight colors and applying color harmony rules.

## Concept
A virtual stage with spotlights:
- **Center spotlight**: User selects the primary color
- **Side spotlights**: Automatically set based on the selected color harmony type
- Visual demonstration of how these colored lights mix on the stage surface

## Features
- [ ] Interactive color wheel for selecting the center spotlight color
- [ ] Harmony type selector with options:
  - Complementary (opposite on the wheel)
  - Analogous (adjacent colors)
  - Triadic (three evenly spaced colors)
  - Split-complementary (base + two colors adjacent to complement)
- [ ] Stage visualization showing:
  - Center spotlight with user-selected color
  - Side spotlights with harmony-derived colors
  - Light mixing/blending where beams overlap
- [ ] Real-time updates as user changes color or harmony type

## Technical Requirements
- Single HTML file with embedded CSS/JS
- Canvas-based rendering for stage and light effects
- Additive color mixing (RGB light model, not subtractive paint mixing)
- Responsive design

## Notes
*Add implementation details and design decisions here.*
