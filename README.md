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
The code requires `python>=3.10`, as well as `torch>=2.5.1` and `torchvision>=0.20.1`.

Be sure to install a version that supports GPU's use.

---

## 🔹 **3. Installing Dependencies**  

1. Install the required packages:  
   ```bash
   pip install -r requirements.txt
   ```
2. Install `sam2` and additional modules:

First, clone SAM2's repository and switch to a stable branch.

   ```bash
      git clone https://github.com/facebookresearch/sam2.git

      cd sam2

      git checkout 86827e2fbae8a293f61d51caa70a4b0602c04454 

   ```

Then upgrade the setuptools wheel and compile the project using : 

   ```bash
      pip install --upgrade pip setuptools wheel

      pip install --no-build-isolation -e .

      cd ..

   ```

If you experience problems with the definition of the CUDA_HOME or CUDA_PATH variables, here is a way of fixing it,

   ```bash

      $cuda = "C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.4"
      
      $env:CUDA_HOME = $cuda
      $env:CUDA_PATH = $cuda
      $env:PATH = "$cuda\bin;$cuda\libnvvp;$env:PATH"

   ```

If you want to explore thee official guidelines on how to install SAM2 according to the [original repository](https://github.com/facebookresearch/sam2)

If you are installing on Windows, it's strongly recommended to use [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install) with Ubuntu.

To use the SAM 2 predictor and run the example notebooks, `jupyter` and `matplotlib` are required and can be installed by:

```bash
pip install -e ".[notebooks]"
```

Note:
1. It's recommended to create a new Python environment via [Anaconda](https://www.anaconda.com/) for this installation and install PyTorch 2.5.1 (or higher) via `pip` following https://pytorch.org/. If you have a PyTorch version lower than 2.5.1 in your current environment, the installation command above will try to upgrade it to the latest PyTorch version using `pip`.
2. The step above requires compiling a custom CUDA kernel with the `nvcc` compiler. If it isn't already available on your machine, please install the [CUDA toolkits](https://developer.nvidia.com/cuda-toolkit-archive) with a version that matches your PyTorch CUDA version.
3. If you see a message like `Failed to build the SAM 2 CUDA extension` during installation, you can ignore it and still use SAM 2 (some post-processing functionality may be limited, but it doesn't affect the results in most cases).

Please see [`INSTALL.md`](./INSTALL.md) for FAQs on potential issues and solutions.

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
📌 **SAM2 model weights** : [Download the model here](https://drive.google.com/file/d/1WN0pzBcQLIEF3TIMNj9JC7THtsnvds2i/view?usp=sharing)

📌 **YOLOv10** : [Download the model here](https://drive.google.com/file/d/1o-UcVMxktZQuz5DafjSR4T72gimdtujW/view?usp=sharing)

📌 **PlantSAM2** : [Download the model here](https://drive.google.com/file/d/1b57wlX9tCHRp4h92or41aRnBLA38rEfg/view?usp=sharing)


You should add the three models in the "models" repository and then you should be able to treat any images contained in a repository using this command line : 

```bash
python predict_mask.py /path/to/repository --output_folder ./results
   ```

For a direct test you can use : 

```bash
python predict_mask.py .\test_images\ --output_folder ./results
   ```

## 🔹 **6. Training Example with CLI Script**

Once everything is installed, you can train the SAM2 model using your dataset and masks via the CLI version of the training script. Here's an example:

```bash
python train_sam2_cli.py \
  --images_path /path/to/images \
  --gt_path /path/to/ground_truth_masks \
  --dataset_json /path/to/dataset.json \
  --model_cfg sam2_hiera_l.yaml \
  --checkpoint ./models/sam2_checkpoint.pt \
  --output_dir ./outputs \
  --patch_size 1024 \
  --epochs 20
```

Make sure the JSON file contains the list of image filenames used during training and that all paths point to valid data.
