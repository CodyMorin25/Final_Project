# Video_Games-ReviewsVSCopies_Sold

#### Google Slides
https://docs.google.com/presentation/d/1PYr4flXaCb-HIgzVWcJvHG2INmE7pAxXoLhhh8ACIvA/edit?usp=sharing

### Selected Topic
See if there is a relationship between how a paid critic rates a game and how a user who bought the game rates the game

### Reason
Selected this topic because as a video gamer there are many factors that determines if a video game will be good or bad. It can be because of who made the game, how long the development was, all of the teasers released to increases hype, the genre of the game, what platforms it is available on , etc. Pridicting whether a game is  any good to begin with is very diffucult and as a gamer I tend to look at reviews first to get an idea about how good a game is. I tend to mainly look for reviews from users who have bought the game. With this analysis I hope to see if there is a relationship between a critics review vs a users review.

### Data Source
The data is from a .csv file abtained from kaggle at [https://www.kaggle.com/datasets/deepcontractor/top-video-games-19952021-metacritic](https://www.kaggle.com/datasets/destring/metacritic-reviewed-games-since-2000) with games, their releases, platform, user review ratings and metacritic review ratings. 

### Question to answer
Is there a relationship between video game user/critic ratings?

## Explore Data
Looked at dataset by seeing if there are potential issues with the dataset. I seen that metascore had values from 0-100 and userscore had 0-10. Will alter the userscore values to better match metascore. After trying to see the count, mean, min, max, etc. for the dataset I saw that it only showed the metascore and not the userscore. I came to find that in the dataset where values 'tbd'. When I go to clean the data I will need to remove those values and change the data type due to its type being 'object' when I need it to be an interger type. Also took a look to see if there were any outliers. I created boxplots of the data and they both showed outliers at the lower values.

## Clean Data
Imported CSV file to Jupyter Notebook in order to clean the data. Dropped the console and date columns because they will not be necessary for the analysis. Needed to change data type for column 'userscore' to multiply the values by 10 inorder to make the values similar in size. Have to first discard the "tbd" values in the column inorder to change the data type to an integer friendly type. Once that is done I can multiply the values by ten to make the values for both 'metascore' and 'userscore' 0-100. After that removed the decimal for 'userscore' and then checked the dataset for outliers. The outliers tended to be lower than 40 for both user and meta scores. After taking a look at the mean, min, max, etc. of the data there wasa no real significant issues with the outliers being in the dataset. There are duplicates in the data but the duplicates are because there are reviews for games based on the platform and there are multiple platforms available. Some of the duplicates have different values and the reviews on different platforms can have different implications. If you have a PS4 you would want to know the reviews for the game for that platform because the capabilities of the console may differ from others and may perform better or worse. Lastly I converted the new dataframe to a CSV file to be used for the analysis.

## Machine Learning Model
### Linear Regression
After uploading the clean dataset to Jupyter Notebook I plotted it to a matplotlib scatter plot to get an idea of what I am looking at. My features from the dataset are 'metascore' and 'userscore'. I made the 'metascore' values my x_data and the 'userscore' values as my y_data. After creating the plot I looked at my data using seaborn to give me more visuales to analyze the data. I used sns.jointplot, sns.jointplot with the kind as 'hex' and sns.pairplot.
Next I did my model by setting my X and y values to pluge into a model I set equal to LinearRegression. Then I fit and predicted the data inorder to plot my data to a scatterplot using matplotlib.
I also used another method for LinearRegression to see if the outcome repeated. I used x_min, x_max, y_min, and y_max for the method.

## Results
After using linear regression the model shows that there is no real difference between critic reviews and user reviews. That using the ciritics review you could predict what the user would review. The correlation coefficient = 0.59943999 for the initial linear regression model  and shows that there is a moderate positive relationship between the two reviews. The correlation coefficient = 0.59309261 for the predicted linear regression model and also show a moderate positive relationship. Lastly the R-Squared value equaled 0.30901127392540895 which isn't all that great for the analysis and tells me that possible changed need done to increase score.


# Future Analysis
After the results it would seem that maybe to help the model would to have more features by finding a dataset with more columns or one with a column with video game names inorder to merge them.
