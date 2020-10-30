# Capstone Project: Convolutional Neural Network Furniture Image Classifier

# 1. Background

Carousell is a marketplace for buying and selling secondhand goods. They operate in Singapore, Malaysia, Philippines, Cambodia, Taiwan, Hong Kong, Macau, Australia, New Zealand and Canada.

As of 2016, over 23 million items have been sold on the platform and has a total listing of over 57 million items, both used and new. Carousell has also successfully received mulitple rounds of investments from multiple investors, which are all indicators of a fast growing firm that heavily relies on their consumers and the experiences they gain from using their platform.

[Information from Wiki] :https://en.wikipedia.org/wiki/Carousell_(company)#History

# 2. Problem Statment
The recent increase in listings of items on our Carousell platform due to the pandemic, has highlighted certain pain points faced by our consumers. The team at Carousell have been noticing an increase in sellers postings and listing items in the wrong categories to increase their listings exposure in the hopes of increasing their chances of making a successful sale. While most wrongly classified listings are usually closely related, This would still negatively affect consumers' user experiences as they are unable to effectively shop and search for specific items due to the “noise” wrongly classified listings. This is a major problem as the company’s main focus is providing a platform that matches sellers to buyers, if the process for either party isn’t smooth and efficient, this may lead to a decrease in users on both ends. Hence, this issue of wrongly classified postings has to be dealt with efficiently and effectively.

As such, the Data Team has been tasked to develop possible methods to help minimise such incidents from happening on the platform. The team has decide to conduct a pilot test to examine if Deep learning Convolutionary Neural Network(CNN) Image Classification Model could be one of the methods deployed to combat the misclassification of listings. The model will be evaluated on its confusion matrix and the calculations that come out of it(accuracy, sensitivity, specificity and precision).

As there is no particular importance in which class(furniture item) is more important than the other, accuracy scores will be our main focus in determining which model is the best performer. If the model was deemed to be a success, it could be systematically deployed across the different categories to combat the issue of incorrect listings.

# 3. Data
The data for a CNN model comes in the form of images in both jpg and jpeg formats. As images were scrapped using a google extension where the sizes(height,width) can be filtered, there will not be a need to check if there are any outliers in terms of size. Table and bed are meant for training the CNN model, while REAL_POSTS_table and REAL_POST_bed are images directly from Carousell's recent listings and will be used to check the accuracy of the best CNN model.
 
 
The data comes in 1 folder with 4 subfolders:
 
    1.Table
        -Approximately 1200 images of tables.
        -Different backgrounds(White and fully furnished settings).
        -Shapes/Material(Round, rectangular, square, wooden, glass, mat and gloss finish).
 
    2.Bed
        -Approximately 1200 images of beds.
        -Different backgrounds(White and fully furnished settings).
        -Size/Material(Queen, Single and bed frames).

    3.REAL_POSTS_table
        -3 images of tables.
        -Different backgrounds(White and fully furnished settings).
        -Shapes/Material(Rounded oval shape, rectangular and wooden).

    4.REAL_POSTS_bed
        -3 images of beds.
        -Different backgrounds(fully furnished settings and low lighting settings).
        -Size/Material(Queen, Single, bed frames).

    5.Weights
        -Weights saved from the best model.
        
# 4. Excutive Summary
CNN model using Transfer learning with data augmentation was the best performer with the highest score of 98.03%, it was always to predict with 100% accuracy listing taken from Carousell platform itself. Proving that the pilot test in using CNN image classifier to solve the problem statement is successful.
## 4.1 Project Approach
### 4.1.1 Preprocessing 
The goal of this section would be to process the jpeg and jpg files into a formatted numpy array ready to be fed into the CNN models. With the main flow being as such:

	1.Creating a list of paths of each image
	2.Creating a main dataframe of all images
	3.Reading each path and converting them into numpy array
	4.Resizing and rescaling(colour)
	5.Train Test Split
	6.Reshaping arrays of both X and y to resemble
        -X:(No. Of images, width, height, RGB)
		-y:(No. Of images,labels)
 
### 4.1.2 Modeling and Model Evaluation 
In this section, the goal is to find a CNN model that achieves the highest accuracy scores. Each CNN model will be finetuned with regularization, padding and amount of layers, transfer learning and data augmentation will also be explored as 1200 images per class is considered to be too small to achieve models with a higher accuracy.  VGG16 will be used as the transfer learning as it seems to be the most popular for classifying furniture. A more detailed examination of what each layer of the transferred learning CNN model will be performed to better understand what goes behind the scenes of a CNN model. 

The main workflow will be as such:

    1.Finalise Number of Layers (1, 2 or 3)
    2.Add Regularization(Dropout, L1 or L2)
    3.Implementation of Data Augmentation
    4.Implementation of Transfer learning 
    5.Model Evaluation 
    
### 4.1.3 Model Predictions on Real Listings
The goal in this section is to prove the deployability of using a CNN image classifier to tackle the problem statement of having over exposed listings. Images of real listings from both categories of tables and beds have been chosen as the proof of concept to test out the CNN model with transfer learning. Images chosen have been selected to represent the vast differences found in listings(with and without background and photos that don’t show the entire item)

Main Workflow:

    1.Import weights 
    2.Importing images
    3.Creating a dataframe
    4.Reading, resizing and re-scaling of images
    5.Reformatting numpy array formats
    6.Predicting using imported model weights
    
# 5 Conclusion, Reccomnedation and Limitation
All models performed better than the baseline of 52%, however, the model using transfer learning with data augmentation performs the best with an accuracy score of 98.03% and has been proven that the model works on real life post from the platform itself with 100% accuracy. With this model, the team is able to successfully meet the objectives stated in the problem statement of using a CNN imgage classifier model as a pilot test to prove that it is indeed possible to develop a model that is able to classify items with great accuracy.

Transfer learning can continue to be applied to item categories that are easier to differentiate such as furniture, however, with more intricate items like electronics, a custom model with data augmentation might be able to classify such items. The Data team can also tap into the 57 million items posted and use that in conjunction with widely available resources to build a model to help a more robust and accurate CNN image classifier model.

There are multiple limitations of this project, this would particularly affect the models that are built from scratch. Due to the method used to scrape google images, there are some random photos that are not related to the item category at all that was found in the datasets. Another limitation was having duplicates of the same photo, and the limited photos available on google.

