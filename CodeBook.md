#GETTING AND CLEANING DATA WEEK 4 PROJECT

Author: Falana Tolu

##Description 
This code book summarizes the data and variables in 'FinalData.txt' which was the output of the Week 4 project in the Coursera Johns Hopkins University course Getting & Cleaning Data and also provides additional information about the variables, data and transformations used in the course project.

##The Data Source
Source data: 

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

Description of the dataset from the source website:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones


##Information on Data Set 
The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING)
wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 
The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

##The data
The dataset includes the following files:
'README.txt'
'features_info.txt': Shows information about the variables used on the feature vector.
'features.txt': List of all features.
'activity_labels.txt': Links the class labels with their activity name.
'train/X_train.txt': Training set.
'train/y_train.txt': Training labels.
'test/X_test.txt': Test set.
'test/y_test.txt': Test labels.

##Project Rquirements  
Source Code 'run_analysis.R' Meets the Requirements for the project in the following ways:
1. Merges the training and the test sets to create one data set. Source code 'run_analysis.R' loads both test and train data, processes them, and merges the results into one dataset.
2. Extracts only the measurements on the mean and standard deviation for each measurement. Source code 'run_analysis.R' extracts the mean and standard deviation data into one dataset with appropriate column names.
3. Uses descriptive activity names to name the activities in the data set. Source code 'run_analysis.R' loads the descriptive feature and activity labels.
4. Appropriately labels the data set with descriptive variable names Source code 'run_analysis.R' adds appropriately descriptive variable names to the large dataset columns (variables).
5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject Source code 'run_analysis.R' calculates the average for all measurement columns grouped by variables
Activity and Subject and then writes the output to a local text file named 'FinalData.txt'

##Variables Used for computed data frames

features <- from features.txt : The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.(561 rows, 2 columns)

activities <- from activity_labels.txt : A list of activities performed when the corresponding measurements were taken and its codes (labels).(6 rows, 2 columns)

subject_test <- from test/subject_test.txt : It contains test data of 9/30 volunteer test subjects being observed.(2947 rows, 1 column)

x_test <- from test/X_test.txt : It contains recorded features test data.(2947 rows, 561 columns)

y_test <- from test/y_test.txt : It contains test data of activities'code labels.(2947 rows, 1 column)

subject_train <- from test/subject_train.txt : It contains train data of 21/30 volunteer subjects being observed.(7352 rows, 1 column)

x_train <- from test/X_train.txt : It contains recorded features train data.(7352 rows, 561 columns)

y_train <- from test/y_train.txt : It contains train data of activities'code labels.(7352 rows, 1 column)

X<-  This was created by merging x_train and x_test using rbind() function.(10299 rows, 561 columns)

Y<-  This wass created by merging y_train and y_test using rbind() function.(10299 rows, 1 column)

Subject<- This was created by merging subject_train and subject_test using rbind() function.(10299 rows, 1 column)

Merged_Data<-  This was created by merging Subject, Y and X using cbind() function.(10299 rows, 563 column)

TidyData<-  This was created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation for each measurement.(10299 rows, 88 columns)

FinalData<-  This was created by summarizing TidyData by taking the means of each variable for each activity and each subject, and afterwards using 'group by' function using both subject and activity.(180 rows, 88 columns)
