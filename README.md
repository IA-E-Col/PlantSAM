# ummiscoSAM

conda create --name PlantSAM2 python==3.11.9

conda activate PlantSAM2

installer pytorch : https://pytorch.org/get-started/locally/
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu124


$env:CUDA_HOME="C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4"

git clone https://github.com/facebookresearch/segment-anything-2.git@86827e2fbae8a293f61d51caa70a4b0602c04454#egg=SAM_2

cd sam2
pip install -e .

pip install -e ".[notebooks]"
cd ..

git clone https://github.com/THU-MIG/yolov10.git

cd yolov10
pip install -r requirements.txt
pip install -e .
cd ..

pip install patchify
pip install transformers

lien modèle yolo https://drive.google.com/file/d/1o-UcVMxktZQuz5DafjSR4T72gimdtujW/view?usp=drive_link

lien modèle SAM https://drive.google.com/file/d/1b57wlX9tCHRp4h92or41aRnBLA38rEfg/view?usp=drive_link