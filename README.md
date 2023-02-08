# Titanic-Survival
The legendary Titanic ML competition 
The sinking of the Titanic is one of the most infamous shipwrecks in history.
On April 15, 1912, during her maiden voyage, the widely considered “unsinkable” RMS Titanic sank after colliding with an iceberg. Unfortunately, there weren’t enough lifeboats for everyone onboard, resulting in the death of 1502 out of 2224 passengers and crew.
While there was some element of luck involved in surviving, it seems some groups of people were more likely to survive than others.
In this challenge, i build a predictive model that answers the question: “what sorts of people were more likely to survive?” using passenger data (ie name, age, gender, socio-economic class, etc).

The following features with total of 891 entries were provided in the train.csv i.e training set
 
 #   Columns/Features
 0   PassengerId  
 1   Survived  
 2   Pclass  
 3   Name    
 4   Sex     
 5   Age    
 6   SibSp   
 7   Parch    
 8   Ticket   
 9   Fare    
 10  Cabin      
 11  Embarked   


 #   Data Cleaning
In this data cleaning process, the null values in the features 'Age' and 'Cabin' were checked. 20% of 'Age' was null and 'Cabin' had 77% null values. 'Cabin' was deleted as it had almost unique values and didn't provide any meaningful correlation.
The feature 'Age' was found to be correlated with 'Pclass' using a heat map and was imputed using a boxplot based on 'Pclass'. The string valued features 'Name', 'Ticket', 'Embarked', and 'Sex' were one-hot encoded.


For e.g:
 

![image](https://user-images.githubusercontent.com/26757681/201900265-d7791012-7c59-4bda-98ae-4ed5824b6988.png)

Feature 'Embarked' which has 3 categorical entries ('Q','S','C')
Feature 'Sex' which has 2 categorical entries ('M','F')

both of them were one hot encoded with drop_first= True

#   Machine Learning (Training the model)
Imported almost all the popular Classifier Algorithms

test_size was taken as 30%

The accuracy scores were computed as below
![image](https://user-images.githubusercontent.com/26757681/201892074-0d8c64b2-684f-41fe-8f22-52d4cf853d9e.png)
![image](https://user-images.githubusercontent.com/26757681/201893899-bff827c2-d996-46f5-9202-77a42ef18f99.png)

The top three that is  XGB,GB & RF were applied on the test dataset and submitted on Kaggle for scores 

GB submission scored slightly better compared to the other two 

Then did Hyper parameter tuning using Grid_Search_CV  on GB model then applied it on the test dataset and submitted on Kaggle for scores

  Accuracy_score= 0.80143 
  My best on Kaggle so far and ranking is 513/14613  that is top 4% of the total submissions on kaggle for this competiton




 
