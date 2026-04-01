# NEO — Near-Earth Object Dashboard

## Overview
A single-page web dashboard that displays live data on Near-Earth Objects (NEOs) using NASA APIs. Features an interactive 3D Earth model that visualizes NEO proximity, approach trajectories, and key risk metrics in real time.

## Features

### Live NEO Data
- Feed of current and upcoming NEO close approaches
- Per-object details: name, size estimate, velocity, miss distance, hazard classification
- Toggle between today's approaches and a configurable date range

### 3D Earth Visualization
- Rotating 3D Earth model rendered with Three.js
- NEO approach paths plotted relative to Earth
- Visual scale indicators for miss distance (Moon distances, lunar orbits)
- Color-coded objects by hazard level (potentially hazardous vs. non-hazardous)
- Click an object in the data feed to highlight its approach path on the globe

### Data Table / Feed
- Sortable table of NEOs by date, size, velocity, or miss distance
- Hazard badge for Potentially Hazardous Asteroids (PHAs)
- Links to NASA JPL Small-Body Database entries per object

## Technical Requirements

### APIs
- **NASA NeoWs API** (`api.nasa.gov`) — primary source for NEO close-approach data
- NASA API key required (free tier available at api.nasa.gov)

### Rendering
- **Three.js** for 3D Earth model and orbital path rendering
- Earth texture map (NASA Blue Marble or equivalent)
- Responsive canvas that fills the viewport

### Data & State
- Date range picker to query NEOs within a 7-day window (NeoWs limit per request)
- Results cached in memory to reduce redundant API calls
- Loading and error states for all API requests

### User Experience
- Responsive layout (desktop and mobile)
- Info tooltips explaining hazard classification, miss distance units, and size estimates
- Accessible color contrast and ARIA labels

### Performance
- Debounced date input to limit API requests
- Lazy rendering — only plot visible/selected NEOs on the 3D model
