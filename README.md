# BloomingtonPetAdoption

## Overview

ASPCA is looking to use resources in a cost-effective manner to help. Most pets get adopted within a month of the date that they are placed in a shelter. If it takes longer than that and the shelter is full, the animal can be euthanized, but the legal required holding time before euthanization is a week. The purpose of this project is to construct a model that can correctly classify the dogs that have the hardest time getting adopted, so that the shelters can advertise those pets more and push potential adopters towards them.

## Data Understanding

https://bloomington.data.socrata.com/dataset/Animal-Shelter-Animals/e245-r9ub
- 18769 intake entries(each row is an animal)
- 23 columns
- The data cones from the city of bloomington open data portal.

While exploring the data I noticed that there was a little over 6000 duplicated entries so I dropped duplicated but kept the last entry so that we can record the time between the original intakedate and the final movement date. After cleaning the breedname and color columns I split the dats into two dataframes. One for dogs and another for cats. To create the Target variable, I subtracted the original intakedate from the movement date. I then divided my target values into 2 categories. 

__Dogs__ 
  - 1 = Dogs that were adopted in less than 21 days
  - 0 = Dogs that were took longer than 21 days to get adopted

__Cats__ 
  - 1= Cats that got adopted in less than a month
  - 2 = Cats that took longer than a month to get adopted

## Modeling

I experimented with 5 different models. 
- Decision Trees
- Random Forest
- KNNneighbors
- Logistic Regression
- XGBboost

When splitting the data for training and testing, I first put away 15% of it to use as a holdout set, then did 75/25 split with the rest of the data for training and testing.

## Evaluation

After testing the models, Logistic regression gave me a false positive rate of 20%, meaning that it only ignores 20% of the cats that take longer than a month to get adopted, It had precision and accuracy scores of 58% when tested on the holdout set.

The Dog Model had a false positive rate of 56%, but was very good at classifying the dogs that got adopted in less then 3 weeks.(77%)

## Conclusion

Because the models are not as accurate as I would like, I recommend that you use the model in conjunction with your own domain knowledge to help the animals that really need assistance in finding safe homes.
