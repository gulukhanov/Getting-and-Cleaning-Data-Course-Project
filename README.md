Getting-and-Cleaning-Data-Course-Project
========================================
#Steps to fulfill (for code look at script file)
* set working directory
* download file 
* unzip file
* set path to unzipped files

#1.Creates one data set
* read Activity data (test and train parts) and merge by rows 
* same to Subjects and Features
* set names to variables
* create one data set (merge by columns)

#2.Extracts only the measurements on the mean and standard deviation for each measurement
* extract columns with "mean()" and "std()" strings in names
* create subset data frame

#3.Uses descriptive activity names to name the activities in the data set
* read descriptive activity names from file
* change factor levels 1-6 to descriptive activity names

#4.Appropriately labels the data set with descriptive variable names
* using gsub()

#5.From the data set in step 4, creates a second, independent tidy data set with the average 
of each variable for each activity and each subject
* using library(plyr) package

#write resulting data frame to a text file

