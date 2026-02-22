# Readable

## Specification

An interactive tool to help users visualize how different combinations of text color and size affect readability.

## Features

### Color Controls
- RGB sliders to set the **background color**
- RGB sliders to set the **text color**

### Readability Metrics
- Display the **luminance** of the background color
- Display the **luminance** of the text color
- Calculate and display the **contrast ratio** between background and text

### Contrast Ratio Calculation
1. Convert RGB values to **relative luminance**
2. Calculate ratio using formula: `(L1 + 0.05) / (L2 + 0.05)`
   - L1 = luminance of the lighter color
   - L2 = luminance of the darker color
3. Display ratio in format: **X.XX:1**

### Text Preview
- Live preview area showing sample text with the selected colors
- Adjustable text size to test readability at different scales

