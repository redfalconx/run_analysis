run_analysis
============

Getting and Cleaning Data Peer Assessment

Note:

* Install 'reshape' and 'reshape2' packages.
* The directory "UCI HAR Dataset" should be in the working directory of your R folder.
* Please ensure that the data files and the script are a part of same R working directory.
* The script processes data for mean and standard deviation columns, and meanFreq columns have also been ignored.
* The script has also been commented with each step explained correctly. Please refer to that in case of any confussion.

Explanation:

First load the reshape packages
The data can be viewed as Train ( X, Y, Subject ) and Test ( X, Y and Subject ). These will form the tidy data later on

We first read the files Train(X.y,Sub) and Test (X,y,sub)

We then have to combine all the 3 datasets. In the final form Train data and Test data will be combined. Within each of train and test data, we will combine the columns of X, Y and Subject in each. So essentially it is like a rbind(Train, Test), and each Test and Train is like Train = cbind(Xtrain, YTrain, SubTrain).

We are row binding each of X , Y, and Subject variables first and will do a cbind later.

NOTE: The order of rows are preserverd since we are doing a rbind of Train and Test data for each of them.

The next step is to label the activity_data correctly. The merge function has been used to merge the activity_labels.txt file with the Y data set and a new column has been added to Y data set by the name "activity_name"

For the X data, we label the column names correctly from data from "features.txt". 'colnames()' function is used for this

Use grep function on column names in X data to retreive columns that have 'mean()' and 'std()' characters

Merge the X, Y, and Subject data together to form the main data set - 'datafinal'

Make the names of the column in 'datafinal' more informative. The names have been simplied based on readability and might be scientifically incorrect.

Use melt and cast functions to create tidy data, which is the average of each column for unique combination of Subject + activity name.

Write the tidy data to a 'tidydata.txt' file in your working directory.
