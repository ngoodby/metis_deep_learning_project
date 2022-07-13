# Metis Deep Learning Project
## Classifying Habitat Types Using Image Recognition

### Abstract

Understanding the types of habitat that animals use and need to survive is key to effectively managing wildlife populations and prioritizing areas for protection and restoration. As human populations and development continue to grow, wildlife habitat continues to be altered and travel corridors for wildlife become increasingly fragmented. To better understand what types of habitat animals are using, we can leverage existing databases that document species occurence and provide photos of animals, such as [iNaturalist](https://www.inaturalist.org/). iNaturalist does not ask contributors to document the habitat type but contributors do contribute photos of the animals they see. Creating a deep learning model that could appropriately label a photo of an animal with its background habitat type would augment this valuable dataset and allow for improved exploration and understanding of habitat associations of various species. This project is a proof of concept of this opportunity that leverages an existing labeled dataset of photos of landscapes and cities. While the labels used in this analysis would not be a good choice for classifying habitat types, the process of model development, evaluation, and implementation would be transferable to other appropriately labeled datasets, once developed. 

### Data & Design

The data was provided by Intel and is a collection of labeled images of natural scenes that can be obtained rom Kaggle [here](https://www.kaggle.com/datasets/puneet6060/intel-image-classification?datasetId=111880&sortBy=voteCount). Each image is assigned to one of six categories: buildings, forest, glacier, mountain, sea, street. There are about 14K images in the training set and 7K in the test set and the classes are well balanced. OpenCV was used to resize the images and prepare the input arrays for modeling. Several convolutional neural network models were trained and tested on a set of validation data. Accuracy was chosen as the key metric for comparison, as the dataset classes are balanced and no one class had more or less importance than the others, given the problem scenario. Final model performance was evaluated on a holdout dataset to understand how the model performed with the various class predictions. 

### Algorithm

Several models were developed and compared. First, a baseline CNN with 7 layers was trained that performed with an accuracy of 0.735 when predicting classes for the validation dataset. A second CNN was develped leveraging the MobileNetV2 weights through transfer learning with three additional dense layers added, leading ultimately to a softmax activation layer that generates the final output. The base model weights were frozen during initial training but final tuning was done by unfreezing the base model weights and training for 10 more epochs with a low learning rate. This led to the model predicting the validation set with an accuracy of 0.897. Lastly, for comparison, a similar model was trained that used the MobileNetV2 weights through transfer learning but additionally implemented image augmentation (shearing, rotation, and zooming). However, performance did not improve as compared to the tuned MobileNetV2 transfer learning model wihtout image augmentation. 

### Tools

- Tensorflow and Keras for deep learning and model development
- Numpy and Pandas for data manipulation
- Matplotlib for visualization
- Scikit-learn for model score reporting

### Communication

- Slides summarizing the project's findings can be found [here](https://github.com/ngoodby/Metis-Deep-Learning-Project/blob/master/deep_learning_slides.pdf)
- A graphic summarizing the final model can be found [here](https://github.com/ngoodby/Metis-Deep-Learning-Project/blob/master/figures/habitat_classifier_with_shape_info.png)
