# NAF : Neural Attenuation Fields for Sparse-View CBCT Reconstruction

A neural-field-based method for CBCT reconstruction Follow Up Code [For STUDY]

[\[NAF : Neural Attenuation Fields Paper\]](https://arxiv.org/abs/2209.14540)
[\[CT Pickle dataset\]](https://drive.google.com/drive/folders/1BJYR4a4iHpfFFOAdbEe5O_7Itt1nukJd?usp=sharing)

![NAF framework](assets/framework.png)

## Setup

Using Conda to set up an environment.

``` sh
# Create environment
conda create -n naf python=3.9 -y
conda activate naf

# Install pytorch (hash encoder requires CUDA v11.3)
pip install torch==1.11.0+cu113 torchvision==0.12.0+cu113 torchaudio==0.11.0 --extra-index-url https://download.pytorch.org/whl/cu113

# Install other packages
pip install -r requirements.txt
```
