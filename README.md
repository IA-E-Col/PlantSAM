# **PlantSAM2 - Installation and Configuration**  

This guide explains how to set up the environment and install the necessary dependencies to use **PlantSAM2**.

---

## 🔹 **1. Creating the Python Environment**  

1. Create a new Conda environment with Python 3.11.9:  
   ```bash
   conda create --name PlantSAM2 python==3.11.9
   ```
2. Activate the environment :  
   ```bash
   conda activate PlantSAM2
   ```

---

## **2. Installing PyTorch**  
Install **PyTorch** following the official instructions:  
[PyTorch Installation Guide](https://pytorch.org/get-started/locally/)  

---

## 🔹 **3. Installing Dependencies**  

1. Install the required packages:  
   ```bash
   pip install -r requirements.txt
   ```
2. Install `sam2` and additional modules:  
   ```bash
   cd segment-anything-2
   pip install -e .
   pip install -e ".[notebooks]"
   cd ..
   ```

---

## **4. Installing YOLOv10**  

1. Clone the YOLOv10 repository :  
   ```bash
   git clone https://github.com/THU-MIG/yolov10.git
   ```
2. Install YOLOv10 dependencies :  
   ```bash
   cd yolov10
   pip install -r requirements.txt
   pip install -e .
   cd ..
   ```

---

## 🔹 **5. Downloading Models**  

```bash
   mkdir models
   ```
📌 **SAM2 model weights** : [Download the model here]([https://drive.google.com/file/d/1WN0pzBcQLIEF3TIMNj9JC7THtsnvds2i/view?usp=sharing](https://drive.google.com/file/d/1WN0pzBcQLIEF3TIMNj9JC7THtsnvds2i/view?usp=sharing)).

📌 **YOLOv10** : [Download the model here]([https://drive.google.com/file/d/1o-UcVMxktZQuz5DafjSR4T72gimdtujW/view?usp=drive_link](https://drive.google.com/file/d/1o-UcVMxktZQuz5DafjSR4T72gimdtujW/view?usp=sharing))  

📌 **PlantSAM2** : [Download the model here]([https://drive.google.com/file/d/1b57wlX9tCHRp4h92or41aRnBLA38rEfg/view?usp=drive_link](https://drive.google.com/file/d/1b57wlX9tCHRp4h92or41aRnBLA38rEfg/view?usp=sharing))  
