# Football-Scores-Prediction-KNN

## Datasets:
- Fifa 21 Complete Player Dataset from keggle.com
- European Leagues 2019-20 Match Results from football-data.co.uk
- Champions League 2019-20 Match Results from fixturedownload.com


The project aims at predicting the 2020-2021 rankings of the 5 major European leagues (Serie A, Premier League, LaLiga, Ligue 1, BundesLiga) and the 2020-21 Champions League competition rounds, starting from the results returned by our model (using the previously mentioned datasets) and using the classification algorithm 'K-Nearest Neighbors'.

## Analysis:

Using the values of the players taken from the FIFA21 dataset and grouping them by team, we obtain an evaluation (divided by fields, for example: age, attack, defense, passing, dribbling, physicality and many others) of each team. Players whose role is 'Goalkeeper' are considered separately because their statistics are different from those of other roles.

The use of this dataset allows to have an updated, consistent and real evaluation of the actual performance and "strength" of the teams, based on the average statistics of the players that compose it.

K-Nearest-Neighbors (KNN), one of the most versatile lazy algorithms, is used.

The KNN algorithm is a classification algorithm, but it is also widely used for predictive analysis. KNN is based on the idea that starting from classified data points, it is possible to classify a new one by looking at the K data points closest to it. This means that the algorithm uses an instance-based learning, where the training data set is used to classify the unknown data point. As can be seen from the figure below, the colored squares (red and blue) are classified, while the white square is the one to be classified. In this case, the K chosen is three and by majority vote the white square will be classified as red.

To determine which points are the closest to the one to be classified, the Euclidean distance between all classified and unclassified data points is measured.

Large K-values are generally more accurate than small K-values because they eliminate noise-generating factors, but they are computationally more expensive.

Before making actual predictions, it is always a good idea to resize features so that all can be evaluated uniformly, so the MinMaxScaler function from the Scikit-Learn library is imported.
 
MinMaxScaler normalizes variables in a standard range [0,1], the range in which floating-point values have the highest precision.

The scaler is then fit with the .fit() function that reads the training data and makes an estimate of the maximum and minimum values that may be encountered.


The program has at its disposal 3400 results of matches of 2019/20 between leagues and international cups on which to train the model, after several tests, the best choice is to use 85% of the data as training and the remaining 15% of the data as tests.
As shown in the graph the ideal number of K to increase the accuracy of the model is K=47, an odd number is chosen so as not to have situations of parity of votes. The program arrives so to guarantee a 55% of accuracy of the result, percentage in line with that of other studies.

The F1 score takes into account test precision and recovery, where precision is the number of true positives divided by the number of all positive results, and recovery is the number of true positives divided by the number of all tests that should have tested positive (i.e. true positives plus false negatives). The F1 is calculated by the harmonic mean of precision and recovery.

For each league, after adding the newly promoted teams and eliminating the relegated ones, all the matches (round-trip) between the participants are created. 3,1,0 points are assigned for victory, draw or defeat respectively. The value "0" indicates a tie, while "1" and "2" win the home or away team.
 
The Champions League groups and participating teams are imported from an external .csv file. The program calculates the rankings of all 8 groups, then the two highest scoring clubs in each group are selected, i.e. the 16 teams that are guaranteed passage to the knockout stage.

## Language used:

Python Notebook (.ipynb)

## Libraries used:

- Numpy, Pandas for dataframes management
- Matplotlib for graph creation
- Sklearn for predictive model creation and training

## Achievements:
Below are two of the results obtained from the prediction, one related to the Italian league and one related to the Champions League.

The model predicts Inter as the winner after 9 consecutive championships obtained by Juventus. Inter will then actually be champion of Italy for the 2020-2021 season, thus confirming the goodness of the prediction.

The model succeeds in predicting 13 of the 16 teams past the Champions League group stages (2020-21) with a percentage of 81.2 percent

Knowing the finalists of May 29 and using the result() function, which takes as input the names of two teams and returns the hypothetical result, Manchester City is favored over Chelsea. Prediction in line with that of the bookmakers.
