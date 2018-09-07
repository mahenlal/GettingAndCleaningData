## Title	: CodeBook.md
## Author	: Mahendra Kumar Lal
## Date   : 06-Sep-2018
## About	:
This Code Book describes the variables in the source data set to produce the variables contained in the tidydata.txt file produced by running the run_analysis.R, and the variables contained in the tidydata.txt file. For full details on the steps to generate the variables described in this file from the original variables, see the README.md.
## Included information
Raw Source Data README Information
Source Data features_info Information
Tidy Data Set Transformations
Data Dictionary - Tidy Data from UCI HAR Dataset Description of each variable in tidydata.txt

## Raw Source Data

Human Activity Recognition Using Smartphones Dataset Version 1.0
Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto. Smartlab - Non Linear Complex Systems Laboratory DITEN - Università degli Studi di Genova. Via Opera Pia 11A, I-16145, Genoa, Italy. activityrecognition@smartlab.ws www.smartlab.ws

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.
The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. See 'features_info.txt' for more details.
### For each record it is provided:
Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.

Triaxial Angular velocity from the gyroscope.

A 561-feature vector with time and frequency domain variables.

Its activity label.

An identifier of the subject who carried out the experiment.

### The dataset includes the following files:
'README.txt'

'features_info.txt': Shows information about the variables used on the feature vector.

'features.txt': List of all features.

'activity_labels.txt': Links the class labels with their activity name.

'train/X_train.txt': Training set.

'train/y_train.txt': Training labels.

'test/X_test.txt': Test set.

'test/y_test.txt': Test labels.


### The following files are available for the train and test data. Their descriptions are equivalent.

'train/subject_train.txt': 
Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30.

'train/Inertial Signals/total_acc_x_train.txt': 
The acceleration signal from the smartphone accelerometer X axis in standard gravity units 'g'. Every row shows a 128 element vector. The same description applies for the 'total_acc_x_train.txt' and 'total_acc_z_train.txt' files for the Y and Z axis.

'train/Inertial Signals/body_acc_x_train.txt': 
The body acceleration signal obtained by subtracting the gravity from the total acceleration.

'train/Inertial Signals/body_gyro_x_train.txt':
The angular velocity vector measured by the gyroscope for each window sample. The units are radians/second.



### Notes:

Features are normalized and bounded within [-1,1].

Each feature vector is a row on the text file.

Features information from Source Data features_info.txt


### Feature Selection
 
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz.
Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag).

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals).
These signals were used to estimate variables of the feature vector for each pattern:
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.
tBodyAcc-XYZ tGravityAcc-XYZ tBodyAccJerk-XYZ tBodyGyro-XYZ tBodyGyroJerk-XYZ tBodyAccMag tGravityAccMag tBodyAccJerkMag tBodyGyroMag tBodyGyroJerkMag fBodyAcc-XYZ fBodyAccJerk-XYZ fBodyGyro-XYZ fBodyAccMag fBodyAccJerkMag fBodyGyroMag fBodyGyroJerkMag

### The set of variables that were estimated from these signals are:

mean(): Mean value

std(): Standard deviation

mad(): Median absolute deviation

max(): Largest value in array

min(): Smallest value in array

sma(): Signal magnitude area

energy(): Energy measure. Sum of the squares divided by the number of values.

iqr(): Interquartile range

entropy(): Signal entropy

arCoeff(): Autorregresion coefficients with Burg order equal to 4

correlation(): correlation coefficient between two signals

maxInds(): index of the frequency component with largest magnitude

meanFreq(): Weighted average of the frequency components to obtain a mean frequency

skewness(): skewness of the frequency domain signal

kurtosis(): kurtosis of the frequency domain signal

bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.

angle(): Angle between to vectors.

Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

gravityMean

tBodyAccMean

tBodyAccJerkMean

tBodyGyroMean

tBodyGyroJerkMean

### Tidy Data Set Transformations

To produce the tidy dataset, the test and train data sets were merged, the subject and activity labels were included. Then, only the Mean and Standard deviation variables on each measurement were selected, and descriptive activity names as defined in activity_labels.txt were used to label the activities. Finally, an independent tidy data set containing the average (mean) of each of the Mean and Standard deviation variables for each activity and each subject was created. 
The description of each variable contained in the tidydata.txt dataset is contained in the "Data Dictionary - Tidy Data from UCI HAR Dataset"" section.

#### Data Dictionary - Tidy Data from UCI HAR Dataset
activity :  

Activity of daily living (ADL) performed while carrying a waist-mounted smartphone with embedded inertial sensors. 

LAYING 

SITTING 

STANDING 

WALKING 

WALKING_DOWNSTAIRS 

WALKING_UPSTAIRS

subject 

One of a group of 30 volunteers within an age bracket of 19-48 years who performed the activities in the experiment.     Range is from 1 to 30 denoting each different test subject.

tBodyAccMeanX 

Mean of the mean value of the Body Acceleration time domain signal on the x axis of the phone normalized and bounded within [-1,1].

tBodyAccMeanY 

Mean of the mean value of the Body Acceleration time domain signal on the y axis of the phone normalized and bounded within [-1,1].

tBodyAccMeanZ 

Mean of the mean value of the Body Acceleration time domain signal on the z axis of the phone normalized and bounded within [-1,1].

tBodyAccStdX 

Mean of the Standard Deviation of the Body Acceleration time domain signal on the x axis of the phone normalized and bounded within [-1,1].

tBodyAccStdY 

Mean of the Standard Deviation of the Body Acceleration time domain signal on the y axis of the phone normalized and bounded within [-1,1].

tBodyAccStdZ 

Mean of the Standard Deviation of the Body Acceleration time domain signal on the z axis of the phone normalized and bounded within [-1,1].

tGravityAccMeanX 

Mean of the mean value of the Gravity Acceleration time domain signal on the x axis of the phone normalized and bounded within [-1,1].

tGravityAccMeanY 

Mean of the mean value of the Gravity Acceleration time domain signal on the y axis of the phone normalized and bounded within [-1,1].

tGravityAccMeanZ 

Mean of the mean value of the Gravity Acceleration time domain signal on the z axis of the phone normalized and bounded within [-1,1].

tGravityAccStdX 

Mean of the Standard Deviation of the Gravity Acceleration time domain signal on the x axis of the phone normalized and bounded within [-1,1].

tGravityAccStdY 

Mean of the Standard Deviation of the Gravity Acceleration time domain signal on the y axis of the phone normalized and bounded within [-1,1].

tGravityAccStdZ 

Mean of the Standard Deviation of the Gravity Acceleration time domain signal on the z axis of the phone normalized and bounded within [-1,1].

tBodyAccJerkMeanX 

Mean of the mean value of the Jerk of the Body Acceleration time domain signal on the x axis of the phone normalized and bounded within [-1,1].

tBodyAccJerkMeanY 

Mean of the mean value of the Jerk of the Body Acceleration time domain signal on the y axis of the phone normalized and bounded within [-1,1].

tBodyAccJerkMeanZ 

Mean of the mean value of the Jerk of the Body Acceleration time domain signal on the z axis of the phone normalized and bounded within [-1,1].

tBodyAccJerkStdX 

Mean of the Standard Deviation of the Jerk of the Body Acceleration time domain signal on the x axis of the phone normalized and bounded within [-1,1].

tBodyAccJerkStdY 

Mean of the Standard Deviation of the Jerk of the Body Acceleration time domain signal on the y axis of the phone normalized and bounded within [-1,1].

tBodyAccJerkStdZ 

Mean of the Standard Deviation of the Jerk of the Body Acceleration time domain signal on the z axis of the phone normalized and bounded within [-1,1].

tBodyGyroMeanX 

Mean of the mean value of the Angular Body time domain signal on the x axis of the phone normalized and bounded within [-1,1].

tBodyGyroMeanY 

Mean of the mean value of the Angular Body time domain signal on the y axis of the phone normalized and bounded within [-1,1].

tBodyGyroMeanZ 

Mean of the mean value of the Angular Body time domain signal on the z axis of the phone normalized and bounded within [-1,1].

tBodyGyroStdX 

Mean of the Standard Deviation of the Angular Body time domain signal on the x axis of the phone normalized and bounded within [-1,1].

tBodyGyroStdY 

Mean of the Standard Deviation of the Angular Body time domain signal on the y axis of the phone normalized and bounded within [-1,1].

tBodyGyroStdZ 

Mean of the Standard Deviation of the Angular Body time domain signal on the z axis of the phone normalized and bounded within [-1,1].

tBodyGyroJerkMeanX 

Mean of the mean value of the Angular Jerk of the Body time domain signal on the x axis of the phone normalized and bounded within [-1,1].

tBodyGyroJerkMeanY 

Mean of the mean value of the Angular Jerk of the Body time domain signal on the y axis of the phone normalized and bounded within [-1,1].

tBodyGyroJerkMeanZ 

Mean of the mean value of the Angular Jerk of the Body time domain signal on the z axis of the phone normalized and bounded within [-1,1].

tBodyGyroJerkStdX 

Mean of the Standard Deviation of the Angular Jerk of the Body time domain signal on the x axis of the phone normalized and bounded within [-1,1].

tBodyGyroJerkStdY 

Mean of the Standard Deviation of the Angular Jerk of the Body time domain signal on the y axis of the phone normalized and bounded within [-1,1].

tBodyGyroJerkStdZ 

Mean of the Standard Deviation of the Angular Jerk of the Body time domain signal on the z axis of the phone normalized and bounded within [-1,1].

tBodyAccMagMean 

Mean of the mean value of the Magnitude of the Body Acceleration time domain signal normalized and bounded within [-1,1].

tBodyAccMagStd 

Mean of the Standard Deviation of the Magnitude of the Body Acceleration time domain signal normalized and bounded within [-1,1].

tGravityAccMagMean 

Mean of the mean value of the Magnitude of the Gravity Acceleration time domain signal normalized and bounded within [-1,1].

tGravityAccMagStd 

Mean of the Standard Deviation of the Magnitude of the Gravity Acceleration time domain signal normalized and bounded within [-1,1].

tBodyAccJerkMagMean 

Mean of the mean value of the Magnitude of the Jerk of the Body Acceleration time domain signal normalized and bounded within [-1,1].

tBodyAccJerkMagStd 

Mean of the Standard Deviation of the Magnitude of the Jerk of the Body Acceleration time domain signal normalized and bounded within [-1,1].

tBodyGyroMagMean 

Mean of the mean value of the Angular Magnitude of the Body time domain signal normalized and bounded within [-1,1].

tBodyGyroMagStd 

Mean of the Standard Deviation of the Angular Magnitude of the Body time domain signal normalized and bounded within [-1,1].

tBodyGyroJerkMagMean 

Mean of the mean value of the Angular Magnitude of the Jerk of the Body time domain signal normalized and bounded within [-1,1].

tBodyGyroJerkMagStd 

Mean of the Standard Deviation of the Angular Magnitude of the Jerk of the Body time domain signal normalized and bounded within [-1,1].

fBodyAccMeanX 

Mean of the mean value of the Body Acceleration frequency domain signal on the x axis of the phone normalized and bounded within [-1,1].

fBodyAccMeanY 

Mean of the mean value of the Body Acceleration frequency domain signal on the y axis of the phone normalized and bounded within [-1,1].

fBodyAccMeanZ 

Mean of the mean value of the Body Acceleration frequency domain signal on the z axis of the phone normalized and bounded within [-1,1].

fBodyAccStdX 

Mean of the Standard Deviation of the Body Acceleration frequency domain signal on the x axis of the phone normalized and bounded within [-1,1].

fBodyAccStdY 

Mean of the Standard Deviation of the Body Acceleration frequency domain signal on the y axis of the phone normalized and bounded within [-1,1].

fBodyAccStdZ 

Mean of the Standard Deviation of the Body Acceleration frequency domain signal on the z axis of the phone normalized and bounded within [-1,1].

fBodyAccJerkMeanX 

Mean of the mean value of the Jerk of the Body Acceleration frequency domain signal on the x axis of the phone normalized and bounded within [-1,1].

fBodyAccJerkMeanY 

Mean of the mean value of the Jerk of the Body Acceleration frequency domain signal on the y axis of the phone normalized and bounded within [-1,1].

fBodyAccJerkMeanZ 

Mean of the mean value of the Jerk of the Body Acceleration frequency domain signal on the z axis of the phone normalized and bounded within [-1,1].

fBodyAccJerkStdX 

Mean of the Standard Deviation of the Jerk of the Body Acceleration frequency domain signal on the x axis of the phone normalized and bounded within [-1,1].

fBodyAccJerkStdY 

Mean of the Standard Deviation of the Jerk of the Body Acceleration frequency domain signal on the y axis of the phone normalized and bounded within [-1,1].

fBodyAccJerkStdZ 

Mean of the Standard Deviation of the Jerk of the Body Acceleration frequency domain signal on the z axis of the phone normalized and bounded within [-1,1].

fBodyGyroMeanX 

Mean of the mean value of the Angular Body frequency domain signal on the x axis of the phone normalized and bounded within [-1,1].

fBodyGyroMeanY 

Mean of the mean value of the Angular Body frequency domain signal on the y axis of the phone normalized and bounded within [-1,1].

fBodyGyroMeanZ 

Mean of the mean value of the Angular Body frequency domain signal on the z axis of the phone normalized and bounded within [-1,1].

fBodyGyroStdX 

Mean of the Standard Deviation of the Angular Body frequency domain signal on the x axis of the phone normalized and bounded within [-1,1].

fBodyGyroStdY 

Mean of the Standard Deviation of the Angular Body frequency domain signal on the y axis of the phone normalized and bounded within [-1,1].

fBodyGyroStdZ 

Mean of the Standard Deviation of the Angular Body frequency domain signal on the z axis of the phone normalized and bounded within [-1,1].

fBodyAccMagMean 

Mean of the mean value of the Magnitude of the Body Acceleration frequency domain signal normalized and bounded within [-1,1].

fBodyAccMagStd 

Mean of the Standard Deviation of the Magnitude of the Body Acceleration frequency domain signal normalized and bounded within [-1,1].

fBodyBodyAccJerkMagMean 

Mean of the mean value of the Magnitude of the Jerk of the Body Acceleration frequency domain signal normalized and bounded within [-1,1].

fBodyBodyAccJerkMagStd 

Mean of the Standard Deviation of the Magnitude of the Jerk of the Body Acceleration frequency domain signal normalized and bounded within [-1,1].

fBodyBodyGyroMagMean 

Mean of the mean value of the Angular Magnitude of the Body frequency domain signal normalized and bounded within [-1,1].

fBodyBodyGyroMagStd 

Mean of the Standard Deviation of the Angular Magnitude of the Body frequency domain signal normalized and bounded within [-1,1].

fBodyBodyGyroJerkMagMean 

Mean of the mean value of the Angular Magnitude of the Jerk of the Body frequency domain signal normalized and bounded within [-1,1].

fBodyBodyGyroJerkMagStd 

Mean of the Standard Deviation of the Angular Magnitude of the Jerk of the Body frequency domain signal normalized and bounded within [-1,1].


