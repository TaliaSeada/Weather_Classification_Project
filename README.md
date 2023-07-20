# Weather Images Classification

 ### Data set:
Our data contains 6862 weather images. The dataset is divided into 11 classes: 'dew', 'fogsmog', 'frost', 'glaze', 'hail', 'lightning', 'rain', 'rainbow', 'rime', 'sandstorm' and 'snow'. While some classes contained more images than others. Every image has a different size and is represented with RGB pixels (three dimensions for each image).

### Questions:
1. What are the accuracies of the Models we ran?
2. What method is best for our multi-class data > one vs one OR one vs all?
3. What weather was the hardest to classify?
4. Are there similar weathers so that it was harder for the models to classify? if so, what methods helped?
5. Can reclassifying multiple classes into a single class potentially improve the results of a classification task?
6. Does PCA help?
   
### Answers
1. See in Results.
2. After some research the result was that the one vs rest is better for our strongest model, but not for all the models we used.
3. The hardest class to classify was 2, which is 'frost'. We can also see that it was hard to classify the 6 class, which is 'rain'. In both classes the model confused a lot; the classes that the model was confused about were similar to the 'frost' images for example: rain, snow, and hail. We can see in the images that the colors of these images are similar.
4. According to answer 3, in order to deal with this problem we checked the correlation between the classes and tried to contact a few classes into one, and train the models again on the new data.
5. For the weak models that we trained on our data this action helped and improved the results, but as for our strongest model (Perceptron), it drastically affected badly. We can assume that this wasn't working because we lost some images in order to keep the data balanced.
6. PCA can help improve the complexity of the data, but not necessarily improve the results. This is because of the fact that PCA is removing data. So, in our notebook, we can see that it helped the weak models, we can assume that it happens due to the fact that we reduced the dimensions and the complexity so it helped the simple models, on the other hand, we can see that it badly affected on the stronger models that can deal with the complexity and utilize it.

### Models:
* KNN
* SVM
* Adaboost
* Decision trees
* Perceptron

### Results:
Main notebook: </br>
![image](https://github.com/TaliaSeada/Machine_Learning_Project/assets/78349342/9dab9c70-d348-47d3-88d9-957df130b1cd) </br>

Gray: </br>
![Screenshot 2023-07-20 143424](https://github.com/TaliaSeada/Machine_Learning_Project/assets/78349342/359d3e54-cbe4-41ad-854f-db2615d48e5e) </br>

Combined Classes: </br>
![WhatsApp Image 2023-07-20 at 14 15 48](https://github.com/TaliaSeada/Machine_Learning_Project/assets/78349342/e8872399-829c-4ccd-ab04-cf4c663b5a4f) </br>

One vs One: </br>
![image](https://github.com/TaliaSeada/Machine_Learning_Project/assets/78349342/9bd9a881-dd05-491d-9a18-146a8d7eb7a8)

### difficulties throughout the project:
1. Imbalanced data - we balanced the data by duplicating using the flip method on the images of some classes, and reduced the number of images in other classes by not taking all the images.
2. Null files - removed.
3. The models were weak.
4. Machine Learning models work better for different types of datasets, for our dataset Deep Learning works better - we wanted to research the machine learning models on this data specifically.

#### The methods we tried:
1. __Dimension reduction:__ In order to reduce the dimensions we tried using the PCA method, as we can see in the results for some models it outperformed but for the strongest model we have it affected it significantly.
2. __gray scale / RGB:__ As part of the dimensions reduction we tried working with grayscale images but the results were much worse because we lost a lot of important information, colors add meaning to weather images. (see in the Gray notebook)
3. __one vs one / one vs rest:__ Since our data is divided into 11 classes we wanted to check which method works best for it, so we tried the one vs one method but the results were better when we tried the one vs rest method (which is the default method in SKlearn)

### Models:
_Why KNN model is weak for our data?_
1. Environment importance: The KNN model calculates the distance between the features which are the pixels in each image, by doing this it completely ignores the neighborhood so it loses a lot of information, and this leads to weak results.
2. Sensitivity to irrelevant features: KNN gives all features the same weight when calculating distances between the pixels. In images, there can be irrelevant or noisy pixels that make the classification harder.
3. Unequal feature importance: Not all pixels in images may have the same information importance for classification. KNN treats all features equally without considering their importance.

_Why SVM model is weak for our data?_
1. The SVM tries to separate the data by using hyperplane, while the images have many dimensions which makes the separate problem more complex.
2. Non-linear Relationships: SVM is designed for linear classification problems. SVM struggles to capture and model such complex non-linear patterns as weather images effectively, leading to weaker performance.
3. Small Training Dataset: SVM performs best when provided with a big amount of labeled training data. But the amount of data that we currently have is small compared to the amount that the SVM need.

_Why DecisionTree model is weak for our data?_
1. Lack of information: Decision trees make decisions based on individual features, without considering the spatial arrangement of those features.
2. High-dimensional data: images typically have high-dimensional data for example color dimensions or pixels. Decision trees may struggle to handle such high-dimensional data effectively.
3. Limited modeling capability: Decision trees have limited modeling capability compared to more complex models like deep neural networks. They may struggle to learn complex and nonlinear problems.

_Why AdaBoost model is weak for our data?_
1. Not meaningful weak classifiers: As we studied AdaBoost uses weak classifiers that are better than random guessing. Weather images contain complex patterns or features that might be difficult for weak classifiers to capture accurately.
2. Sensitivity to noise and outliers: Weather images may contain noise or outliers, that can affect the Adaboost accuracy since AdaBoost is sensitive to noisy data.

_Why the Perceptron model is __good__ for our data?_
1. Perceptrons are versatile. They can be used to classify images of different sizes and resolutions.
2. perceptrons have some specific advantages for weather image classification. For example, perceptrons can be used to classify images based on their color, texture, and shape.
