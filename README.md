# **PlantSAM2 - Installation et Configuration**  

Ce guide explique comment configurer l'environnement et installer les dépendances nécessaires pour utiliser **PlantSAM2**.

---

## 🔹 **1. Création de l'environnement Python**  

1. Crée un nouvel environnement Conda avec Python 3.11.9 :  
   ```bash
   conda create --name PlantSAM2 python==3.11.9
   ```
2. Active l’environnement :  
   ```bash
   conda activate PlantSAM2
   ```

---

## 🔹 **2. Installation de PyTorch**  
Installe **PyTorch** en suivant les instructions officielles :  
👉 [Guide d'installation PyTorch](https://pytorch.org/get-started/locally/)  

---

## 🔹 **3. Installation des dépendances**  

1. Installe les paquets nécessaires :  
   ```bash
   pip install -r requirements.txt
   ```
2. Installe `sam2` et les modules complémentaires :  
   ```bash
   cd segment-anything-2
   pip install -e .
   pip install -e ".[notebooks]"
   cd ..
   ```

---

## 🔹 **4. Installation de YOLOv10**  

1. Clone le dépôt YOLOv10 :  
   ```bash
   git clone https://github.com/THU-MIG/yolov10.git
   ```
2. Installe les dépendances de YOLOv10 :  
   ```bash
   cd yolov10
   pip install -r requirements.txt
   pip install -e .
   cd ..
   ```

---

## 🔹 **5. Téléchargement des modèles**  

📌 **YOLOv10** : [Télécharger le modèle ici](https://drive.google.com/file/d/1o-UcVMxktZQuz5DafjSR4T72gimdtujW/view?usp=drive_link)  

📌 **Segment Anything Model (SAM)** : [Télécharger le modèle ici](https://drive.google.com/file/d/1b57wlX9tCHRp4h92or41aRnBLA38rEfg/view?usp=drive_link)  

---

## 🎯 **Résumé**  

1. Créer et activer l’environnement Conda  
2. Installer PyTorch  
3. Installer les dépendances avec `pip install -r requirements.txt`  
4. Installer `sam2` et `yolov10`  
5. Télécharger les modèles YOLO et SAM  
