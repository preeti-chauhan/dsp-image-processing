# DSP Image Processing Toolkit

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/preeti-chauhan/dsp-image-processing/blob/main/dsp_image_processing.ipynb)
[![View Notebook](https://img.shields.io/badge/Jupyter-View%20Notebook-orange?logo=jupyter)](https://nbviewer.org/github/preeti-chauhan/dsp-image-processing/blob/main/dsp_image_processing.ipynb)

> **GitHub can't render the notebook?** Click one of the badges above to view or run it instantly.

Classical 2D digital signal processing techniques applied to images — from spatial filters to frequency-domain analysis, edge detection, and denoising.

## Motivation

Many image processing problems — blurring, sharpening, noise removal, edge extraction — are fundamentally signal processing problems. Understanding them in both the spatial and frequency domain builds intuition for why deep learning-based approaches work, and when classical methods are sufficient. This notebook implements the core DSP toolkit from scratch using NumPy and SciPy.

## Overview

Covers five areas of 2D image DSP:

- **Spatial filters** — Gaussian, median, low-pass, high-pass, band-pass (DoG)
- **Frequency domain** — 2D FFT, magnitude/phase/power spectra, ideal LP/HP filters
- **Edge detection** — Sobel (magnitude + directional), Laplacian, LoG, Canny
- **Noise & denoising** — Gaussian and salt-and-pepper noise; Gaussian, Wiener, median, and Total Variation denoising; PSNR & SSIM evaluation
- **End-to-end pipeline** — noise → denoise → edge detection in a single figure

## Topics in Detail

### 1 · Spatial Filters
| Filter | Purpose |
|---|---|
| Gaussian | Smooth/blur — low-pass in spatial domain |
| Median | Remove salt-and-pepper noise, preserve edges |
| Low-pass | Retain slow-varying intensity (suppress detail) |
| High-pass | Enhance edges and fine detail |
| Band-pass (DoG) | Isolate mid-frequency structure (blob detection) |

### 2 · Frequency Domain (2D FFT)
Transforms the image to the frequency domain to visualise which spatial frequencies carry structure vs. noise. Applies ideal low-pass and high-pass masks directly in the frequency domain to demonstrate the duality with spatial filtering.

### 3 · Edge Detection
| Method | How it works |
|---|---|
| Sobel | First-order gradient — fast, directional |
| Laplacian | Second-order derivative — finds zero-crossings |
| LoG | Gaussian-smoothed Laplacian — noise-robust |
| Canny | Multi-stage: gradient + NMS + hysteresis — best general-purpose |

### 4 · Noise & Denoising
Adds synthetic Gaussian and salt-and-pepper noise, then compares four classical denoisers using PSNR and SSIM to quantify quality vs. the clean reference.

### 5 · End-to-End Pipeline
Chains noise addition → denoising → edge detection in a single pass, showing how each stage affects the final result.

## Design Decisions

- **Spatial and frequency domain together** — every filter is shown in both domains to build intuition for the Fourier duality between convolution and multiplication
- **PSNR + SSIM for denoising** — PSNR measures pixel-level error; SSIM captures perceptual structure — both together give a complete picture of denoising quality
- **Classical methods only** — no deep learning; the goal is to understand the signal processing foundations that motivate CNN-based approaches
- **Built-in sample image** — uses `skimage.data.astronaut()` by default so the notebook runs without any setup; swap in any image in Section 0

## Requirements

```
pip install numpy scipy matplotlib scikit-image Pillow
```

## Usage

```bash
jupyter notebook dsp_image_processing.ipynb
```

Or open in Colab via the badge above — no local setup needed.

## Using Your Own Image

In Section 0, uncomment Option B and set your image path:

```python
img_pil   = Image.open('your_image.jpg').convert('RGB')
img_color = np.array(img_pil)
img       = color.rgb2gray(img_color)
```

## Files

| File | Description |
|---|---|
| `dsp_image_processing.ipynb` | Main notebook |
| `README.md` | This file |
