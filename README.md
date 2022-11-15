# Titanic-Survival
The legendary Titanic ML competition 
The sinking of the Titanic is one of the most infamous shipwrecks in history.
On April 15, 1912, during her maiden voyage, the widely considered “unsinkable” RMS Titanic sank after colliding with an iceberg. Unfortunately, there weren’t enough lifeboats for everyone onboard, resulting in the death of 1502 out of 2224 passengers and crew.
While there was some element of luck involved in surviving, it seems some groups of people were more likely to survive than others.
In this challenge, i build a predictive model that answers the question: “what sorts of people were more likely to survive?” using passenger data (ie name, age, gender, socio-economic class, etc).

The following features with total of 891 entries were provided in the train.csv i.e training set
 
 #   Column       Non-Null Count  Dtype  
---  ------       --------------  -----  
 0   PassengerId  891 non-null    int64  
 1   Survived     891 non-null    int64  
 2   Pclass       891 non-null    int64  
 3   Name         891 non-null    object 
 4   Sex          891 non-null    object 
 5   Age          714 non-null    float64
 6   SibSp        891 non-null    int64  
 7   Parch        891 non-null    int64  
 8   Ticket       891 non-null    object 
 9   Fare         891 non-null    float64
 10  Cabin        204 non-null    object 
 11  Embarked     889 non-null    object





And then blindly had a look on how whether any of the feature had any null values

  Features: 'Age' & 'Cabin', 20% of 'Age' were null whereas 'Cabin' had around 77% which is huge

Since 'Cabin' is the main issue here, i had to check whether it is of catergorical or continuous type

  It was categorical but almost had unique values like for 80% of the dataset and rest were redundant entries.
  
  So it was meaningless and any correlation coming out of it also wouldn't make any sense hence 'Cabin' feature deleted.
  
Then coming to "Age" , i did just plot a heat map wherein it correlated well with the feature "Pclass" which is the Passenger Class which has 3 categorical entries (1,2,3)

So immediate plan that came to mind is to do boxplot for both of these, so that i can map the values accordingly 
For e.g:
  
  def agemap(x):
    age=x[0]
    pclass=x[1]
    if np.isnan(age):
        if pclass ==1:
            return 38
        elif pclass==2:
            return 29
        else:
            return 25
    else:
        return age
    
train['Age']=train[['Age','Pclass']].apply(agemap,axis=1)


Not just an example, it's the actaul code used. simple.

Then for any dataset to be fed into Machine Learning Model it should be numerised or one hot encoded.

And in this case we have the features "Name","Sex","Ticket","Embarked" which had string values.

Out of these "Name" & "Ticket" are totally unique for each of the entries and not required since we can refer the entry by "PassengerId" feature

Deleted "Name" & "Ticket"

Feature 'Embarked' which has 3 categorical entries ('Q','S','C')
Feature 'Sex' which has 2 categorical entries ('M','F')

both of them were one hot encoded with drop_first= True

imported almost all the popular Classifier Algorithms

test_size was taken as 30%

![image](https://user-images.githubusercontent.com/26757681/201892074-0d8c64b2-684f-41fe-8f22-52d4cf853d9e.png)

  LGBM	Light Gradient Boosting
  MNB	  Multinomial NB
  XGB	  XGBoost
  RF	  Random Forest
  AB	  Ada Boost
  GB	  Gradient Boosting
  LOG	  Logistic Regression
  SGD	  Stochastic gradient descent
  DT	  Decision Trees
![image](https://user-images.githubusercontent.com/26757681/201892134-cb2820c1-e866-4bc0-a6de-4130aeb0d3d0.png)


 On plotting the heatmap for all the features  





 


My highest kaggle score as of now is 0.80143
and ranking is 513/14613  that is top 4% of the total submissions on kaggle for this copmpetiton
