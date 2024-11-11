# ResNet_Vgg16_AlexNet_Cifar100

# Introduction
- Overview of the Problem: 
Explain the challenges of image classification and the 
importance of CIFAR-100 in evaluating model performance.
- Purpose of Comparison: State the motivation behind comparing VGG-16, AlexNet, 
and ResNet, focusing on their distinct architectures and suitability for image 
classification tasks.
# Background
- VGG-16: Detail the sequential architecture with deeper layers, emphasizing 
the use of small filters and multiple convolution layers.
- AlexNet: Describe AlexNet's pioneering use of convolution layers and ReLU 
activations, making it suitable for image recognition.
- ResNet: Discuss the introduction of residual connections to solve the 
vanishing gradient problem, which allows for deeper networks without 
performance degradation.
# Method
## Dataset Preparation:
1. Explain the CIFAR-100 dataset 
2. Including training, validation, and test splits.
3. Data augmentation on train
4. resizing shape of images from 
(32,32,3) to (224,224,3) to be appropriate for models

# ResNet
How does ResNet work?
Let us now understand how ResNet works. Here, we have something called 
Residual blocks. Many Residual blocks are stacked together to form a ResNet. We 
have “skipped connections” which are the major part of ResNet. The following 
image was provided by the authors in the original paper which denotes how a 
residual network works. The idea is to connect the input of a layer directly to the 
output of a layer after skipping a few connections. We can see here, x is the input to 
the layer which we are directly using to connect to a layer after skipping the identity 
connections and if we think the output from identity connection to be F(x). Then we 
can say the output will be F(x) + x.

![1_D0F3UitQ2l5Q0Ak-tjEdJg](https://github.com/user-attachments/assets/74513e5f-e706-41eb-bf01-c57a4ff55ba8)

## The identity block
The identity block is the standard block used in ResNets and corresponds to the 
case where the input activation (say a[l]) has the same dimension as the output 
activation (say a[l+2]). To flesh out the different steps of what happens in a ResNet's 
identity block, here is an alternative diagram showing the individual steps:
*Identity block* Skip connection "skips over" 2 layers.

<img width="591" alt="idblock2_kiank" src="https://github.com/user-attachments/assets/83f577db-7f25-4eac-b3b4-7bc9b4e4368a">
The upper path is the "shortcut path." The lower path is the "main path." In this 
diagram, we have also made explicit the CONV2D and ReLU steps in each layer. To 
speed up training we have also added a BatchNorm step.

**Identity block. ** Skip connection "skips over" 3 layers.
<img width="729" alt="idblock3_kiank (1)" src="https://github.com/user-attachments/assets/5ed78ed2-5ca0-4609-8cbd-b059c039b3fa">

## ResNet model (50 layers)
The following figure describes in detail the architecture of this neural network. "ID 
BLOCK" in the diagram stands for "Identity block," and "ID BLOCK x3" means you 
should stack 3 identity blocks together.
<img width="698" alt="resnet_kiank" src="https://github.com/user-attachments/assets/f150e3d2-b9cd-446b-ab23-60358b99b7fb">

# AlexNet
A deeper architecture that includes multiple convolutional layers with pooling, 
dropout, and dense layers, adjusted to work on CIFAR-100. The architecture is 
comprised of eight layers in total, out of which the first 5 are convolutional layer and 
the last 3 are fully connected. The first two convolutional layers are connected to 
overlapping max-pooling layers to extract a maximum number of features. The third, 
fourth, and fifth convolutional layers are directly connected to the fully connected 
layers. All the outputs of the convolutional and fully connected layers are connected 
to ReLu non-linear activation function. The final output layer is connected to a 
softmax activation layer, which produces a distribution of 1000 class labels in 
CIFAR-100, the output layer only has 100 class labels.

![1_0dsWFuc0pDmcAmHJUh7wqg](https://github.com/user-attachments/assets/74e7a972-dc4e-489b-9b81-22357637cb39)

# VGG16
The VGG-16 model is a convolutional neural network (CNN) architecture that was 
proposed by the Visual Geometry Group (VGG) at the University of Oxford. It is 
characterized by its depth, consisting of 16 layers, including 13 convolutional layers 
and 3 fully connected layers

![0_yOUk3vyhY_qimwMg](https://github.com/user-attachments/assets/d4027dc7-1b86-4ce4-bc23-33af0bea7cdd)


# Results and Accuracy Comparison
To evaluate the effectiveness of ResNet, AlexNet, and VGG16 
architectures on the CIFAR-100 dataset, we used Top-1 and Top-5 
accuracy metrics. The results are presented in the bar chart below, 
showcasing the performance differences among the models.
Top-1 and Top-5 Accuracy Results:
- ResNet reached the highest accuracy with Top-1 accuracy of 
51.62% and a Top-5 accuracy of 80.12%.
- VGG16 achieved a Top-1 accuracy of 49.83% and a Top-5 
accuracy of 78.59%.
- AlexNet scored 44.81% in Top-1 accuracy and 73.32% in Top-5 
accuracy

![Screenshot 2024-11-11 005714](https://github.com/user-attachments/assets/3a48ed72-74a6-4ecb-9e50-01d146502046)






