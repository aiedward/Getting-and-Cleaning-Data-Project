Getting and Cleaning Data Project
=================================
Introduction:
-------------
The purpose of this project is to demonstrate the ability to collect, work with, and clean a data set. The goal is to prepare tidy data that can be used for later analysis. 

Description of original dataset:
--------------------------------
The data linked to from the course website represent data collected from the accelerometers from the Samsung Galaxy S smartphone. A full description is available at the site where the data was obtained:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

Here are the data for the project:

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

Data Set Information:
---------------------
The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

Processing:
-----------
From the original data set a series of steps were followed in order to obtain a tidy data set for further postprocessing. 
To carry out this process the [run_analysis.R](https://github.com/aiedward/Getting-and-Cleaning-Data-Project/blob/master/run_analysis.R) script was used. 

The steps go from downloading the original dataset, extracting it and performing reshaping and postprocessing. 
The different steps are described inside [run_analysis.R](https://github.com/aiedward/Getting-and-Cleaning-Data-Project/blob/master/run_analysis.R) but a general overview includes:
- Merging the training and the test subjects into a single dataset.
- Extracting only the measurements corresponding to the mean (**mean()**) and standard deviation (**std()**) for each available measurement. 
- Joining the subjects with the activities performed by the subjects with the measurements from the dataset.
- Evaluating the mean per subject and activity of the available meassurements and sorting by subject and activity.
- Saving the resulting dataset in a text file.
- Saving the dataset column names in a text file.

The resulting dataset [tidy.txt](https://github.com/aiedward/Getting-and-Cleaning-Data-Project/blob/master/tidy.txt) contains 66 columns of averaged information (per subject and activity) corresponding to the **Mean** and **std** of different meassurements for a total of 180 observations (30 subjects x 6 activities). 

These observations include meassurements in **Time** and **Frequency** of magnitude (**Mag**) and components in **X**,**Y** and **Z** direction for the linear acceleration (**Acc**), angular acceleration (**Gyro**), linear jerk (**AccJerk**) and angular jerk (**GyroJerk**) for both **Body** and **Gravity** components. Columns 1 and 2 correspond to the **Subject** and **Activity**. 

Postprocessing:
---------------
A detailed description of the variable names (columns) found in [tidy.txt](https://github.com/aiedward/Getting-and-Cleaning-Data-Project/blob/master/tidy.txt) and the dataset For more information please refer to [CodeBook.md](https://github.com/aiedward/Getting-and-Cleaning-Data-Project/blob/master/CodeBook.md)

This project includes the following files:
------------------------------------------
- 'README.md': Read me documents.
- 'CodeBook.md': List of all features.
- 'run_analysis.R': Main R script performing the tidy operations.
- 'test.md': Test Github files
- 'tidy.txt': Tidy dataset.  

