Getting-and-Cleaning-Data-Course-Project
========================================
Overview

The purpose of this project is to demonstrate your ability to collect, work with, and clean a data set. The goal is to prepare tidy data that can be used for later analysis. You will be graded by your peers on a series of yes/no questions related to the project. You will be required to submit: 1) a tidy data set as described below, 2) a link to a Github repository with your script for performing the analysis, and 3) a code book that describes the variables, the data, and any transformations or work that you performed to clean up the data called CodeBook.md. You should also include a README.md in the repo with your scripts. This repo explains how all of the scripts work and how they are connected.

One of the most exciting areas in all of data science right now is wearable computing - see for example this article . Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most advanced algorithms to attract new users. The data linked to from the course website represent data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones
Here are the data for the project:

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
You should create one R script called run_analysis.R that does the following.

Merges the training and the test sets to create one data set.
Extracts only the measurements on the mean and standard deviation for each measurement.
Uses descriptive activity names to name the activities in the data set
Appropriately labels the data set with descriptive variable names.
Creates a second, independent tidy data set with the average of each variable for each activity and each subject.

##Steps to fulfill (for code look script file)
* set working directory
* download file 
* unzip file
* set path to unzipped files

###1.Creates one data set
* read Activity data (test and train parts) and merge by rows 
* same to Subjects and Features
* set names to variables
* create one data set (merge by columns)

###2.Extracts only the measurements on the mean and standard deviation for each measurement
* extract columns with "mean()" and "std()" strings in names
* create subset data frame

###3.Uses descriptive activity names to name the activities in the data set
* read descriptive activity names from file
* change factor levels 1-6 to descriptive activity names

###4.Appropriately labels the data set with descriptive variable names
* using gsub()

###5.From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
* using library(plyr) package

* write resulting data frame to a text file

