# BloomingtonPetAdoption

## Overview

ASPCA is looking to use resources in a cost-effective manner to help. Most pets get adopted within a month of the date that they are placed in a shelter. If it takes longer than that and the shelter is full, the animal can be euthanized, but the legal required holding time before euthanization is a week. The purpose of this project is to construct a model that can correctly classify the dogs that have the hardest time getting adopted, so that the shelters can advertise those pets more and push potential adopters towards them.

Information about the legal holding time for animal shelters can be found on this [animal law](https://www.animallaw.info/topic/state-holding-period-laws-impounded-animals#:~:text=These%20laws%20provide%20the%20minimum%20required%20period%20that,holding%20period%20runs%20from%20five%20to%20seven%20days.) website.

## Notebook Sequence
1.  EDA Cleaning Notebook
2.  Main Notebook
3.  You can then look at additional visualizations in the visualization notebook

## Data Understanding

The dataset that I used can be found [here](https://bloomington.data.socrata.com/dataset/Animal-Shelter-Animals/e245-r9ub)
  - After clicking the link you can click the export button in the top right corner to download the data as a CSV.
  - This is an open portal so the data is constantly being updated
  - I downloaded the data 11/16/21 so it will look a little different from the current dataset


### Description of the dataset
- 18769 intake entries(each row is an animal)
- 23 columns
- The data cones from the city of bloomington open data portal.
 

Dogs take up more space on average than cats, so the dog sections can run out of space quicker than the cat sections. That's why I am using 21 days as the standard for dog adoption speed and using a month as the cutoff point for cat adoption speed. More information about the space requirements for dogs and cats can be found [here](https://www.maddiesfund.org/design-for-shelter-animals.htm)

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

## Recommendations

- Release literature addressing the stigma about black cats
- Make more use of the media to portray pitbulls in a different light
- Stage animals with unfavorable characteristics in areas that get the most customer traffic

## Conclusion

Because the models are not as accurate as I would like, I recommend that you use the model in conjunction with your own domain knowledge to help the animals that really need assistance in finding safe homes.

### Shelter population
![graph1](https://github.com/wharr1203/BloomingtonPetAdoption/blob/main/Images/shelter.png)

### Top 3 breeds that get put to sleep
![graph2](https://github.com/wharr1203/BloomingtonPetAdoption/blob/main/Images/dogs.png)

### Colors of cats that had trouble getting adopted
![graph3](https://github.com/wharr1203/BloomingtonPetAdoption/blob/main/Images/cats.png)
