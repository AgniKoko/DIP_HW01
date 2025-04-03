# Digital Image Processing — 1st Course Assignment (Academic Year 2024–2025)

## Description
This repository contains the Python implementation for the first lab assignment of the Digital Image Processing course. The goal is to analyze thermal radiation captured by a camera, convert and visualize it in different color spaces, and estimate material temperature using blackbody radiation principles.

![image](https://github.com/user-attachments/assets/5bf5ca2c-d7c4-44cc-a08e-c4c1b3c3dca7)


## Contents

```plaintext
├── data/
│   ├── CFA_stream.png         # Raw Bayer-pattern image of thermal emission
│   ├── chromaDiagram.png       # CIE xy chromaticity diagram
│   └── cieXYZ_curves.csv      # Color Matching Functions (CMF) data for 1 nm wavelengths
├── DIP_HW01.ipynb            # Jupyter Notebook with all tasks implemented
├── output/
│   ├── demosaiced.png         # RGB image after demosaicing
│   ├── xy_chromaticities.png # Chromaticity trajectory plot
│   ├── material_mask.png      # Binary mask isolating material region
│   ├── temperature_map.png    # Heatmap of estimated temperatures
│   └── temperature_plot.png   # Plot of temperature distribution and mean temperature
└── README.md                 # This document
```

## Setup

### Requirements
- Python 3.9 or later
- pip

## Tasks

The assignment consists of the following steps, implemented sequentially in the Jupyter Notebook:

1. **Compute XYZ tristimulus values**
   - Load spectral CMF data from `data/cieXYZ_curves.csv`.
   - Evaluate blackbody spectral radiance (Planck's law) for temperatures from 1000 K to 30000 K.
   - Integrate against CMF curves to compute X, Y, Z coordinates.

2. **Plot chromaticity trajectory**
   - Convert computed XYZ to xy chromaticity.
   - Overlay trajectory for different temperatures onto `data/chromaDiagram.png`.

3. **Demosaic CFA image**
   - Convert raw Bayer-pattern image (`data/CFA_stream.png`) to RGB using OpenCV or Colour library.
   - Save and display the resulting color image.

4. **Convert RGB to XYZ**
   - Use `colour` library’s `sRGB_to_XYZ` function to transform the demosaiced image.

5. **Mask material region**
   - Define and apply a pixel-based criterion to isolate the hot material region.
   - Visualize and save the binary mask (`output/material_mask.png`).

6. **Estimate temperature**
   - For masked pixels, convert XYZ to xy chromaticity and interpolate against the computed blackbody trajectory to estimate temperature.
   - Plot per-pixel temperature distribution and compute the mean temperature.
     
7. **Histogram and Heatmap**
   - Create a histogram based on the per-pixel temperature distribution and generate and save a heatmap (`output/temperature_map.png`) and a temperature distribution plot (`output/temperature_plot.png`).

## Outputs
- **Demosaiced RGB image** (`output/demosaiced.png`)
- **Chromaticity trajectory plot** (`output/xy_chromaticities.png`)
- **Material mask** (`output/material_mask.png`)
- **Temperature heatmap** (`output/temperature_map.png`)
- **Temperature distribution plot** (`output/temperature_plot.png`)

## Running the Notebook
Open `DIP_HW01.ipynb` in Jupyter and execute all cells.

## References
- Planck’s law for blackbody radiation
- CIE 1931 color matching functions
- Colour Science Python library documentation

---
## Notes
This project is based on an assignment from the "Digital Image Processing" course at Democritus University of Thrace (DUTH). The original task description is intellectual property of the course instructor.
