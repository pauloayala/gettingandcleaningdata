The run_analysis.R script executes the data preparation and then followed by the 5 steps asked as described in project’s definition.

Step 1: Download the dataset
Download Dataset and extract to the folder named "UCI HAR Dataset"

Step 2: Assigning each data to variables
features <- features.txt : 561 rows, 2 columns 
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
activities <- activity_labels.txt : 6 rows, 2 columns 
List of activities executed when the corresponding measurements were taken and its respectives codes
subject_test <- test/subject_test.txt : 2947 rows, 1 column 
includes test data of 9/30 volunteer test subjects observed
x_test <- test/X_test.txt : 2947 rows, 561 columns 
includes recorded features test data
y_test <- test/y_test.txt : 2947 rows, 1 columns 
includes test data of activities’code labels
subject_train <- test/subject_train.txt : 7352 rows, 1 column 
includes train data of 21/30 volunteer subjects observed
x_train <- test/X_train.txt : 7352 rows, 561 columns 
includes recorded features train data
y_train <- test/y_train.txt : 7352 rows, 1 columns 
includes train data of activities’code labels

Step 3: Joined the training and the test data sets to create one data set
X (10299 rows, 561 columns) was created by merging x_train and x_test using rbind() function
Y (10299 rows, 1 column) was created by merging y_train and y_test using rbind() function
Subject (10299 rows, 1 column) was created by merging subject_train and subject_test using rbind() function
Merged_Data (10299 rows, 563 column) was created by merging Subject, Y and X using cbind() function

Step 4: Extracts only the measurements on the standard deviation and the mean to each measurement
TidyData (10299 rows, 88 columns) is created by subsetting Joined_Data, selecting only columns: subject, code and the measurements on the standard deviation (std) and mean to each measurement

Step 5: Uses descriptive activity names to call the activities in the data set. Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable
Appropriately labels the data set with descriptive variable names:
a) code column in TidyData renamed into activities
b) All BodyBody in column’s name replaced by Body
c) All Gyro in column’s name replaced by Gyroscope
d) All Acc in column’s name replaced by Accelerometer
e) All Mag in column’s name replaced by Magnitude
f) All start with character f in column’s name replaced by Frequency
g) All start with character t in column’s name replaced by Time
h) All "-mean()" in column’s name replaced by Mean
i) All "-std()" in column’s name replaced by STD
k) All "-freq()" in column’s name replaced by Frequency
l) All "angle" in column’s name replaced by Angle
m) All "gravity" in column’s name replaced by Gravity

Step 6: From the data set in step 4, creates a second tidy data set with the average of each variable for each activity and each subject. LastData has 180 rows and 88 columns. It was created by sumarizing TidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity. And finallly, export LastData into LastData.txt file.