Getting-and-Cleaning-Data-Course-Project
========================================
#set working directory
setwd("D:/DS/C3W3")

#download file 
if(!file.exists("./data")){dir.create("./data")}
fileUrl <- "http://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
download.file(fileUrl,destfile="./data/Dataset.zip")

#unzip file
unzip(zipfile="./data/Dataset.zip",exdir="./data")

#set path to unzipped files
pf <- file.path("./data" , "UCI HAR Dataset")

#1.Creates one data set
#read Activity data (test and train parts) and merge by rows 
dataActivityTest  <- read.table(file.path(pf, "test" , "Y_test.txt" ),header = FALSE)
dataActivityTrain <- read.table(file.path(pf, "train", "Y_train.txt"),header = FALSE)
dataActivity<- rbind(dataActivityTrain, dataActivityTest)

#same to Subjects 
dataSubjectTrain <- read.table(file.path(pf, "train", "subject_train.txt"),header = FALSE)
dataSubjectTest  <- read.table(file.path(pf, "test" , "subject_test.txt"),header = FALSE)
dataSubject <- rbind(dataSubjectTrain, dataSubjectTest)

#same to Features
dataFeaturesTest  <- read.table(file.path(pf, "test" , "X_test.txt" ),header = FALSE)
dataFeaturesTrain <- read.table(file.path(pf, "train", "X_train.txt"),header = FALSE)
dataFeatures<- rbind(dataFeaturesTrain, dataFeaturesTest)

#set names to variables
names(dataSubject)<-c("subject")
names(dataActivity)<- c("activity")
dataFeaturesNames <- read.table(file.path(pf, "features.txt"),head=FALSE)
names(dataFeatures)<- dataFeaturesNames$V2

#create one data set (merge by columns)
Data <- cbind(dataFeatures, dataSubject, dataActivity)

#2.Extracts only the measurements on the mean and standard deviation for each measurement
#extract columns with "mean()" and "std()" strings in names
subdataFeaturesNames<-dataFeaturesNames$V2[grep("mean\\(\\)|std\\(\\)", dataFeaturesNames$V2)]
selectedNames<-c(as.character(subdataFeaturesNames), "subject", "activity" )
#create subset data frame
Data<-subset(Data,select=selectedNames)

#3.Uses descriptive activity names to name the activities in the data set
#read descriptive activity names from file
activityLabels <- read.table(file.path(pf, "activity_labels.txt"),header = FALSE)

#change factor levels 1-6 to descriptive activity names
Data$activity<-factor(Data$activity,levels=activityLabels$V1,labels=activityLabels$V2)
#head(Data$activity,30)

#4.Appropriately labels the data set with descriptive variable names
names(Data)<-gsub("^t", "time", names(Data))            #replace prefix t by time
names(Data)<-gsub("^f", "frequency", names(Data))       #replace prefix f by frequency
names(Data)<-gsub("Acc", "Accelerometer", names(Data))  #replace Acc by Accelerometer
names(Data)<-gsub("Gyro", "Gyroscope", names(Data))     #replace Gyro by Gyroscope
names(Data)<-gsub("Mag", "Magnitude", names(Data))      #replace Mag by Magnitude
names(Data)<-gsub("BodyBody", "Body", names(Data))      #replace BodyBody to Body
#head(Data,20)

#5.From the data set in step 4, creates a second, independent tidy data set with the average 
#of each variable for each activity and each subject
library(plyr);
Data2<-aggregate(. ~subject + activity, Data, mean)
Data2<-Data2[order(Data2$subject,Data2$activity),]
#head(Data2)

#write resulting data frame to a text file
write.table(Data2, file = "tidydata.txt",row.name=FALSE)
