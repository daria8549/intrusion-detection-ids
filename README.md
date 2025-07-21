# Data Processing 2: Scalable Data Processing, Legal & Ethical Foundations of Data Science 

## Project Overview
This project develops an Intrusion Detection System (IDS) using machine learning to classify network traffic as normal or malicious. The system leverages the UNSW-NB15 dataset and AlienVault Open Threat Exchange (OTX) for external threat intelligence.

## Instructions
In case you need to start the programms:
1) With IDS you can restart it as you will.
2) With OTX:
    2.1 First Start the OTX_Producer, let it run 
    2.2 Then you start OTX_Consumer,also let it run
    The mora data it collects, the more accurate will be Naive Bayes. (I got it as hight as 43%)
    2.3 Then you stop the OTX_Producer (it has error handling for it)
    2.4 Only then you stop OTX_Consumer (the moment you stop it, it creates new JSON file in the directory)
    Then it just processes the JSON file, and starts training Naive Bayes.

Finally, I'd like to say, that I tried to do as much error handling as possible, but in the end of the day, even in class we encountered many errors with the lab code, often due to poorly followed instructions.

## Model Explanation (Please read it)
- Why Naive Bayes performed poorly?

1) Data collected had many feature vectors that were empty ((5439,[],[])). This likely means that for many rows, the feature extraction process didn’t capture any meaningful data, due to missing or irrelevant entries in the Tags column.

2) I used CountVectorizer to extract features from the Tags column, but the resulting feature space might have been too sparse or didn’t capture enough meaningful variance. This is likely due to vocabulary being large or if the Tags column contained too many general or unimportant terms.

3) Finally Naïve Bayes assumes that features are independent given the class. However, in our dataset, if the features were correlated (e.g., Tags or other columns), this assumption would be violated.

Thats why I decided to try different approach and make use of Random Forest instead. I hoped to improve the model’s ability to correctly classify the data, but I haven't had chance to test it, due to memmory being not enough and constant error "Exception: Java gateway process exited before sending its port number". Which I tried to fix in different ways, but due to the access being restricted for our jupiter profiles, I also haven't had the chance to do so. 

I'll put my Random Forest in text file in data, if you'd be intersted to try it. (Which I guess you're not, but still.)

All in all, I'd like to point out that we have a working dynamic data pipeline, and in a way working Naive Bayes, which is still in my opinion suffucient proof of concept.

## Last Modified
The project was last modified on 14.02.2025.
