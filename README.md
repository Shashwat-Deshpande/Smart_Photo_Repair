# Smart Photo Repair: Context-Aware Selective Image Enhancement

> *"Repair the region, not the image."*

## 📝 About the Project
Traditional photo-editing applications provide global adjustments (brightness, contrast, exposure, saturation) that affect the entire image, often ruining properly exposed areas while fixing problematic regions. 

**Smart Photo Repair** is a context-aware computer vision system designed to bridge this gap. Instead of applying global filters, our system combines scene understanding, object detection, and pixel-level segmentation to identify specific visual regions (such as a person or a background), analyze their visual conditions, and apply targeted, localized corrections—all while preserving the rest of the image.

---

## ✨ Key Features
* **Automatic Region & Object Detection:** Identifies key visual components in a photograph using lightweight YOLO detection models.
* **Click-to-Select / Interactive Segmentation:** Generates precise binary masks allowing users to select specific regions (e.g., a person) for targeted edits.
* **Selective Image Enhancement:** Apply independent adjustments (Brightness, Contrast, Warmth, Saturation, and Sharpness) strictly within the selected segmentation mask.
* **Smart Glow / Focus Mode:** Automatically isolates a subject, enhances its local highlights, and selectively dims or blurs the background to create a professional portrait effect.
* **Automated Repair Mode:** Automatically analyzes regional illumination statistics (e.g., detecting underexposure or harsh backlighting) and recommends/applies corrective adjustments.
* **Before / After Comparison:** Provides a seamless interactive preview to evaluate changes side-by-side.

---

## 🛠️ Technical Architecture & Pipeline
The core pipeline moves sequentially from raw image input to natural reconstruction:

1. **Image Acquisition & Preprocessing:** Load, resize, and normalize input images.
2. **Scene Understanding & Detection:** Detect objects and isolate regions of interest.
3. **Segmentation:** Generate pixel-level binary masks ($M(x,y)$) for targeted intervention.
4. **Region Analysis & Diagnosis:** Analyze luminance, contrast, and histogram distributions to detect exposure faults.
5. **Correction Engine & Mask Blending:** Apply transformations strictly inside the masked area using alpha-blending mathematics:
   $$I'(x,y) = M(x,y) \cdot F(I(x,y)) + (1 - M(x,y)) \cdot I(x,y)$$

---

## ⚙️ Tech Stack
* **Programming Language:** Python
* **Computer Vision & Image Processing:** OpenCV, NumPy, Pillow (PIL)
* **Object Detection:** YOLO (You Only Look Once)
* **Segmentation:** Segment Anything (SAM) / Lightweight Segmentation Models
* **User Interface:** Streamlit (for a fast, interactive web-based interface)
* **Development Environment:** VS Code, Jupyter Notebooks

---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone [https://github.com/your-username/Smart_Photo_Repair.git](https://github.com/your-username/Smart_Photo_Repair.git)
cd Smart_Photo_Repair
