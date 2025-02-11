
# Plant Disease Classification

This project uses a custom Convolutional Neural Network (CNN) with six convolutional layers for classifying images from the Potato-plant dataset to detect the disease type of potato plant at an early stage. The project sequence breakdown is as follows:

**Objective-** Detect whether the plant is healthy. If not, detect whether it is of Early Blight, or Late Blight.

**Dataset-** "Plant Village" folder containing respective set of leaf images imported from Kaggle,out of which 80% for Training, 10% for Validation and 10% for Testing is used.

**Data Preprocessing-**
1) *Defining*- BATCH_SIZE = 32; CHANNELS = 3;
 TARGET_IMAGE_SIZE = 256*256; EPOCHS = 30.

2) *Dataset Resizing to* TARGET_IMAGE_SIZE *and Rescaling to* [0,1] , *after Batch Preprocessing with size as* BATCH_SIZE.

3) *Data Augmentation* with *Random Flip*(both horizontal and vertical) and *Random Rotation* between -36 degrees to +36 degrees.

**CNN Architecture-**

- **Convolutional Layers:** For feature extraction and classification.
- **MaxPooling Layers:** For reducing spatial dimension of inputs.
- **Flatten:** To transform the high-level 2D feature map into a one-dimensional vector.
- **Dense:** Actual fully-connected neural network layer for classification. 

| Layer (Activation Function) | Output Shape   | Param #   |
|:---------------:|:------------------:|:------:|
| Conv2D (ReLU)   | (32, 254, 254, 32) | 896    |
| MaxPooling2D    | (32, 127, 127, 32) | 0      | 
| Conv2D (ReLU)   | (32, 125, 125, 64) | 18496  |
| MaxPooling2D    | (32, 62, 62, 64)   | 0      |
| Conv2D (ReLU)   | (32, 60, 60, 64)   | 36928  |
| MaxPooling2D    | (32, 30, 30, 64)   | 0      |
| Conv2D (ReLU)   | (32, 28, 28, 64)   | 36928  |
| MaxPooling2D    | (32, 14, 14, 64)   | 0      |
| Conv2D (ReLU)   | (32, 12, 12, 64)   | 36928  |
| MaxPooling2D    | (32, 6, 6, 64)     | 0      |
| Conv2D (ReLU)   | (32, 4, 4, 64)     | 36928  |
| MaxPooling2D    | (32, 2, 2, 64)     | 0      |
| Flatten         | (256)              | 0      |
| Dense (Softmax) | (64)               | 16448  |

**Total Trainable Parameters-** 183552 

**Optimizer-** 'adam'

## Results

**Training accurary -** 0.9832 ;  **Training loss -** 0.0428

**Validation accuracy -** 0.9762 ;  **Validation loss -** 0.0705

**Testing accuracy -** 1.0 ;  **Testing loss -** 0.0178

From the above values, we can observe that even though there is a drop in values of validation accuracy and raise in validation loss with respect to training accuracy and training loss respectively(which may be arrived due to sparse overfitting occured in the initial training phase), we can visualise that the increase in testing accuracy and significant reduce in testing loss, which depicts the effectiveness of techniques used during the data preprocessing.





## Dataset Download

[Dataset](https://www.kaggle.com/datasets/arjuntejaswi/plant-village)


## Lessons Learned

The major problem arised during the Training time, where the model significantly inclined to overfit. Then Data Augmentation not only helped in enacting as a form of regularization, but also increased the dataset size internally for better generalization, which made the model to get well trained for 30 epochs instead of 50 epochs.

