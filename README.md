

**Training code available at [![Repo](https://badgen.net/badge/icon/GitHub?icon=github&label)](https://github.com/ABaldrati/CLIP4Cir)**

## Getting Started

To get a local copy up and running follow these simple steps.

### Prerequisites

We strongly recommend the use of the [**Anaconda**](https://www.anaconda.com/) package manager in order to avoid dependency/reproducibility problems.
A conda installation guide for linux systems can be found [here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html)

### Installation
 
1. Clone the repo
```sh
git clone https://github.com/ABaldrati/CLIP4CirDemo
```
2. Install Python dependencies
```sh
conda create -n clip4cir -y python=3.8
conda activate clip4cir
conda install -y -c pytorch pytorch=1.7.1 torchvision=0.8.2
pip install flask==2.0.2
pip install git+https://github.com/openai/CLIP.git
```
3. Download [**FashionIQ**](https://sites.google.com/view/cvcreative2020/fashion-iq)
and [**CIRR**](https://cuberick-orion.github.io/CIRR/) datasets
## Usage
Here's a brief description of each and every file and folder in the repo:

* ```utils.py```: Utils file
* ```model.py```: Combiner model definition file
* ```data_utils.py```: Dataset loading and preprocessing utils file
* ```extract_features.py```: Feature extraction file
* ```hubconf.py```: Torch Hub config file
* ```app.py```: Flask server file
* ```static```: Flask static files folder
* ```templates```: Flask templates folder

### Data Preparation
To properly work with the codebase [**FashionIQ**](https://sites.google.com/view/cvcreative2020/fashion-iq)
and [**CIRR**](https://cuberick-orion.github.io/CIRR/) datasets should have the following structure:


```
project_base_path
└───  fashionIQ_dataset
      └─── captions
            | cap.dress.test.json
            | cap.dress.train.json
            | cap.dress.val.json
            | ...
            
      └───  images
            | B00006M009.png
            | B00006M00B.png
            | B00006M6IH.png
            | ...
            
      └─── image_splits
            | split.dress.test.json
            | split.dress.train.json
            | split.dress.val.json
            | ...

└───  cirr_dataset       
       └─── dev
            | dev-0-0-img0.png
            | dev-0-0-img1.png
            | dev-0-1-img0.png
            | ...
       
       └─── test1
            | test1-0-0-img0.png
            | test1-0-0-img1.png
            | test1-0-1-img0.png 
            | ...
       
       └─── cirr
            └─── captions
                | cap.rc2.test1.json
                | cap.rc2.train.json
                | cap.rc2.val.json
                
            └─── image_splits
                | split.rc2.test1.json
                | split.rc2.train.json
                | split.rc2.val.json
```

### Feature Extraction
Before launching the demo it is necessary to extract the features 
using the following command
```shell
python extract_features.py
```

### Run the Demo
Start the server and run the demo using the following command
```shell
python app.py
```
By default, the server run on port 5000 of localhost address: http://127.0.0.1:5000/


## Demo overview
* Initially choose the dataset you want to experience with. As the image 
shown by the image you can experience with CIRR dataset or FashionIQ dataset

![](images/dataset_choice.png "Dataset choice")

* Choose the reference image 

![](images/reference_choice.png "Reference choice")

* Choose or manually insert the relative caption

![](images/relative_caption.png "Caption choice")

* Check out the results. By clicking on a
retrieved image you can use such image as reference image in a
new query

![](images/results.png "Results")

