# 🌳 MARSAD
### Satellite Image Processing • Street Extraction • Empty-Space Segmentation • Tree Count Estimation

This repository contains the **AI implementation** of the MARSAD system — a computer-vision solution designed to analyze satellite imagery and automatically identify **streets**, and **empty spaces** to support urban forestation efforts.

---

## 📁 Repository Structure
```
MARSAD-AI-Implementation/
│
├── Models/                     
│   ├── empty_space_segmentation_weights.pt
│   └── street_detection_weights.pt
│
├── MARSAD_AI_System.ipynb      # Final pipeline notebook
└── ai_implementation.py        # # All experiments       
```

---

## My Role (AI Lead & Project Leader)

- Led the AI pipeline design & experimentation  
- Assigned tasks and managed team workflow  
- Communicated with external stakeholders (e.g., Jeddah Municipality)  
- Participated in dataset collection & performed annotation on Roboflow  
- Implemented image augmentation strategies  
- Trained YOLOv12 for street detection  
- Trained YOLOv11 for empty-space segmentation   
- Designed logo, poster, and project branding  

---

## 🔬 Experiments Overview

### **Experiment 1 — Full Segmentation Pipeline (Mask R‑CNN)**
- Two segmentation models (streets + empty space)  
- **AP50: 40%**, **AP: 15%**  
- Low performance → model struggled with aerial noise  

### **Experiment 2 — Direct Segmentation (YOLOv11)**
- Single-step segmentation  
- **mAP50: 57%**, **Precision: 66%**, **Recall: 62%**  
- High false negatives  

### **Experiment 3 — Detection Before Segmentation**
- YOLOv12 → street detection  
- YOLOv11 → segmentation  
- **AP50: 66%**, **AP: 49%**, **Precision: 62%**, **Recall: 62%**  
- High false positives  

### **Experiment 4 — Rotation-Based Optimization**
- Rotation preprocessing to align streets  
- Failed — unusual aspect ratios confused the model  

### **Experiment 5 — Final Processing Pipeline (Chosen Approach)**
- Combines Experiment 2 + 3 sequentially  
- **AP50: 66%**, **Precision: 60%**, **Recall: 67%**  
- Most stable results  

---

## 🧩 Final End-to-End Pipeline

1. **Input Layer**  
   - Satellite images retrieved from ESRI  

2. **Street Detection (YOLOv12)**  
   - Outputs street bounding boxes  

3. **Cropping & Padding**  
   - Normalize street orientation & shape  

4. **Empty Space Segmentation (YOLOv11)**  
   - Mask generation for plantation areas  

5. **Mask Merging**  
   - Combine segments into full geospatial layers  

6. **Tree Counting Formula**  
```
num_trees = width * GSD / tree_spacing
```

7. **Final Output**  
   - Tree count per segment  
   - Visualized maps with segment labels  

---

## 📬 Contact
**Nujud Almaleki**  
AI Developer & Computer Vision Enthusiast  
📧 nujudalmaleki@gmail.com
