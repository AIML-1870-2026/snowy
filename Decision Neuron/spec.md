# Decision Neuron

## Overview
An interactive visualization of a single perceptron (artificial neuron) that helps users understand how neural networks make decisions. The example scenario: **"Should I go to the gym in the morning?"**

## Core Concept

### The Perceptron Model
A perceptron takes multiple inputs, multiplies each by a weight (importance), sums them together, adds a bias, and produces an output decision.

### Decision Formula
```
Decision Score = (factor₁ × importance₁) + (factor₂ × importance₂) + (factor₃ × importance₃) + bias
```

If the Decision Score exceeds a threshold (typically 0), the output is **YES** (go to gym). Otherwise, **NO** (skip gym).

## Input Factors

| Factor | Description | Range | Effect |
|--------|-------------|-------|--------|
| **Bedtime** | What time the user went to bed | Early (-1) to Late (+1) | Earlier bedtime = more likely to go |
| **Gym Time** | How early the gym session is | Late morning (-1) to Early dawn (+1) | Later gym time = more likely to go |
| **Morning Busyness** | How packed the rest of the morning is | Free (-1) to Busy (+1) | Less busy = more likely to go |

## Weights (Importance)
Each factor has an adjustable weight representing how much it influences the decision:
- **Bedtime Importance**: How much sleep affects your gym motivation
- **Gym Time Importance**: How much the wake-up time matters
- **Busyness Importance**: How much schedule flexibility affects the decision

Weight range: -2.0 to +2.0

## Bias
- **Health Consciousness**: The user's baseline motivation to exercise
- Acts as a "default tendency" before considering factors
- Positive bias = naturally inclined to go
- Negative bias = naturally inclined to skip
- Range: -2.0 to +2.0

## Visual Design

### Neuron Diagram
- Display a classic perceptron diagram showing:
  - 3 input nodes (factors) on the left
  - Connection lines with weight labels
  - Central neuron node (summation + activation)
  - Output node on the right (YES/NO)
- Animate signal flow from inputs through to output
- Color-code connections based on weight (positive = green, negative = red)

### Canvas
- Full viewport size
- Dark background (#0a0a0f)
- Glowing, neural-inspired aesthetic
- Animated pulses along connections

### Color Scheme
- Background: Deep dark (#0a0a0f)
- Positive weights/signals: Cyan/Green glow
- Negative weights/signals: Red/Orange glow
- Neurons: Purple/Blue gradient
- Active output: Bright pulse animation

## User Controls

### Control Panel
- Position: Fixed panel on the right side
- Style: Dark theme, matches aesthetic
- Collapsible on mobile

### Factor Sliders
| Control | Range | Default | Description |
|---------|-------|---------|-------------|
| Bedtime | -1 to 1 | 0 | -1 = 8pm, 0 = 11pm, 1 = 2am |
| Gym Time | -1 to 1 | 0 | -1 = 9am, 0 = 7am, 1 = 5am |
| Morning Busyness | -1 to 1 | 0 | -1 = Free, 0 = Normal, 1 = Packed |

### Weight Sliders
| Control | Range | Default | Description |
|---------|-------|---------|-------------|
| Bedtime Weight | -2 to 2 | 1.0 | How much sleep matters |
| Gym Time Weight | -2 to 2 | 0.8 | How much early wake-up hurts |
| Busyness Weight | -2 to 2 | -0.5 | How much busyness discourages |

### Bias Slider
| Control | Range | Default | Description |
|---------|-------|---------|-------------|
| Health Consciousness | -2 to 2 | 0.5 | Baseline gym motivation |

### Threshold
- Adjustable decision threshold (default: 0)
- Score > threshold = GO
- Score ≤ threshold = SKIP

## Output Display

### Decision Result
- Large, prominent display of the decision: **"GO TO GYM"** or **"SKIP TODAY"**
- Color indicates decision (green = go, red = skip)
- Show the calculated score numerically

### Calculation Breakdown
Display the math in real-time:
```
(Bedtime × Weight₁) + (Gym Time × Weight₂) + (Busyness × Weight₃) + Bias = Score

Example:
(-0.5 × 1.0) + (0.2 × 0.8) + (0.3 × -0.5) + 0.5 = 0.31 → GO!
```

## Stats Display
- Current decision score
- Individual contributions from each factor
- Distance from threshold
- Decision confidence percentage

## Responsive Design
- Canvas scales to viewport
- Control panel collapses to hamburger menu on mobile
- Touch-friendly controls with larger hit areas

## File Structure
```
Decision Neuron/
├── index.html (single file containing all HTML, CSS, JS)
└── spec.md (this file)
```

## Future Enhancements (Optional)
- Multiple scenarios/decisions to choose from
- Multi-layer network visualization
- Training mode (adjust weights to match desired outputs)
- Preset personality profiles
- Share configuration via URL
- Animation of learning/weight adjustment
