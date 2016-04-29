#CodeBook for the data cleaning Course

##source

This dataset is derived from the "Human Activity Recognition Using Smartphones Data Set" which was originally made avaiable here: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

##Feature Selection

I refer you to the README and features.txt files in the original dataset to learn more about the feature selection for this dataset. And there you will find the follow description:

The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz.

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag).

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals).

The reasoning behind my selection of features is that the assignment explicitly states "Extracts only the measurements on the mean and standard deviation for each measurement." To be complete, I included all variables having to do with mean or standard deviation.

In short, for this derived dataset, these signals were used to estimate variables of the feature vector for each pattern:
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

tBodyAcc-XYZ
tGravityAcc-XYZ
tBodyAccJerk-XYZ
tBodyGyro-XYZ
tBodyGyroJerk-XYZ
tBodyAccMag
tGravityAccMag
tBodyAccJerkMag
tBodyGyroMag
tBodyGyroJerkMag
fBodyAcc-XYZ
fBodyAccJerk-XYZ
fBodyGyro-XYZ
fBodyAccMag
fBodyAccJerkMag
fBodyGyroMag
fBodyGyroJerkMag
The set of variables that were estimated (and kept for this assignment) from these signals are:

mean(): Mean value
std(): Standard deviation
Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

gravityMean
tBodyAccMean
tBodyAccJerkMean
tBodyGyroMean
tBodyGyroJerkMean
Other estimates have been removed for the purpose of this excercise.

Note: features are normalized and bounded within [-1,1].

The resulting variable names are of the following form: tbodyaccmeanx, which means the mean value of tBodyAcc-XYZ.
 
##Subject and Activity

These variables identify the unique subject/activity pair the variables relate to:

Subject: the integer subject ID.
Activity: the string activity name:
Walking
Walking Upstairs
Walking Downstairs
Sitting
Standing
Laying

##Measurement Means

All variables are the mean of a measurement for each subject and activity. This is indicated by the initial Mean in the variable name.
The data base contains 30 subject and 6 activities. Therefore, there are 180 combinations grouped by subject and activity in the factorized database.
For each possible pair mean of 79 variables are reported in the followng order.
 
 [1] "subject"                                                               
 [2] "activity"

 
 [3] "body-acceleration-mean-x-time"                                         
 [4] "body-acceleration-mean-y-time"                                         
 [5] "body-acceleration-mean-z-time"                                         
 [6] "body-acceleration-std-x-time"                                          
 [7] "body-acceleration-std-y-time"                                          
 [8] "body-acceleration-std-z-time"                                          
 [9] "gravity-acceleration-mean-x-time"                                      
[10] "gravity-acceleration-mean-y-time"                                      
[11] "gravity-acceleration-mean-z-time"                                      
[12] "gravity-acceleration-std-x-time"                                       
[13] "gravity-acceleration-std-y-time"                                       
[14] "gravity-acceleration-std-z-time"                                       
[15] "body-acceleration-suddenmovement-mean-x-time"                          
[16] "body-acceleration-suddenmovement-mean-y-time"                          
[17] "body-acceleration-suddenmovement-mean-z-time"                          
[18] "body-acceleration-suddenmovement-std-x-time"                           
[19] "body-acceleration-suddenmovement-std-y-time"                           
[20] "body-acceleration-suddenmovement-std-z-time"                           
[21] "body-gyroscopicmeasurement-mean-x-time"                                
[22] "body-gyroscopicmeasurement-mean-y-time"                                
[23] "body-gyroscopicmeasurement-mean-z-time"                                
[24] "body-gyroscopicmeasurement-std-x-time"                                 
[25] "body-gyroscopicmeasurement-std-y-time"                                 
[26] "body-gyroscopicmeasurement-std-z-time"                                 
[27] "body-gyroscopicmeasurement-suddenmovement-mean-x-time"                 
[28] "body-gyroscopicmeasurement-suddenmovement-mean-y-time"                 
[29] "body-gyroscopicmeasurement-suddenmovement-mean-z-time"                 
[30] "body-gyroscopicmeasurement-suddenmovement-std-x-time"                  
[31] "body-gyroscopicmeasurement-suddenmovement-std-y-time"                  
[32] "body-gyroscopicmeasurement-suddenmovement-std-z-time"                  
[33] "body-acceleration-magnitude-mean-time"                                 
[34] "body-acceleration-magnitude-std-time"                                  
[35] "gravity-acceleration-magnitude-mean-time"                              
[36] "gravity-acceleration-magnitude-std-time"                               
[37] "body-acceleration-suddenmovement-magnitude-mean-time"                  
[38] "body-acceleration-suddenmovement-magnitude-std-time"                   
[39] "body-gyroscopicmeasurement-magnitude-mean-time"                        
[40] "body-gyroscopicmeasurement-magnitude-std-time"                         
[41] "body-gyroscopicmeasurement-suddenmovement-magnitude-mean-time"         
[42] "body-gyroscopicmeasurement-suddenmovement-magnitude-std-time"          
[43] "body-acceleration-mean-x-frequency"                                    
[44] "body-acceleration-mean-y-frequency"                                    
[45] "body-acceleration-mean-z-frequency"                                    
[46] "body-acceleration-std-x-frequency"                                     
[47] "body-acceleration-std-y-frequency"                                     
[48] "body-acceleration-std-z-frequency"                                     
[49] "body-acceleration-meanfreq-x-frequency"                                
[50] "body-acceleration-meanfreq-y-frequency"                                
[51] "body-acceleration-meanfreq-z-frequency"                                
[52] "body-acceleration-suddenmovement-mean-x-frequency"                     
[53] "body-acceleration-suddenmovement-mean-y-frequency"                     
[54] "body-acceleration-suddenmovement-mean-z-frequency"                     
[55] "body-acceleration-suddenmovement-std-x-frequency"                      
[56] "body-acceleration-suddenmovement-std-y-frequency"                      
[57] "body-acceleration-suddenmovement-std-z-frequency"                      
[58] "body-acceleration-suddenmovement-meanfreq-x-frequency"                 
[59] "body-acceleration-suddenmovement-meanfreq-y-frequency"                 
[60] "body-acceleration-suddenmovement-meanfreq-z-frequency"                 
[61] "body-gyroscopicmeasurement-mean-x-frequency"                           
[62] "body-gyroscopicmeasurement-mean-y-frequency"                           
[63] "body-gyroscopicmeasurement-mean-z-frequency"                           
[64] "body-gyroscopicmeasurement-std-x-frequency"                            
[65] "body-gyroscopicmeasurement-std-y-frequency"                            
[66] "body-gyroscopicmeasurement-std-z-frequency"                            
[67] "body-gyroscopicmeasurement-meanfreq-x-frequency"                       
[68] "body-gyroscopicmeasurement-meanfreq-y-frequency"                       
[69] "body-gyroscopicmeasurement-meanfreq-z-frequency"                       
[70] "body-acceleration-magnitude-mean-frequency"                            
[71] "body-acceleration-magnitude-std-frequency"                             
[72] "body-acceleration-magnitude-meanfreq-frequency"                        
[73] "body-acceleration-suddenmovement-magnitude-mean-frequency"             
[74] "body-acceleration-suddenmovement-magnitude-std-frequency"              
[75] "body-acceleration-suddenmovement-magnitude-meanfreq-frequency"         
[76] "body-gyroscopicmeasurement-magnitude-mean-frequency"                   
[77] "body-gyroscopicmeasurement-magnitude-std-frequency"                    
[78] "body-gyroscopicmeasurement-magnitude-meanfreq-frequency"               
[79] "body-gyroscopicmeasurement-suddenmovement-magnitude-mean-frequency"    
[80] "body-gyroscopicmeasurement-suddenmovement-magnitude-std-frequency"     
[81] "body-gyroscopicmeasurement-suddenmovement-magnitude-meanfreq-frequency"