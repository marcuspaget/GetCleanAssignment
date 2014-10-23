### Introduction

This repository is by Mark Paget, for the John Hopkins School Coursera get-data-008 course project.

Original data source: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

Zip Last-Modified: Wed, 15 Jan 2014 14:20:28 GMT

Zip sha1sum: 566456a9e02a23c2c0144674d9fa42a8b5390e71

Please referencing the README.txt included in the zip and CodeBook.md in this repository.


==================================================================
Extracted from the README.txt included in the zip:

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. See 'features_info.txt' for more details.

==================================================================

If you have questions about the data, please contact marcuspaget via github

### Preparation

I found under Linux it was required to strip the initial blank space and any double blank spaces. So test and train data could be loaded correctly.

Here is the Unix shell code I used:

$ sed 's/  / /g' X_train.txt > X_train.txt2
$ sed 's/^ //' X_train.txt2 > X_train.txt

$ sed 's/  / /g' X_test.txt > X_test.txt2
$ sed 's/^ //' X_test.txt2 > X_test.txt

### Details


The dataset includes the following files:
=========================================

- README.md: this file

- CodeBook.md: Shows information about the variables, data sourcing and manipulation.

- run_analysis.R: The R code to analysis the data - merging sources and cleaning the data. Objectives:

	* Merges the training and the test sets to create one data set.
	* Extracts only the measurements on the mean and standard deviation for each measurement. 
	* Uses descriptive activity names to name the activities in the data set
	* Appropriately labels the data set with descriptive variable names. 
	* From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.


- comb_results.txt: Tidy dataset as generated by run_analysis.R

## Code Book

Please see CodeBook.md

## Analysis

As listed for run_analysis.R above. Once the zip is downloaded and unzipped with the unzip command a directory called "UCI HAR Dataset" is created.

This contains the README.txt file - which explains the other files. Data lives in the train and test directories. run_analysis.R is run from the UCI HAR Dataset directory and picks up the relevant data files under test/train. Then it combines the subjects (people) involved in the study with their data and activity. It labels the activities which are numeric originally and produces a mean for the columns that contain "std", and "mean".

All other details about the data is available via the README.txt file in the zip.
