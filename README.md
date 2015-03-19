This file describes the files involved in this assignment submission.

1) Objective

The purpose of this assignment is to extract a tidy data set which contains the average of each mean and standard deviation measurements(variables), for each activity and each subject from the "Human Activity Recognition Using Smartphones Data Set".

More details about the raw data and transformation can be found in CodeBook.md.

2) Files submitted

4 files were submitted for this assignment. 

The tidy data set, in "tidyData.txt", was uploaded as attachment in the course assignment page. In this data set, each variable has a column and each observation is a row.

The remaining 3 files, README.md, CodeBook.md and run_analysis.R were uploaded to the following Github repository:

https://github.com/FlyWong/getdata-012AssignmentSubmission

CodeBook.md describes the raw data, the variables and outlined the transformations performed to clean up the raw data into the required form.

run_analysis.R is the R script used to perform the transformation. The script assumes all required data files are in the working directory and output the tidy data file, 'tidyData.txt' into the working directory. The script requires dplyr and reshape2 libraries.