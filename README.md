Getting-and-Cleaning-Data-Course-Project
========================================
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
