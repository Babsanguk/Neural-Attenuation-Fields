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

## Training and evaluation

Download four CT datasets from [here](https://drive.google.com/drive/folders/1BJYR4a4iHpfFFOAdbEe5O_7Itt1nukJd?usp=sharing). Put them into the `./data` folder.

Experiments settings are stored in `./config` folder.

For example, train NAF with `chest_50` dataset:

``` sh
python train.py --config ./config/chest_50.yaml
```

*Note: It may take minutes to compile the hash encoder module for the first time.*

The evaluation outputs will be saved in `./logs/eval/epoch_*` folder.

## Customized dataset

You can make your own simulation dataset with TIGRE toolbox. Please first install [TIGRE](https://github.com/CERN/TIGRE/blob/master/Frontispiece/python_installation.md).

```sh
# Install TIGRE
wget https://github.com/CERN/TIGRE/archive/refs/tags/v2.3.zip
unzip v2.3.zip
cd TIGRE-2.3/Python
pip install . --no-build-isolation
cd ../../
```

Put your CT data in the format as follows. Examples can be seen in [here](https://drive.google.com/drive/folders/1BJYR4a4iHpfFFOAdbEe5O_7Itt1nukJd?usp=sharing).

```sh
├── raw                                                                                                       
│   ├── XXX (your CT name)
│   │   └── img.mat (CT data)
│   │   └── config.yml (Information about CT data and the geometry setting of CT scanner)
```

Then use TIGRE to generate simulated X-ray projections.

``` sh
python dataGenerator/generateData.py --ctName XXX --outputName XXX_50
```
## Coordinate system
Our coordinate system is similar to that in TIGRE toolbox, except for the detector plane which follows OpenCV standards.

![NAF coordinate systen](assets/coord.png)


