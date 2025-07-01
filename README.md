# Traffic-Sign-Classification-Using-Classical-Digital-Image-Processing-Techniques
A rule-based traffic sign classification system built entirely using classical image processing techniques in Python and NumPy, without using any machine learning models or external libraries (except for image reading).

# 📌 Project Objective
The goal of this project is to implement a complete end-to-end image analysis pipeline using only classical digital image processing (DIP) techniques. The system classifies cropped traffic sign images using their color, shape, and geometric features, without the use of pretrained models or learning-based methods.

This project revisits foundational computer vision concepts, demonstrating how powerful results can still be achieved using traditional image processing techniques alone.

# 🧠 Core Techniques Used
This project is divided into a series of DIP-based stages:

## 1. 📥 Image Reading
• Image files are read using cv2.imread() or PIL.Image.open()<br>
• All subsequent processing is done using NumPy only (no OpenCV functions)

## 2. 🧽 Preprocessing and Filtering
All filters are implemented from scratch:<br>
• Mean Filter (3×3)<br>
• Gaussian Filter (with tunable σ)<br>
• Median Filter<br>
• Adaptive Median Filter<br>
• Unsharp Masking / High-Boost Filtering

## 3. 🎨 Color Space Conversion & Segmentation
• Manual or PIL-based RGB → HSV conversion<br>
• Segmentation of signs by HSV thresholding:<br>
1) Red signs: Hue [0–15] or [165–180]<br>
2) Blue signs: Hue [100–130]<br>
• Binary mask creation<br>
• Morphological operations: erosion, dilation, opening<br>
• Noise removal using connected components<br>
• Hole filling for improved segmentation

## 4. ✂️ Edge Detection
Custom Canny edge detection, including:<br>
• Gradient calculation using Sobel operator<br>
• Non-maximum suppression<br>
• Double thresholding<br>
• Edge tracking by hysteresis

## 6. 📊 Feature Extraction
From the normalized segmented region, the following features are extracted:<br>
• Corner Count (via Harris Corner Detector)<br>
• Circularity = 4π × Area / (Perimeter)^2<br>
• Aspect Ratio = Width / Height<br>
• Extent = Region Area / Bounding Box Area<br>
• Average Hue

## 7. 🧠 Rule-Based Classification
Using if-else logic based on the above features:<br>
• Distinguishes signs by color and geometry<br>
• Interpretable logic used to differentiate visually similar signs (e.g., Yield vs Stop)

# 🧪 Evaluation
Each prediction is compared against ground truth using:<br>
• results.csv – filename, ground truth, predicted, correctness<br>
• metrics.txt – accuracy, precision, recall (overall and per-class)<br>
• confusion_matrix.png – heatmap visualization

# 💡 Key Learning Outcomes
• Manual implementation of fundamental image processing techniques<br>
• Understanding HSV segmentation and morphological operations<br>
• Experience with rule-based classification logic<br>
• Evaluation and benchmarking of DIP-based classification pipelines
