# Pi2Cook- An smart Android Application with food ingredient recognition and dish recommendation.

![](https://img.shields.io/appveyor/build/gruntjs/grunt)
![](https://img.shields.io/badge/license-MIT-blue) 
![](https://img.shields.io/badge/Android-7.0%2B-blue)

This is the grauation project of my Bachlor degree of Enginnering in South China University of Technology. A image recoginition Android Application with a recipe recommend systems.

![image](https://github.com/Magicboomliu/Graduation_Project-SCUT-/blob/master/imags/ccc.png)

## Background and introducation  

The reason why I conducted this research is that during the special period like now when everyone stay at home, It was a very troublesome to decide what to cook at home everyday for everyone, and It is not very convenient to buy vegetables outside. So this application with food ingredient recognition and dishes recommend functions can allow user to decide what to cook with the ingredient have already have at home very quickly and convenient.

![image](https://github.com/Magicboomliu/Graduation_Project-SCUT-/blob/master/imags/hahahaha.png)

The picture below is the logic structure of the application, it can both used in the supermarket or at home. First , users take pictures and do ingredient recognition, in the mean time, user can make speech input for supplement and preference settings. Finally, the recommendation system will give recipe recommendation based on both the recognition result and the information that the user provided.
### The MainFunctions of Pic2Cook 
![functions](https://github.com/Magicboomliu/Pic2Cook/blob/master/imags/pic2cookss.jpg)

<br>This figure shows the main functions of the Pic2Cook. The Main functions is Food Ingredient recognition and Dishes Recommendation.There are still other functions like search function will enable user to get plenty of dishes recommendation according the text input or
the speech input; While Weekly feedbacks can show the weekly report of the user's interactions and diet statistics.</br>  
In addition, there is also a Chatbot which provide user a interface to have conversations with the chatbot of Pic2Cook, which will
give user guidance on Cooking and fast jump to the detailed dishes pages.


### Facing Problems and Dataset Preparation

First , About the food ingredient recognition part. The dataset I chose is MV80-Maket , a dataset conducted by Peking University. It has many images with many classes which is big enough to build a ingredient classifier model.
However, there are still some challenging problems in the dataset images 
![image](https://github.com/Magicboomliu/Graduation_Project-SCUT-/blob/master/imags/uploader01.png)
* Coverage problems
* package problems, 
* overexposed problems caused by the light 

## The Food Ingredient Model  
### The YoloV3-SRN hybrid Network  
![image](https://github.com/Magicboomliu/Graduation_Project-SCUT-/blob/master/imags/图片1.png)  
 
###### Just like the picture below, Here I use YOLOv3 as the main detection Networks. And I also add a spatial regularization network to connect to the main network. Next I will call it SRN.   
  <br>The SRN can learn attention maps for each label. The attention masp focus on small activation regions for each category, which associates the related image regions to each labels. The confidence map, what we get from 1 by 1 convolution, consists of many distinctive parameters corresponding to each region. These parameters can re-weight the attention map after we do element-wise multiplication operation with these two maps . After doing that, our model will more focus on the part that the attention maps appears, and find more detail and tiny feature, finally get better performance. It just like we do regularization operation in the images’ spatial domain, that is the reason why it called spatial regularization Network.</br>
  
  ## The Dishes Recommendation Alogorithm
 ![image](https://github.com/Magicboomliu/Graduation_Project-SCUT-/blob/master/imags/Picture1.png)
  After get the food ingredients recognition result and user’s speech input, It is time to build the recommendation system.
First I design a Web crawler to download over 2000 thousand recipes and over 500 user’s data. The users’ data including user’s following list, user’s searching history, user’s basic information and other interactive logs. Then I give each recipe scores according to user’s data and get a User-dishes data set.
After that , first I use the User-based Collaborative filtering algorithm to get a collaborative matrix between target user and potentially similar users. 
Then I encode all the user information, such as age, gender, preference into a high-dimenson vectors, then use a Neural Networks. ,in the picture is NCF to calculate the similarity between the users, and generated a matrix too. Then I add the two matrix and train a Neural Network as a filter to find the most similarity-share group. Then we will do recommendation according to food ingredient ,the user’s speech input and similarity-share groups’ preferences. 

## Other Functions
* You can see other functions in the codes, simple and clear.

-------------------------------------------------------------------------------------------------------------------------------
## Experiments and Results

The figure below shows the evaluation result of the food ingredient recignition and dish recommendation systems
![iMAGE](https://github.com/Magicboomliu/Graduation_Project-SCUT-/blob/master/imags/androidsss.png) ![iMAGE](https://github.com/Magicboomliu/Graduation_Project-SCUT-/blob/master/imags/Picture2.png)

This is the experiments results of the recognition model. I compared the my model with some other object detection structures ,and use mAP, F1-C and F1-O.
 As we can see in this chart, Yolov3-with SRN achieves state of art among the five methods in the data set.
The picture on the right is that I apply this model into an Android Phone . Through It has packages, the model can recognize the food ingredient perfectly. It shows that classifier is strong and robust.  
The Figure also shows evaluation results of the recommend system, I use HR@15 to evaluate the recall rate. As we can see on the chart on the right, the recommend system that I proposed has the best performance compared with ItemCF and UsrCF.

------------------------------------------------------------------------------------------------------------------------
## UI designs and Completed Application
Cool dark mode is applied in this application.  
![iMAGE](https://github.com/Magicboomliu/Graduation_Project-SCUT-/blob/master/imags/finaloutput.png)
![Image](https://github.com/Magicboomliu/Pic2Cook/blob/master/imags/%E4%BF%A1%E6%81%AF%E6%94%B6%E9%9B%86%E5%BC%95%E5%AF%BC%E9%A1%B5.jpg)
### Go to the release page to use this Pic2Cook, make your cook experiences easy and amazing!


  
  
