# Fake-currency-detection-system
Document Highlights:
Core Algorithms: Detailed explanation of the ORB (Oriented FAST and Rotated BRIEF) and SSIM (Structural Similarity Index) pipeline used to verify currency features.

Feature Breakdown: Descriptions of the 10 specific features analyzed, including bleed lines for both Rs. 500 and Rs. 2000 denominations.

System Workflow: A guide to the sequential execution of the project via the controller.ipynb notebook.

GUI Integration: Overview of the Tkinter-based interface for image selection and result visualization.

Python
from weasyprint import HTML

# Defining the Markdown content
readme_content = """# Fake Currency Detection System

This project is a Python-based application designed to evaluate the authenticity of Indian currency notes (Rs. 500 and Rs. 2000 denominations) using Computer Vision and Image Processing techniques. The system analyzes specific security features to determine if a note is genuine or counterfeit.

## 🚀 System Architecture

The project is modularized into several Jupyter Notebooks, integrated through a central controller:

* **`controller.ipynb`**: The main entry point. It manages the sequential execution of the GUI and testing modules.
* **`gui_1.ipynb`**: The starting interface where users select the currency image (.jpg) and the denomination.
* **`500_Testing.ipynb` / `2000_Testing.ipynb`**: Denomination-specific logic for feature extraction and verification.
* **`gui_2.ipynb`**: The final result analysis interface showing a pass/fail status for each feature.

## 🔍 Verification Features

The system evaluates **10 key features** on each currency note:

1.  **Features 1–7 (Security Motifs):** Verified using **ORB (Oriented FAST and Rotated BRIEF)** for feature detection and **SSIM (Structural Similarity Index)** for comparison against stored templates.
2.  **Feature 8 & 9 (Bleed Lines):**
    * **Rs. 500**: Checks for 5 bleed lines on the left and right.
    * **Rs. 2000**: Checks for 7 bleed lines on the left and right.
    * *Algorithm*: Uses binary thresholding and column-wise pixel analysis to count black regions.
3.  **Feature 10 (Serial Number Panel):** Uses contour detection to verify the presence of 9 distinct characters in the number panel.

## 🛠️ Technology Stack

* **OpenCV (cv2)**: For image resizing, Gaussian blurring, grayscale conversion, and ORB feature matching.
* **Scikit-Image (skimage)**: For calculating the SSIM score to determine image similarity.
* **Tkinter**: For building the Graphical User Interface (GUI) and progress bars.
* **Matplotlib**: For visualizing the image processing steps within the notebooks.

## 📋 Installation & Usage

### Prerequisites
Ensure you have Python installed with the following libraries:
```bash
pip install opencv-python numpy matplotlib scikit-image pillow
Execution
Open and run controller.ipynb.

In the first GUI window:

Click Select an Image to browse for a .jpg file of a currency note.

Select the denomination (500 or 2000).

Click Submit.

The system will process the image through 10 stages of analysis.

View the final report in the Result Analysis window to see which features passed or failed.

📊 Result Analysis
A feature is considered "Verified" if:

Its Average SSIM Score exceeds a predefined threshold (e.g., 0.4 - 0.5 depending on the feature).

Its Max SSIM Score is above 0.79.

For the number panel, exactly 9 characters are detected.
