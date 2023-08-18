# Analyzing Pop Music Genre Classification Using Logistic Regression and K-Nearest Neighbors Based on Spotify's Audio Features

*Tools: Python*

![spotify-1](https://github.com/katlynkenisha/Spotify/assets/109913754/d6361a54-4e58-4085-af62-e0c42caa8151)

## Introduction
I completed this project as the final requirement for my Mathematics degree.

This research aims to compare the predictive performance of supervised learning algorithms, specifically Logistic Regression and K-Nearest Neighbors (KNN), for the classification of pop music based on Spotify's audio features.

## Methodology
### 1. Data Collection
The dataset consists of 5000 randomly selected tracks stored in a Spotify playlist. A function is used to extract audio features for each track. The code to extract these features can be found inside the ‘code’ folder.

### 2. Data Preparation
#### Data Cleaning
Data cleaning involves eliminating duplicate tracks, removing tracks without any genre information, and selecting tracks released between 2010-2019.

#### Data Preprocessing
Data preprocessing involves converting track duration from milliseconds to minutes for easier interpretability and categorizing genres as either pop or non-pop.

#### Data Exploration
![spotify-2](https://github.com/katlynkenisha/Spotify/assets/109913754/3ccd2243-09d9-47af-9c98-1d947f194d10)

A noteworthy observation during data exploration is the mild imbalance between the number of pop and non-pop tracks, suggesting the need to address data imbalance. Due to the mild level of imbalance (66% to 34%), the primary metric used to evaluate model performance is the F1-Score.

### 3. Data Transformation
Data transformation involves encoding genres such that pop is represented as 1 and non-pop as 0, as well as normalizing variables with varying scales.

### 4. Train Test Split and Data Balancing
The dataset is dividied into 80% training and 20% testing sets. To address the mild imbalance of genres, the training set is balanced using SMOTE.

### 5. Modeling
Each type of classification model is assessed using all variables as well as only variables without multicollinearity. Hence, 4 models are obtained. Model performance on training sets is evaluated through 5-Fold Cross Validation, followed by fitting the model to evaluate performance on unseen testing set.

### 6. Model Performance
| Model | F1-Score (Training) | F1-Score (Testing) |
| :--- | :---: | :---: |
| Logistic Regression with All Variables | 76.1% | 81.1% |
| Logistic Regression with Variables Free from Multicollinearity | 73.7% | 78.5% |
| KNN with All Variables | 76.9% | 76% |
| KNN with Variables Free from Multicollinearity | 74.7% | 76.2% |

In general, logistic regression shows a better performance compared to KNN. The logistic regression model with all variables achieves the highest F1-Score of 81.1%. However, to ensure the reliability of the logistic regression model, it is better to avoid using variables that exhibit multicollinearity as they can lead to instability in parameter estimation. Hence, the best model in this case is the logistic regression model with variables free from multicollinearity, obtaining an F1-Score of 78.5%.

### 7. Feature Importance
Permutation importance is applied to determine feature importance and gain insights on the impact of each audio feature on track genre classification. Key insights from permutation importance analysis include:
- Speechiness consistently shows the highest contribution across all models, indicating its important role in determining whether a track's genre is pop or non-pop.
- Valence also shows a high contribution on all models.
- Instrumentalness, liveness, and mode show a low contribution on all models, possibly signifiying their minor impact in the case of pop music genre classification.

## Conclusion
Results show that Logistic Regression outperforms KNN in the case of pop music classification.
