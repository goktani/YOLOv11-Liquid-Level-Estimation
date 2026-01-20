# 🧪 Liquid Level Estimation with YOLOv11 & Geometric Logic

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![YOLOv11](https://img.shields.io/badge/Model-YOLOv11-green)
![OpenCV](https://img.shields.io/badge/Library-OpenCV-red)
![Status](https://img.shields.io/badge/Status-Proof%20of%20Concept-orange)

## 📌 Project Overview
This project demonstrates an industrial Computer Vision approach to estimate the liquid fill level of transparent containers. Unlike standard classification tasks (Empty/Full), this project combines **Object Detection (YOLOv11)** with **Geometric Logic** to calculate a specific fill percentage.

The system not only detects objects but also generates a detailed **Excel Report** with embedded visual references for Quality Control (QC) purposes.

## 🚀 Features
* **Object Detection:** Fine-tuned **YOLOv11** model to detect `Container` and `Fluid`.
* **Geometric Calculation:** Estimates fill level based on the pixel-height ratio:
    $$Fill \% = \frac{\text{Fluid Height}}{\text{Container Height}} \times 100$$
* **Logic Mapping:** Automatically maps detected fluids to their respective containers based on bounding box overlap.
* **Automated Reporting:** Generates a rich `.xlsx` report using `XlsxWriter`, embedding the analyzed images alongside their statistics.

## 📂 Dataset
The project utilizes the **SAM2 Liquid Sem Segmentation** dataset from Roboflow, converted for Object Detection.
* **Source:** [Roboflow Universe](https://universe.roboflow.com/liquids/sam2-liquid-sem-segmentation)
* **Classes:** `Container`, `Fluid`

## 🛠️ Tech Stack
* **Ultralytics YOLOv11:** For state-of-the-art object detection.
* **OpenCV:** For image processing and drawing bounding boxes.
* **Pandas & XlsxWriter:** For data structuring and Excel report generation.
* **Roboflow:** For dataset management and retrieval.

## ⚙️ Installation & Usage

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/goktani/YOLOv11-Liquid-Level-Estimation.git](https://github.com/goktani/YOLOv11-Liquid-Level-Estimation.git)
    cd YOLOv11-Liquid-Level-Estimation
    ```

2.  **Install Requirements**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the Analysis**
    You can run the notebook `yolov11-liquid-level-detection.ipynb` locally or on Kaggle/Colab.
    * *Note: You will need a Roboflow API Key to download the dataset automatically, or you can use your own dataset.*

## 📊 Methodology

1.  **Detection:** The model predicts bounding boxes for containers (Blue) and fluids (Green).
2.  **Association:** The script checks if the center of a Fluid box lies within a Container box.
3.  **Calculation:**
    * `Container Height` = $y_{bottom} - y_{top}$
    * `Fluid Level` = $y_{container\_bottom} - y_{fluid\_top}$
    * `Result` = $(Fluid Level / Container Height) * 100$
4.  **Reporting:** Results are logged and exported to Excel.

## 📈 Outputs
The project outputs two main artifacts:
1.  **Analyzed Images:** Images with bounding boxes and "Lvl: XX%" labels.
2.  **Final_Liquid_Level_Report.xlsx:** A spreadsheet containing:
    * File Name
    * Container ID
    * Fill Percentage
    * **Visual Reference (Embedded Image)**

## 👤 Author
**Göktan İren**
* [Kaggle Profile](https://www.kaggle.com/goktani)
* [LinkedIn](https://www.linkedin.com/in/goktani)

## 📜 Acknowledgements
Special thanks to the open-source community and Roboflow for the dataset availability.
