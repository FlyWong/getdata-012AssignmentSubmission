Code Book

This Code Book describes the data, its variables and transformations (using run_analysis.R) performed to clean up the data

1. Data

1.1 Data Source

The raw data was obtained from the "Human Activity Recognition Using Smartphones Data Set". Details of the experiment which produced the data can be found at:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

The raw data was downloaded from:

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

1.2 Data Files

Unzip the downloaded zip file and under the .\getdata-projectfiles-UCI HAR Dataset\UCI HAR Dataset folder, data was divided into train and test data sets in the train and test folders respectively.

a) README.txt, features_info.txt, features.txt, activity_labels.txt

These are the common files applicable to both the train and test data sets.

README.txt contains general information about the experiment and the files in the data sets

features_info.txt contains descriptive information on how the variables (features) were obtained from the from the accelerometer and gyroscope 3-axial raw signals

features.txt contains the list of descriptive names for the 561 variables this data set.

activity_labels.txt provides code and descriptive labels to the activities experiment subjects performed.

b) \train\X_train.txt, \test\X_test.txt

Contains 561 columns of variable values from the experiment. There are 7352 and 2947 observations in train and test set respectively.

c) \train\y_train.txt, \test\y_test.txt

Contains single column recording the activity code experiment subject was performing when the observation was made.

d) \train\subject_train.txt, \test\subject_test.txt

Contains single column recording code of the subject performing activity when observation was made.
 
1.3 Exclusion

Data files in the Inertial Signals folders are not required for this purpose and thus ignored.

2 Variables

See features_info.txt for details 

3. Data Transformation

3.1 Objective

The objective of this assignment is to
a)merge the train and test data sets
b)subset only mean and standard deviation variables (columns)
c)use descriptive activity label in the data set
d)use descriptive variable (column) names in the data set

1.2 Preparation

For the ease of reference, all required files are placed in a common folder with the run_analysis.R script.

1.3 Transformation Steps

The following steps are performed in run_analysis.R. The script also requires dplyr and reshape2 R libraries.

a)Read "activity_labels.txt" into a data frame and rename column 1 and 2 to "Activity_ID" and "Activity_Desc" respectively.

b)Read "features.txt" into a data frame.

c)Read "subject_test.txt" into a data frame and rename column 1 to "Subject_ID"

d)Read "y_test.txt" into a data frame and rename column 1 to "Activity_ID"

e)Inner join "activity_labels" and "y_test" data frames using Activity_ID

f)cbind "subject_test" data frame into data frame resulting from step e.

g)Read "X_test.txt" into data frame.

h)Rename "X_test" data frame column names using descriptive labels from "features" data frame.

i)cbind X_test data frame with data frame from step f to create a complete descriptive test data frame

j)Repeat steps from c) to i) for the train data set to create a complete descriptive train data frame.

k)rbind complete descriptive test and train data frames to create full data frame.

l)Create data frame of required variables by subsetting the full data frame to only select "Subject_ID", "Activity_Desc" and variables with either "mean()" or "std()" in their names.

m)Melt the data frame of required variables by using "Subject_ID" and "Activity_Desc" as id.

n)dcast the melt data frame from step m) using "Subject_ID" and "Activity_Desc" as id and "variable" as measured variables. Set "mean"" as aggregate function.

o)Use write.table with row.name=FALSE to write tiny data frame from step n into text file.




