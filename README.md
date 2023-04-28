# RealSign-Indian-Sign-Language-Dataset: An Open-Source Indian Sign Language Database
This repository contains a collection of images of Fingerspelled Indian Sign Language (ISL) alphabets. Four signers have contributed towards the making of this dataset with different lighting, skin tones, colors, and variations of the ISL gestures to ensure diversity.
  
## Table of Contents
 
- [File structure](#file-structure)
- [Dataset Summary](#dataset-summary) 
- [Dependencies](#dependencies)
- [Usage](#usage)
- [BibTeX](#bibtex)
- [Our Work](#our-work)
- [Team](#team)
- [Acknowledgments](#acknowledgments)
- [License](#license)
  
   
## File Structure

The data in this work is structured as follows:

```
📦 Dataset.zip
├─ Training (A-Z)    # contains 26 folders containing training data; 700 images for each class/folder
├─ Testing (A-Z)     # contains 26 folders containing test data; 200 images for each class/folder
├─ Validation (A-Z)  # contains 26 folders containing validation data; 100 images for each class/folder
└─ Letters (A-Z)     # contains 26 images for visualization purposes
```
  
## Dataset Summary


|       Name       | Number of Classes |          Images from each class         |    Size on Disk    |
|:----------------:|:-----------------:|:---------------------------------------:|:------------------:|
| RealSign-Dataset |         26        | ~1000 (training + testing + validation) | ~25MB (per class) |

The RealSign folder contains 26 folders with images from each class i.e., ISL fingerspelled alphabets. 

A sample of the dataset for ISL alphabet 'D' is given below:

![ISL signs](https://user-images.githubusercontent.com/56569120/235040509-5a08605a-673e-4139-92a9-aa82bf706b36.png)
  
  
## Dependencies
The dependencies required to use this dataset (_if using python_) are listed below:
- Tensorflow
- Keras
- NumPy 
- Matplotlib
- opencv-python

It is not, however, confined to these libraries. You can utilize whatever works best for you.
  
  
## Usage
The dataset is divided into three main folders: training, testing, and validation. The following Python function can be used to unload the dataset from these directories.

To begin, load the training dataset to your workspace. To mount the dataset, we utilized Google Drive.

```python
# to mount the drive
from google.colab import drive
drive.mount('/content/gdrive')

# to add the specific training data folder
import os
directory = '/content/gdrive/MyDrive/Dataset/Training'
os.listdir(directory) # lists 26 folders from A-Z
```

After uploading the dataset, you may label and preprocess the photos with the following code.

```python
import numpy as np
import tensorflow as tf
from tensorflow import keras
import cv2
    
def load_images(directory):
    images = []
    labels = []
    outputs = 0
    uniq_labels = sorted(os.listdir(directory))

    for idx, label in enumerate(uniq_labels):
        print(label, " is ready to load")
        outputs = outputs + 1
        for file in os.listdir(directory + "/" + label):
            filepath = directory + "/" + label + "/" + file
            image = cv2.resize(cv2.imread(filepath), (128, 128))
            images.append(image)
            labels.append(idx)
    images = np.array(images)
    labels = np.array(labels)

    print(images.shape)
    images = images.astype('float32')/255.0
    labels = tf.keras.utils.to_categorical(labels)
    return(images, labels, outputs)
```
  
To run the function with your directory, use the following command:
  
```python
images, labels, number_of_outputs = load_images(directory)   # file path containing training image data folder
```
  
This function provides numpy arrays with preprocessed images, labels, and the number of photos which can be used to train any neural network or deep learning architecture.
  
  
## BibTeX

If you use our dataset for your work, please consider citing this repository as given below:

```bibtex
@misc{Boggaram_RealSign-Dataset_An_Open-Source,
author = {Boggaram, Aaptha and Boggaram, Ankith and Srinivasa Ramanujan, Ashwin and Sharma, Aryan and R, Bharathi},
title = {{RealSign-Dataset: An Open-Source Indian Sign Language Database}},
url = {https://github.com/RealSign62/RealSign-Dataset}
}
```

## Our Work
  
Consider looking at our systematic literature review on [Sign Language the Translation Systems](https://www.igi-global.com/article/sign-language-translation-systems/311448) before working with this dataset as it will help you find research gaps that can be addressed.

We have used this dataset in another work. It can be viewed in this github [repository](https://github.com/RealSign62/RealSign-Bidirectional_Sign_Language_Translator). 
 
 
## Team
  
Our Team members include: 
- [Aaptha Boggaram](https://www.linkedin.com/in/aaptha-boggaram)
- [Ankith Boggaram](https://www.linkedin.com/in/ankith-boggaram/)
- [Ashwin Srinivasa Ramanujan](https://www.linkedin.com/in/ashwin-sr-355633221/)
- [Aryan Rajesh Sharma](https://www.linkedin.com/in/aryans29/)
 
  
## Acknowledgments

- Special thanks to [Dr. Bharathi R](https://staff.pes.edu/nm1370) for guiding us throughout this initiative.
- We would also like to express our gratitude to [PES University](https://pes.edu/) for giving us the opportunity to present this work.
- Finally, thanks to everyone who supported us!
  
   
## License
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)


