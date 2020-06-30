# CNN Microchip Classification
## Table of contents
1. [Introduction](#introduction)
2. [Task Description](#taskdes)
3. [Dataset](#data)
4. [Implementation](#imp)
5. [Result](#result)
<br/>

<a name="introduction"></a>

## Introduction
This is a task given by ViTrox Sdn Bhd on its interview for CS fresh graduates. The interviewer asked to develop a simple model on recognising images in a dataset provided by them. The candidates are required to spend less than one week to produce the model. The model produced is hence shown in this repository.

<a name="taskdes"></a>

## Task Description
The task given is named Microchip Abnormaly Detection, while the actual task itself is just image classification. Candidates are required to train a model which can provide prediction on input image(es) to give a class label from a total of 4 classes to it. The classes required are as followed:
- Capacitor
- Sot
- Resistor
- Unknown

<a name="data"></a>

## Dataset
The dataset given is promised to be destroyed as soon as completion of the project for confidentiality. The dataset provided by ViTrox consists of 1820 labelled images, while Unknown images are further subcategorised. The dataset is being split into 70:30 (1274:546) for training and testing data.

<a name="imp"></a>

## Implementation

### Data preprocessing
The data is first being resized into the smallest length of all dimension which is 27 * 27. The images are also converted into grayscale for ease of training (decrease weight counts.) Before the training data is fed into the model for training, it is fed into image data generator for data augmentation. In this case, the parameters are as followed:
- Rotation range: 5 degrees
- Zoom range: 5%
- Width shift range: 5%
- Height shift range: 5%

### Validation
K-fold is being used in the training as the data size is considered small, hence procuding different models with a higher variety of data, and get the mode of their prediction (inspired by random forests algorithm) is assumed that they will give a higher accurancy prediction. In this case, K value is assigned to 10 for it has the highest accuracy result.

### Model
The model used is Convolutional Neural Network with 10 layers. 

![CNN model](./images/nn.jpg 'Convolutional Neural Network with 10 layers')

Parameters used:
- Epochs: 15
- Batch size: 16

<a name="result"></a>

## Result
![Validation Result](./images/val.png 'Validation')
![Confusion Matrix](./images/cm.png 'Confusion Matrix')
| Class | Precision | Recall | F1 Score |
| --- | --- | --- | --- |
| Capacitor | 0.988 | 1.0 | 0.994 |
| Resistor | 0.948 | 0.991 | 0.969 |
| Sot | 0.904 | 0.988| 0.944 |
| Unknown | 0.996 | 0.944 | 0.969 |

<dl>
<dt>Final result</dt>
<dd>
<ul>
<li>Tested Accuracy on 546 Test Data: 0.96886 (96.9%)
<li>2 Mins Training Time
</ul></dd>
</dl>