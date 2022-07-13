# Metis Deep Learning Project
## Classifying Habitat Types Using Image Recognition

### Abstract

Understanding the types of habitat that animals use and need to survive is key to effectively managing wildlife populations. As humans and our 

### Design

### Data

The data was provided by Intel and is a collection of labeled images of natural scenes that can be obtained rom Kaggle [here](https://www.kaggle.com/datasets/puneet6060/intel-image-classification?datasetId=111880&sortBy=voteCount). Each image is assigned to one of six categories: buildings, forest, glacier, mountain, sea, street. There are about 14K images in the training set and 7K in the test set and the classes are well balanced. OpenCV was used to resize the images and prepare the input arrays for modeling. 

### Algorithm

Several convolutional neural network models were trained and tested. Accuracy was chosen as the key metric for comparison, as the dataset classes are balanced and no one class had more or less importance than the others given the problem scenario. A baseline CNN with 7 layers performed with an accuracy of 0.735. A second CNN was develped leveraging the MobileNetV2 weights through transfer learning with three additional dense layers added, leading ultimately to a softmax activation layer to generate the final output. The base model weights were frozen during initial training but final tuning was done by unfreezing the base model weights and training for 10 more epochs with a low learning rate. For comparison, a similar model that used the MobileNetV2 weights through transfer learning was created that implemented image augmentation (shearing, rotation, and zooming) but performance did not improve. 

### Tools

- Tensorflow and Keras for deep learning and model development
- Numpy and Pandas for data manipulation
- Matplotlib for visualization
- Scikit-learn for model score reporting

### Communication

- Slides summarizing the project's findings can be found [here](https://github.com/ngoodby/Metis-Deep-Learning-Project/blob/master/deep_learning_slides.pdf)
- A graphic summarizing the final model can be found [here](
