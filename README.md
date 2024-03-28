The purpose of the following script is to develop all the tables and figures needed for the technical report of the clinical study. 

The study was to compare the performance of Pymaceuticals’ drug of interest, Capomulin, against the other treatment regimens.

They have also asked you for a top-level summary of the study results.

This study was conducted on
249 mice with drug regimens; 
Capomulin, Ramicane, Infubinol, and Ceftamin.

Over 45 days, Tumor development was observed and measured for each treatment.


INPUT: 
Mouse_metadata.csv:
	 Contains metadata about each mouse including:
	 ID, drug regimen, sex, and weight.

Study_results.csv: 
	Contains the results of the study including:
	data on tumor volume, timepoints, and mouse ID.



Data Prep and Cleaning:
Read the CSV files containing mouse metadata and study results.

Merge these datasets on the 'Mouse ID' column into a single DataFrame.	- complete_mouse_data
	
Identify and remove any duplicate entries in the dataset.		- clean_mouse_data


Summary Statistics:

Group the data by drug regimen, 					- Drug_regimen_complete
calculate summary statistics: 
mean, median, variance, standard deviation, and standard error of the mean (SEM) for tumor volume.

Assemble the resulting series into a single summary DataFrame using Pandas and using aggregation methods.


Data Visualization:

Bar Plotting 
Drug_regimen_complete - Grouped by Drug Regimen.
Count each timepoint within each group, grouped by Drug Regimen.
Create a bar plot with count as the value and drug regimen name as the labels.


Pie Plotting
Count how many times different values occur within the 'sex' column.
plot as a pie chart.


Box Plotting
Start by getting the last (greatest) timepoint for each mouse.
	Cut columns to just include, mouse ID and timepoints.
	Groupby mouse ID then find the maximum value within each group.
Merge this grouped Dataframe with the original DataFrame by matching values of 'Timepoints' and 'Mouse ID',
this ensures only the rows with the maximum timpoints for each mouse will be taken.

Put treatments into a list, 

create a for loop that, for each drug:
	Locates the rows which contain tumor volumes and puts into a new list.
	Determine outliers using upper and lower bounds of each list of tumor volumes.
	prints each tumor volume lists outliers.

Generate a box plot that shows the distrubution of the tumor volume for each treatment group and outliers.



Line Plotting 
Set index to Mouse ID to find just rows with the ID we are looking for.
plot tumor volume vs time for the one mouse ID.

Scatter Plotting
Set index to Drug Regimen to find just rows with the drug we are looking for.
Take drug Capomulin and Columns for Tumor Volume, Weight and Mouse ID.
Group the mouse by 'Mouse ID' so we can find mean values for each individual mouse.
Find the mean tumor volume for each mouse.
We Need x and Y series sizes to be the same for plotting a scatter graph.
        # Assuming the weight stays the same for each mouse, or fluctuates slightly.
        # find mean weight of each mouse.

Regression Analysis:
Correlation Calculation: Calculate the correlation coefficient between mouse weight and average tumor volume.
Linear Regression: Perform linear regression analysis to model the relationship between mouse weight and tumor volume. Plot the regression line along with the scatter plot.
Assumptions:
Each mouse in the study has unique identification (Mouse ID).
Tumor volume measurements are accurate and consistent.
The data is representative of the study population and doesn't contain significant errors or biases.
Outliers in the dataset may indicate anomalies but are not necessarily errors.
Key Takeaways:
Different drug regimens have varying effects on tumor volume.
Mouse weight correlates with tumor volume, indicating a potential relationship between these two variables.
Visualization techniques such as bar plots, pie charts, box plots, and scatter plots provide valuable insights into the data distribution and relationships between variables.
Statistical analysis helps in quantitatively understanding the central tendency and variability of the data.
Conclusion:
This analysis provides a comprehensive understanding of the mouse study data, including data cleaning, summary statistics, visualization, and regression analysis. The findings contribute to the understanding of how different drug regimens affect tumor growth and the relationship between mouse weight and tumor volume.



