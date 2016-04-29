## R code to get, combine, and clean the data.

# If required packages are not present then install them.
if("dplyr" %in% rownames(installed.packages()) == FALSE) {install.packages("dplyr")};library(dplyr)
if("tidyr" %in% rownames(installed.packages()) == FALSE) {install.packages("tidyr")};library(tidyr)

# If the dataset is not present in the current working directory then download it
setwd("D:/Coursera/DataCleaning")
Url <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
if (!file.exists("UCI HAR Dataset")) {
  download.file(Url, destfile="Dataset.zip")
  unzip("Dataset.zip")
}
# Reading the data and storing it in data frames
x_train <- read.table("UCI HAR Dataset//train/X_train.txt")
x_test <- read.table("UCI HAR Dataset//test/X_test.txt")
subject_train <- read.table("UCI HAR Dataset//train/subject_train.txt", col.names=c("subject"))
subject_test <- read.table("UCI HAR Dataset/test/subject_test.txt", col.names=c("subject"))
y_train <- read.table("UCI HAR Dataset/train//y_train.txt", col.names=c("activity"))
y_test <- read.table("UCI HAR Dataset/test//y_test.txt", col.names=c("activity"))
train_db <- cbind(subject_train, y_train, x_train)
test_db <- cbind(subject_test, y_test, x_test)

# Combine the test and train datasets

MasterData<- rbind(train_db,test_db)

#Read Feature file that contains the column names for the train and test datasets.
features <- read.table("UCI HAR Dataset//features.txt")

# Assign feature names to individual columns in the merged dataset.

for (i in 3:length(MasterData)){colnames(MasterData)[i]<-as.vector(features[i-2,2])}

Index<- grepl("mean|std|subject|activity", colnames(MasterData))
SelectedData <- MasterData[, Index]

# Download activity lables and substitude them as factors instead of the numbers in the data set

activityname <- read.table("UCI HAR Dataset//activity_labels.txt")
SelectedData$activity<- as.character(SelectedData$activity)
for (j in 1:nrow(SelectedData)){
  if (SelectedData[j,2]=="1"){SelectedData[j,2]<- as.character(activityname[1,2])}
  if (SelectedData[j,2]=="2"){SelectedData[j,2]<- as.character(activityname[2,2])}
  if (SelectedData[j,2]=="3"){SelectedData[j,2]<- as.character(activityname[3,2])}
  if (SelectedData[j,2]=="4"){SelectedData[j,2]<- as.character(activityname[4,2])}
  if (SelectedData[j,2]=="5"){SelectedData[j,2]<- as.character(activityname[5,2])}
  if (SelectedData[j,2]=="6"){SelectedData[j,2]<- as.character(activityname[6,2])}
}
SelectedData$activity<- as.factor(SelectedData$activity)

#Cleaning up the column names to include full names for abbreviations, remove (), ...
TidyColumnNames<- colnames(SelectedData)
TidyColumnNames<- tolower(TidyColumnNames)
TidyColumnNames <- gsub("\\(\\)", "", TidyColumnNames)
TidyColumnNames <- gsub("acc", "-acceleration", TidyColumnNames)
TidyColumnNames <- gsub("gyro", "-gyroscopicmeasurement", TidyColumnNames)
TidyColumnNames <- gsub("jerk", "-suddenmovement", TidyColumnNames)
TidyColumnNames <- gsub("mag", "-magnitude", TidyColumnNames)
TidyColumnNames <- gsub("^t(.*)$", "\\1-time", TidyColumnNames)
TidyColumnNames<- gsub("^f(.*)$", "\\1-frequency", TidyColumnNames)
TidyColumnNames<- gsub("bodybody", "body", TidyColumnNames)
colnames(SelectedData)<- TidyColumnNames
write.table(SelectedData, file="TidyDataSet.txt", row.name=FALSE)

#Create a new data set that averages values for each subject and each activity
SelectedData$subject <- as.factor(SelectedData$subject)
NewData<- group_by(SelectedData,subject,activity)
NewDataset<- summarise_each(NewData,funs(mean))
write.table(NewDataset, file="FactorizedDataSet.txt", row.name=FALSE)
