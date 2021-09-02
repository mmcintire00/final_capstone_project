## USING NEURAL NETWORKS AND SATELLITE IMAGERY TO IMPROVE FLOOD DAMAGE ASSESMENTS

### BACKGROUND
Climate change is considered the greatest threat to society in the coming decades and will have far reaching effects on weather patterns, regional climates, wildlife, agriculture, property, and many other aspects of life on Earth. The planet is already experiencing some of the effects of climate change. In the western US, water is becoming scarcer, and fire season is lengthening and getting more costly [5]. In the South Pacific, people are being forced from their homes due to rising sea levels and lack of drinking water [6]. Along the Gulf coast of the US, residents must endure more frequent and stronger hurricanes capable of causing catastrophic flood damage. In August 2017, the Texas Gulf coast was hit by Hurricane Harvey. Harvey made landfall on August 25th in Rockport, Texas as a category 4 storm. Over the next 5 days Harvey stalled over the Houston Metro area and dumped more than 27 trillion gallons of water on southeastern Texas. Some parts of Houston received up to 50 inches of rain during the storm [7]. The catastrophic flooding caused by the storm resulted in an approximately $125 billion in damage to properties and businesses in southeastern Texas. This is the second costliest storm in US history, only behind Hurricane Katrina in 2005.

### PURPOSE
As the effects of climate change continue to accelerate in the coming years, cleaning up after a natural disaster will become more complicated and costly. In the aftermath of Hurricane Harvey, many homes and businesses were severely damaged due to intense flooding. THE PROBLEM: Insurance companies and FEMA traditionally must drive through these areas to assess the damage and understand the economic costs. This can be a time consuming, expensive, and frequently dangerous task. SOLUTION: This study will attempt to improve the evaluation process using available satellite imagery and neural networks to identify areas affected by flooding. PROJECT VALUE: This study will be of great value for both the federal government and insurance companies who need to assess the costliness of a natural disaster. It can be implemented to help focus efforts on affected areas, cutting down the time an agent spends in a particular area and decreasing travel costs and potential harm.

### DATA
This dataset was taken from Kaggle.com [3] and was originally published on the IEEE website [1]. The authors of the dataset also wrote a paper detailing their approach and findings [2].  The data contains 23000 images of both damaged and undamaged classes. The data is broken into both training and test datasets. 

![data_distribution](https://user-images.githubusercontent.com/80219614/131153907-6257ef88-ad67-4b39-adb1-38c71f1ce13a.jpeg)

The figure above shows the distribuiton of the two classes of data. There are 23000 total images, with 15000 images classified as "damage" and 8000 images classified as "no_damage."

![data_location](https://user-images.githubusercontent.com/80219614/131153819-f911dd47-e5ad-4cbe-ba29-b7d33abad011.jpeg)

The locations of the data points can be observed on the map of SE Texas above. There are three primary locations that the data was collected. The first is Rockport, Texas where Hurricane Harvey made landfall as a category 4 hurricane. There are datapoints collected around the Houston Metro area where some of the greatest impacts of flooding were observed. And finally on the Texas-Lousiana border near Beaumont, Texas which also saw devistating flood damage.

### RESULTS

Comparing confusion matrices between models and looking at accuracy scores and run times, the AlexNet model provides the best results for predicting both the majority and the minority classes. The recall values for damage and no_damge are .89 and .92, respectively.

![loss_accuracy](https://user-images.githubusercontent.com/80219614/131872378-4650e727-a1b2-4aee-a5fe-ce08e49eaa6f.png)

![cm_test_ann](https://user-images.githubusercontent.com/80219614/131872398-4f0bc727-03a3-40b7-b871-d4ad05937d60.png)

![models](https://user-images.githubusercontent.com/80219614/131872411-3153252e-1675-43ac-905d-504765b24421.png)

### CHALLENGES 

The biggest challenge I faced during this project was dealing with what I assume is data leakage in the model. Comparing the model results on the training data and the test data, there are some interesting descrepancies between when evaluating the training data and testing data. I've stratified my data split on the labeled data, as well as looked at the different sized splits (80-20,70-30, 60-40), augmenting images, and making sure the class proportion remains the same between the train and test, the issue still persists. This will be something I will continue to investigate.

### FUTURE WORK

* Testing models with images from Google Earth and Google Images
* Additional adjustment of AlexNet and CNN Model #2 to improve performance of models
* Dashboard build in Ploty/Dash
* Web based app using Heroku

### DEPLOYMENT

This model could be deployed in a couple of different ways. It could be deployed at scale as an ArcGIS module that could be applied to larger satellite imagery sets. I assume this would be the best way to implement for a large insurance company or the federal government. A simpler way to deploy this model would be to build a web based image classification app using Heroku. The premise of this app would be that you input your own satelite image and the app will tell you if it is damaged or not. A potential downside to this approach is that if you put in an image that does not have a building with or without damage, the app will likely not understand that the image is not a damage/no_damage home and provide a incorrect classification.

### SOURCES
[1] Original Dataset: https://ieee-dataport.org/open-access/detecting-damaged-buildings-post-hurricane-satellite-imagery-based-customized

[2] Original Dataset paper: https://arxiv.org/abs/1807.01688

[3] Kaggle Dataset: https://www.kaggle.com/kmader/satellite-images-of-hurricane-damage

[4] Nasa Climate Change Research: https://climate.nasa.gov/

[5] Western US Fires: https://climate.nasa.gov/blog/3066/the-climate-connections-of-a-record-fire-year-in-the-us-west/

[6] Rising Sea Levels (Kiribati): https://www.nytimes.com/2016/07/03/world/asia/climate-change-kiribati.html

[7] Hurricane Harvey facts: https://tdem.texas.gov/hurricane-harvey-dr-4332-2/c

[8] Texas counties shapefile (TXDOT): https://gis-txdot.opendata.arcgis.com/datasets/texas-county-boundaries-detailed/explore?location=31.168805%2C-100.077018%2C6.70

[9] Guide to CNN: https://towardsdatascience.com/a-comprehensive-guide-to-convolutional-neural-networks-the-eli5-way-3bd2b1164a53

[10] Kaggle Computer Vision Course: https://www.kaggle.com/learn/computer-vision

[11] IBM Computer Vision Explanation: https://www.ibm.com/topics/computer-vision

[12] IBM CNN Explanation: https://www.ibm.com/cloud/learn/convolutional-neural-networks


