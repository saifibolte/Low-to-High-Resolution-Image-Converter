# Low to High Resolution Image Converter (4x Super-Resolution)

This project is an **image super-resolution tool** that converts **low-resolution images** into **high-resolution images (4x upscale)** using a **Residual-in-Residual Dense Block Network (RRDBNet)**, which is the backbone of **ESRGAN** architecture.

---

## Features
✅ Converts **low-resolution (LR)** images to **high-resolution (HR)** images by **4x**.  
✅ Utilizes **PyTorch** for deep learning model inference.  
✅ Implements **RRDBNet** architecture for super-resolution.  
✅ Supports **batch processing** of images from a folder.  

---

## Project Structure
```
├── RRDBNet_arch.py      # Model architecture for RRDBNet
├── test.py              # Script to run super-resolution on images
├── models/
│   └── RRDB_ESRGAN_x4.pth   # Pre-trained model weights (download separately)
├── LR/                  # Input low-resolution images
├── results/             # Output high-resolution images
└── README.md
```

---

## Model Architecture
- **RRDBNet** (Residual-in-Residual Dense Block Network)
- Consists of:
  - Residual Dense Blocks (RDB)
  - Multiple RRDB blocks for feature extraction
  - Two-step upsampling layers for **4x scaling**
  - Leaky ReLU activation for non-linearity

---

## How It Works
1. Loads a **pre-trained ESRGAN RRDBNet model**.
2. Reads low-resolution images from the `LR/` folder.
3. Upscales each image by a factor of **4x**.
4. Saves the high-resolution images to the `results/` folder.

---

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/Low-to-High-Image-Converter.git
   cd Low-to-High-Image-Converter
   ```

2. Install dependencies:
   ```bash
   pip install torch torchvision opencv-python numpy
   ```

3. Download pre-trained ESRGAN model weights and place them in the `models/` folder:
   - [Download ESRGAN RRDBNet_x4.pth](https://drive.google.com/file/d/1eoWN613w5pjL4Uyh5XnYMuBIXL52CZ4z/view?usp=sharing)

---

## Usage
1. Place your **low-resolution images** in the `LR/` folder.
2. Run the super-resolution script:
   ```bash
   python test.py
   ```
3. High-resolution images will be saved in the `results/` folder.

---

## Example
Input (Low Resolution):  
<img src="https://github.com/saifibolte/Low-to-High-Resolution-Image-Converter/blob/a7786fb2eb69fd56bed0c37a97eadf69ff189a59/LR/124.png">  

Output (High Resolution, 4x):  
<img src="https://via.placeholder.com/600" width="600"/>  

---

## Customization
- **Change upscale factor** → Modify interpolation scale factor in `RRDBNet_arch.py` (`F.interpolate(... scale_factor=2 ...)`) for each upsampling stage.
- **Use GPU** → Set device to `cuda` in `test.py`:
   ```python
   device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
   ```
