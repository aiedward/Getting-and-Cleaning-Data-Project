
The Rscript named "run_analysis.R", it commented highly, self-explanatory and detailed overview of what it done, step by step: (Square brackets "[ ]" are used here to denote variables, vectors, data frames, etc. used in the script)

	1.Reads the names of all features from features.txt into [feature_names_original].

	2.Identifies the indices for "mean" [mean_indices] and "std" [std_indices] features only, and keeps them sorted in [indices], together with their respective descriptions.

	3.Separates [indices] into [feature_indices] and [feature_names], to be later used as column names.

	4.Tides up these variable names:
		1.Changes "-" to "_"
		2.Deals with duplicate "Body" in "BodyBody"
		
	5.Reads the activity labels into [activity_labels].
	
	6.Reads the training and the test sets, and processes both of them in the same manner:
		6.1.Takes only selected columns, as per [feature_indices], and stores data in [X_train / X_test].
		6.2.Assigns feature names to data.
		6.3.Reads training subject IDs into [X_tr_subject / X_ts_subject].
		6.4.Assigns a column name "subject" instead of "V1".
		6.5.Reads the training activity index into [y_train_ind / y_test_ind].
		6.6.Assigns a column name "activity_index" instead of "V1".
		6.7.Merges (by binding columns) the subject IDs + activity ind + measurements into [X_tr_temp / X_ts_temp].
		6.8.Merges (by joining) in order to get activity descriptions (in addition ti IDs) into [X_tr_description / X_ts_description].
		6.9.Creates tidy training / test sets into [X_tr / X_ts].
			6.9.1.subject ID first
			6.9.2.activity descriptions second
			6.9.3.then all the mean / std measurements
	
	7.Merges the training and the test sets to create one data set [X].
	
	8.From the data set [X], it creates a second, independent tidy data set with the average of each variable for each activity and each subject. It is called [agg_wide], as it shows an aggregation in the wide (rather than long) format.
	
	9.Makes sure that [agg_wide] is tidy and self-explanatory:
		9.1.First columns, by which aggregation is done, are named properly ("activity_description" and "subject" respectively).
		9.2.All subsequent mean variables are prefixed with "Mean_of_".
		9.3.Rows are sorted by "Activity_Sescription" and "Subject".
		
	10.Creates a file named "tidy.txt" from [agg_wide]. This data set can be found in this repo.
