# GettingAndCleaningData

|Title	| README.md
|-------|----------
|Author	| Mahendra Kumar Lal
|Date	  | 06-Sept-2018


This is the README.md file for the Getting and Cleaning Data Final Assignment. 
As part of this assignment, the following files are included:



### README.md

A file in markdown format that displays when someone accesses the GitHub repository for a person's submission for the course project. The file is located at https://github.com/mahenlal/GettingAndCleaningData/blob/master/README.md

### CodeBook.md

A file in markdown format that describes the variables (columns) contained in the tidy data set that must be uploaded to the coursera website as part of the project submission process. A file of tidy data created from the UCI HAR dataset using the run_analysis.R script. The file is located at https://github.com/mahenlal/GettingAndCleaningData/blob/master/code_book.md

### run_analysis.R

An R script that contains all of the R functions used to transform the eight input data files into the required formats . This file is located at https://github.com/mahenlal/GettingAndCleaningData/blob/master/run_analysis.R

### independentTidyData.txt
Another file, the output from step 5 listed in "The Data Cleansing Task" should be uploaded to the Coursera website as part of the assignment submission. I have included this independentTidyData.txt  file as well in the GitHub repository for easy reference, located at
https://github.com/mahenlal/GettingAndCleaningData/blob/master/independentTidyData.txt



|File   |Description
|-------|-----------
independentTidyData.txt |A file of tidy data created from the UCI HAR dataset using the run_analysis.R script. The file is located at https://github.com/mahenlal/GettingAndCleaningData

Included information
Dataset use disclosure
Tidy Data
Steps performed in the run_analysis.R
Creation of the CodeBook.md
Dataset use disclosure
Original data was obtained from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

Use of this dataset is acknowledged by referencing the following publication [1]

[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

Tidy Data
According to the Tidy Data paper by Hadley Wickham (http://vita.had.co.nz/papers/tidy-data.pdf), there are four components of tidy data:

Each measured variable forms a column
Each different observation of variables forms a row
Each type of observational unit forms a table
If there are multiple tables, they should include a column in the table which allows them to be linked.
Additionally, there should be:
a row including the variable names at the top of each file
human readable variable names
data should be saved in one file per table

## Steps performed in the run_analysis.R
Assumption note:
This script assumes that the Samsung data folder "UCI HAR Dataset" is in the working directory of the user running the run_analysis.R script.

#### 1. Read data from the file into Data Tables

Source Data File |  Data Table
-----------------|------------------
features.txt  | features
activity_labels.txt| activity_labels
test/subject_test.txt| subject_test
train/subject_train.txt|subject_train
test/y_test.txt | y_test
train/y_train.txt|y_train
test/X_test.txt|x_test
train/X_train.txt|x_train

#### 2. Appropriately labels the data set with descriptive variable names.

colnames(x_test)<-features[,2]
colnames(x_train)<-features[,2]
colnames(y_train)<-"Act_ID"
colnames(y_test)<-"Act_ID"
colnames(subject_test)<-"Subject_ID"
colnames(subject_train)<-"Subject_ID"
colnames(activity_labels)<-c('Act_ID', 'Act_Name')

#### 3. Merge the test  data table (y_test, subject_test, x_test) columns into single Table TEST
TEST <- cbind(y_test, subject_test, x_test)

#### 4. Merge the y_train, subject_train, x_train columns  into  table TRAIN
TRAIN<- cbind(y_train, subject_train, x_train)
#### 5. Combine TEST and TRAIN rows
all_data<-rbind(TRAIN, TEST)


#### 6. Extracts only the measurements on the mean and standard deviation for each measurement.
colNames<-colnames(all_data)

#### 7.Uses descriptive activity names to name the activities in the data set
meanAndStdDev<-(grepl("Act_ID" , colNames) | grepl("Subject_ID" , colNames) | grepl("mean.." , colNames) | grepl("std.." , colNames))
forMaenAndStdDev<-all_data[,meanAndStdDev==TRUE]
withActivity_name<-merge(forMaenAndStdDev, activity_labels, by = 'Act_ID', all.x=TRUE)

#### 8. creates a second, independent tidy data set with the average of each variable for each activity and each subject
indTidyData<-aggregate(.~Subject_ID + Act_ID, withActivity_name, mean)
indTidyData<-indTidyData[order(indTidyData$Subject_ID, indTidyData$Act_ID),]

#### 9. Save data
write.table(indTidyData, "independentTidyData.txt", row.name=FALSE)

File created aboe is uploaded at coursera and also located at https://github.com/mahenlal/GettingAndCleaningData/blob/master/independentTidyData.txt
