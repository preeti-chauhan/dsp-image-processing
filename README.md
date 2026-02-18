# DSP Image Processing Toolkit

A Jupyter notebook covering core 2D digital signal processing techniques applied to images.

## Topics Covered

1. **Spatial Filters** — Gaussian, median, low-pass, high-pass, band-pass (DoG)
2. **Frequency Domain Analysis** — 2D FFT, magnitude/phase/power spectra, ideal LP/HP filters
3. **Edge Detection** — Sobel (magnitude + directional), Laplacian, LoG, Canny
4. **Noise Addition & Removal** — Gaussian and salt-and-pepper noise; denoising with Gaussian, Wiener, median, and Total Variation filters
5. **End-to-End Pipeline** — noise → denoise → edge detection in a single figure

## Requirements

```
pip install numpy scipy matplotlib scikit-image Pillow
```

## Usage

Open the notebook in VS Code:

```bash
code "/Users/preetichauhan/Documents/ClaudeProjects/dsp_image_processing.ipynb"
```

Or launch with Jupyter:

```bash
jupyter notebook "/Users/preetichauhan/Documents/ClaudeProjects/dsp_image_processing.ipynb"
```

Run cells top to bottom with **Shift + Enter**.

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
