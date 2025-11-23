# DMS Heatmap Desaturator

A lightweight Python utility for Deep Mutational Scanning (DMS) visualization. This tool programmatically detects high-contrast red blocks (often used to signify stop codons or missing data) in heatmaps and replaces them with a neutral color. 

It is designed specifically for scientific figures, ensuring **lossless quality** and preserving original **DPI metadata**.

## 🎯 The Problem
In DMS heatmaps, pure red blocks (`#FF0000`) are often used to mark specific categories (like nonsense mutations). However, visually, these bright blocks can dominate the image, distracting from the actual fitness landscape data (usually represented in blue/white gradients).

**This tool fixes that by muting the red channel without affecting the rest of the data.**

## ✨ Features
* **Smart Masking:** Uses NumPy filtering to target specific color ranges (handles compression artifacts around edges).
* **Publication Ready:** Forces PNG (lossless) saving to prevent JPEG artifacts.
* **DPI Preservation:** Retains the original image resolution metadata (e.g., 300 DPI) for printing.
* **Customizable:** Easily adjust the target color (gray, white, muted orange, etc.).

## 🛠️ Installation

### Prerequisites
You will need Python 3 installed.

### Install Dependencies
This project relies on `Pillow` (PIL) for image handling and `NumPy` for fast matrix operations.

```bash
pip install numpy Pillow
```

## 🚀 Usage

### 1. The Script
Clone the code as a file named `dms_cleaner.py`.


### 2. Running the Command
Open your terminal or command prompt and run:

```bash
python dms_cleaner.py original_heatmap.png clean_heatmap.png
```

## 🎨 Customization

To change the output color, modify the `new_color` tuple in the script:

* **Dark Gray:** `(100, 100, 100)`
* **White (Invisible):** `(255, 255, 255)`
* **Muted Orange:** `(210, 150, 100)`

## 📄 License
This project is open source and available under the MIT License.
