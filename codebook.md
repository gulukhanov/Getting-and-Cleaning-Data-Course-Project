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

## Output Variables

##  [1] "timeBodyAccelerometer-mean()-X"                
##  [2] "timeBodyAccelerometer-mean()-Y"                
##  [3] "timeBodyAccelerometer-mean()-Z"                
##  [4] "timeBodyAccelerometer-std()-X"                 
##  [5] "timeBodyAccelerometer-std()-Y"                 
##  [6] "timeBodyAccelerometer-std()-Z"                 
##  [7] "timeGravityAccelerometer-mean()-X"             
##  [8] "timeGravityAccelerometer-mean()-Y"             
##  [9] "timeGravityAccelerometer-mean()-Z"             
## [10] "timeGravityAccelerometer-std()-X"              
## [11] "timeGravityAccelerometer-std()-Y"              
## [12] "timeGravityAccelerometer-std()-Z"              
## [13] "timeBodyAccelerometerJerk-mean()-X"            
## [14] "timeBodyAccelerometerJerk-mean()-Y"            
## [15] "timeBodyAccelerometerJerk-mean()-Z"            
## [16] "timeBodyAccelerometerJerk-std()-X"             
## [17] "timeBodyAccelerometerJerk-std()-Y"             
## [18] "timeBodyAccelerometerJerk-std()-Z"             
## [19] "timeBodyGyroscope-mean()-X"                    
## [20] "timeBodyGyroscope-mean()-Y"                    
## [21] "timeBodyGyroscope-mean()-Z"                    
## [22] "timeBodyGyroscope-std()-X"                     
## [23] "timeBodyGyroscope-std()-Y"                     
## [24] "timeBodyGyroscope-std()-Z"                     
## [25] "timeBodyGyroscopeJerk-mean()-X"                
## [26] "timeBodyGyroscopeJerk-mean()-Y"                
## [27] "timeBodyGyroscopeJerk-mean()-Z"                
## [28] "timeBodyGyroscopeJerk-std()-X"                 
## [29] "timeBodyGyroscopeJerk-std()-Y"                 
## [30] "timeBodyGyroscopeJerk-std()-Z"                 
## [31] "timeBodyAccelerometerMagnitude-mean()"         
## [32] "timeBodyAccelerometerMagnitude-std()"          
## [33] "timeGravityAccelerometerMagnitude-mean()"      
## [34] "timeGravityAccelerometerMagnitude-std()"       
## [35] "timeBodyAccelerometerJerkMagnitude-mean()"     
## [36] "timeBodyAccelerometerJerkMagnitude-std()"      
## [37] "timeBodyGyroscopeMagnitude-mean()"             
## [38] "timeBodyGyroscopeMagnitude-std()"              
## [39] "timeBodyGyroscopeJerkMagnitude-mean()"         
## [40] "timeBodyGyroscopeJerkMagnitude-std()"          
## [41] "frequencyBodyAccelerometer-mean()-X"           
## [42] "frequencyBodyAccelerometer-mean()-Y"           
## [43] "frequencyBodyAccelerometer-mean()-Z"           
## [44] "frequencyBodyAccelerometer-std()-X"            
## [45] "frequencyBodyAccelerometer-std()-Y"            
## [46] "frequencyBodyAccelerometer-std()-Z"            
## [47] "frequencyBodyAccelerometerJerk-mean()-X"       
## [48] "frequencyBodyAccelerometerJerk-mean()-Y"       
## [49] "frequencyBodyAccelerometerJerk-mean()-Z"       
## [50] "frequencyBodyAccelerometerJerk-std()-X"        
## [51] "frequencyBodyAccelerometerJerk-std()-Y"        
## [52] "frequencyBodyAccelerometerJerk-std()-Z"        
## [53] "frequencyBodyGyroscope-mean()-X"               
## [54] "frequencyBodyGyroscope-mean()-Y"               
## [55] "frequencyBodyGyroscope-mean()-Z"               
## [56] "frequencyBodyGyroscope-std()-X"                
## [57] "frequencyBodyGyroscope-std()-Y"                
## [58] "frequencyBodyGyroscope-std()-Z"                
## [59] "frequencyBodyAccelerometerMagnitude-mean()"    
## [60] "frequencyBodyAccelerometerMagnitude-std()"     
## [61] "frequencyBodyAccelerometerJerkMagnitude-mean()"
## [62] "frequencyBodyAccelerometerJerkMagnitude-std()" 
## [63] "frequencyBodyGyroscopeMagnitude-mean()"        
## [64] "frequencyBodyGyroscopeMagnitude-std()"         
## [65] "frequencyBodyGyroscopeJerkMagnitude-mean()"    
## [66] "frequencyBodyGyroscopeJerkMagnitude-std()"     
## [67] "subject"                                       
## [68] "activity"
