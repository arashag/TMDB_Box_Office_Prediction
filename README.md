# TMDB Box Office Prediction
This dataset is a collection of movie data that contains variables such as budget, genres homepage, original language, popularity, production countries, release date and spoken language.

## Prerequisites
All the required packages along with their version are in the `requirements.txt`. They can be easily installed with following command:

``` pip3 install -r requirements.txt```
## Data Cleaning and Feature Engineering
### genres
Since the genre column contains a string representation of a list, regex has been used to extract the generes from the text and put the results into a list. The reason, I have chosen lists is that a movie can have multiple genres. In addition, a scikit-learn compatible custom transformer have been developed for this and other variables onward. Then CountVectorizer has been used for to convert the movie genres to one hot encoded values.
Result of genre cleaner:
```
array([list(['Comedy']), list(['Comedy', 'Drama', 'Family', 'Romance']),
list(['Drama']), ...,
list(['Crime', 'Action', 'Mystery', 'Thriller']),
list(['Comedy', 'Romance']),
list(['Thriller', 'Action', 'Mystery'])], dtype=object)
```       


### release date
the original dataset release dates had two digit format which can cause ambiguity because we have years from both 20th and 21th century. I converted the years to 4 digit format and developed my model based on it. In this way, my model can be used for any year in 21th century. Moreover, I extracted the year and month of release dates to be used as features in my models

**Since this dataset needed a lot of data cleaning and feature engineering, please consult the jupyter notebook for details of worked done for other variables.**

## EDA
The distribution of movie revenues:

![Revenue Distribution](https://github.com/arashag/TMDB_Box_Office_Prediction/blob/master/TMDB_images/2.png)

The revenue VS original language:

![Boxplot](https://github.com/arashag/TMDB_Box_Office_Prediction/blob/master/TMDB_images/5.png)

The revenue VS release months:

![Boxplot](https://github.com/arashag/TMDB_Box_Office_Prediction/blob/master/TMDB_images/6.png)

Features correlation with target:

![corr plot](https://github.com/arashag/TMDB_Box_Office_Prediction/blob/master/TMDB_images/7.png)


## Modelling and results
### Evaluation Criteria
The criteria prescribed in the Kaggle competition is the sqaure root of mean squared log error which is already available in Scikit-Learn.

### Machine Learning Models
Various models have been used including Random Forest, Gradient Boosting, XGBoost and so on. It was found that Random Forest gives us the best result. The best metric value I could reach is 2.39 on the test set.
