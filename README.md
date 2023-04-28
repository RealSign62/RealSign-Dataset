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

However, it is not limited to these libraries. You can use what suits best for your work.
  
  
## Usage
The dataset contains folders for training and testing respectively. To unload the dataset from these folders, the following python functions can be used.

```python
import os
import numpy as np
```


## BibTeX



## Our Work


## Team


## Acknowledgments


## License
