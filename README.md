# Explainable-Deep-Vision-for-Safe-Autonomous-Driving

### 🧠 Overview
This project focuses on developing an **explainable and weather-resistant autonomous driving system** capable of operating safely under **fog, haze, and low-visibility conditions**.  
The proposed model integrates **Adaptive DehazeNet**, a **DenseNet/ResNet-50 backbone**, **Liquid Time Constant (LTC) Networks**, and **Grad-CAM-based XAI** to ensure transparency, interpretability, and robust decision-making in adverse environments.

---

### 🏗️ Model Architecture
The core pipeline (see diagram on *page 15* of the report) consists of:
1. **Adaptive DehazeNet** — Removes haze and improves visibility using convolutional and attention-based refinement.  
2. **MetaDenseBackbone / ResNet-50** — Extracts contextual and spatial features for segmentation and detection.  
3. **Liquid Time-Constant (LTC) Network** — Captures temporal dependencies across continuous driving frames.  
4. **Grad-CAM (XAI)** — Generates visual heatmaps highlighting key decision regions for interpretability.

![Model Pipeline](figures/model_pipeline.jpg)
*(Figure 3.1 – Model Pipeline from report)*

---

### 🧩 Modules
| Module | Description |
|---------|--------------|
| **Adaptive DehazeNet** | Uses convolutional + channel attention to dehaze inputs dynamically. |
| **MetaDenseBackbone / ResNet-50** | Feature extractor for robust perception; ResNet-50 chosen for best validation loss (0.278 vs 0.477 for DenseNet). |
| **Liquid Time Constant Network** | Temporal modeling for real-time adaptability using learnable time constants. |
| **Grad-CAM (XAI)** | Visual interpretability for control, detection, and segmentation tasks. |

---

### 📊 Experimental Results
| Backbone Architecture | Best Validation Loss |
|------------------------|----------------------|
| DenseNet-121 | 0.477888 |
| ResNet-50 | **0.278269 ✅** |

> **Result:** ResNet-50 achieved lower validation loss and better interpretability, making it the preferred backbone.

#### Grad-CAM Visualizations  
Below are example heatmaps showing model focus under foggy conditions.

![Grad-CAM DenseNet](figures/gradcam_densenet.jpg)
![Grad-CAM ResNet50](figures/gradcam_resnet.jpg)

*(Figures 4.1 & 4.2 – Grad-CAM Outputs)*

---

### 📚 Dataset
**Cityscapes Foggy and Haze Dataset**  
- 3,475 Foggy DBF images (20 GB)  
- Realistic urban scenes with varying fog/haze levels  
- Used for training and validation of dehazing and perception modules  

---

### ⚙️ Methodology Summary
- **Input:** Video frames from foggy urban scenes  
- **Processing:** Adaptive dehazing → feature extraction → temporal modeling → explainability  
- **Output:** Interpretable segmentation maps and driving decisions  

![Adaptive DehazeNet Pipeline](figures/dehazenet_pipeline.jpg)
*(Figure 3.2 – Adaptive DehazeNet Pipeline)*

---

### 🚀 Future Work
- Extend to multi-sensor (LiDAR + camera) fusion.  
- Deploy in real-time embedded systems for on-road testing.  
- Compare LTC networks with transformer-based temporal models.  

**© 2025 Indian Institute of Information Technology Kottayam**  
*Developed as part of B.Tech Final Year Project — Explainable Deep Vision for Safe Autonomous Driving*
