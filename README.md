# RealSign-Dataset: An Open-Source Indian Sign Language Database
This repository contains a collection of images of Fingerspelled Indian Sign Language (ISL) alphabets.
  
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
📦 Dataset
├─ Training (A-Z)   # contains 26 folders containing training image data, one for each class 
├─ Testing          # contains 26 folders containing testing image data, one for each class 
└─ Letters          # contains 26 images for visualization purposes
```

## Dataset Summary


|       Name       | Number of Classes |   Images from each class   |    Size on Disk    |
|:----------------:|:-----------------:|:--------------------------:|:------------------:|
| RealSign-Dataset |         26        | ~1000 (training + testing) | ~100MB (per class) |

The RealSign folder contains 26 folders with images from each class i.e., ISL fingerspelled alphabets. 4 signers have contributed in capturing these images and have contributed equally for each class.

A sample of the dataset for ISL alphabet 'D' is given below:

![ISL signs](https://user-images.githubusercontent.com/56569120/235040509-5a08605a-673e-4139-92a9-aa82bf706b36.png)

## Dependencies
The dependencies required to use this dataset (_if using python_) are listed below:
- Python
- Tensorflow
- Keras
- NumPy 
- Matplotlib
- opencv-python
- os
- cv2

However, it is not limited to these libraries. You can use what suits best for your work.
  
  
## Usage
The dataset contains folders for training and testing respectively. To unload the dataset from these folders, the following python functions can be used.

First, unload the training dataset in your workspace. We used Google Drive to mount the dataset.

```python
# to mount the drive
from google.colab import drive
drive.mount('/content/gdrive')

# to add the specific training data folder
import os
directory = '/content/gdrive/MyDrive/Dataset/Training'
os.listdir(directory) # lists 26 folders from A-Z
```

Upon uploading the dataset, you can label these images and preprocess them using the following two functions.

```python
import numpy as np
import tensorflow as tf
from tensorflow import keras

# the following function is used to shuffle the dataset after preprocessing
# # Can be considered as an optional step
def unison_shuffled_copies(a, b):
    assert len(a) == len(b)
    p = np.random.permutation(len(a))
    return a[p], b[p]
    
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
            # x=random.randint(96,2000);
            # y=random.randint(96,2000);
            image = cv2.resize(cv2.imread(filepath), (128, 128))
            # image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
            images.append(image)
            labels.append(idx)
    images = np.array(images)
    labels = np.array(labels)

    images, labels = unison_shuffled_copies(images, labels)

    # images = images.reshape((len(images), 96, 96, 1))
    print(images.shape)
    images = images.astype('float32')/255.0
    # labels = tensorflow.keras.utils.np_utils.to_categorical(labels)
    labels = tensorflow.keras.utils.to_categorical(labels)
    return(images, labels, outputs)
```


## BibTeX



## Our Work


## Team


## Acknowledgments


## License
