FACES RECOGNITION PROJECT 

The project consist in the following parts: 

Image preprocessing
 
For the preprocessing of images we have performed the normalization of the images and we have increased the test set by performing the flip operation on the images. By increasing the dataset there are more examples to obtain the characteristics so you have more data to know which are the most important.
 
Feature Extraction We have extracted all the characteristics of the images and then the training will be done.
 
Classifier Training
 
To find the important features we have trained the features with an AdaBoost. To perform this training we have tested with different numbers of weak classifiers and have concluded that from about 30 classifiers the results are quite similar and similar accuracy is obtained giving good results. With 30 classifiers we obtain a training accuracy of 0.98% while the optimal result is obtained with 60 classifiers with an accuracy of 0.99%. On the other hand, with less than thirty classifiers, the results detecting faces were not good. Therefore we have reached the conclusion that 60 the best result is obtained although the time for training is higher (approximately 11 minutes).
 
We have trained 5 classifiers each with a number of characteristics between 5 and 60 characteristics in order to perform the detection of cascading faces.
 

Real-time testing
 
To detect the faces in an image we go through a window through the entire image. For each window we initially extract 5 characteristics and it is predicted with the first classifier. If you predict how expensive the cascade detection continues, increasing the number of characteristics with which we have previously trained. Only those windows that are predicted as faces in all classifiers will be taken as possible faces.
 
Once we have obtained the possible faces there is overlap between positive windows. To solve this we obtain the face with greater probability and apply the function of intersection_over_union with all possible faces that have overlap, and if the intersection between both is greater than 0.5 the face with less probability is discarded because they are possibly the same face. Next, we draw the rectangle of the faces in the image, with the size of the current window for future viewing. Finally we reduce and enlarge the image to detect faces with another size, since the window is fixed size (24x24). If the detected face is smaller than our original window when drawing the rectangle in the original image, it must also be adjusted to the original image.
