# PA4 - DATA WRANGLING AND DATA VISUALIZATION
This repository contains Python scripts designed to address a range of programming problems in ECE2112. The focus is on Data Wrangling and Visualization and the utilization of the Pandas and Matplot libraries. Presented below are the key concepts and functionalities used in the given Python exercises.

***
### Intended Learning Outcomes:
1. To identify the codes and functions needed in cleaning and visualizing data
2. To be able to apply and use the different codes and functions in creating a Python program that will be used in data wrangling and data visualization

***
### Introduction to Data Wrangling:
Data wrangling (also called data munching) involves manipulation and transformation of data frames in
preparation for data analytics. <br><br>
Why do we need to do this? <br> 
* To make the data useful.
> Useful data can be referred to as information: processed, organized, or structured data that provides
meaning, context, or insight. 

This is achieved by converting raw (unrefined or messy) data and turning it to a format
with the intent of making it more appropriate, valuable and useful for data analytics.

***

# ECE BOARD EXAM PROBLEM: 
### Instructions: 
Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.
<br>
* Create the following data frames based on the format provided: <br>
Example: Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as Visayas <br>
Output: <br>
![Screen Shot 2024-09-19 at 1 13 55 AM](https://github.com/user-attachments/assets/9d9fb968-b2fa-41c8-a62a-5f833ce80cdd)


* Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon
* Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female
* Create a visualization that shows how the different features contributes to average grade. Does
chosen track in college, gender, or hometown contributes to a higher average score?

##

### List of Essential Syntax and their Functions in the Given Python Excercise: 
1.) Creating data frame for instrumentation
```
Instru = data[(data['Track'] == 'Instrumentation') & (data['Hometown'] == 'Luzon') & (data['Electronics'] > 70)][['Name', 'GEAS', 'Electronics']]
```
> The syntax utilizes boolean logic to filter a DataFrame, data, based on specific criteria related to student characteristics. It checks for three conditions: whether the 'Track' is 'Instrumentation', the 'Hometown' is 'Luzon', and the 'Electronics' score is greater than 70. The result is a new DataFrame, Instru, that contains only the 'Name', 'GEAS', and 'Electronics' columns for students who meet all these criteria
<br>

2.) Creating a new column 'Average' in the original data frame
```
data['Average'] = data[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
```
> The syntax computes the average scores for each student across four subjects—'Math', 'Electronics', 'GEAS', and 'Communication'—and adds this average as a new column named 'Average' in the DataFrame.
<br>

3.) Creating data frame for Mindy
```
Mindy = data.loc[(data['Hometown'] == 'Mindanao') & (data['Gender'] == 'Female') & (data['Average'] >= 55), ['Name', 'Track', 'Electronics', 'Average']]
```
> The syntax computes the average scores for each student across four subjects—'Math', 'Electronics', 'GEAS', and 'Communication'—and adds this average as a new column named 'Average' in the DataFrame.
<br>

4.) Calculating the average grade for each track, gender, and hometown
```
track_ave = data.groupby('Track')['Average'].mean()
gender_ave = data.groupby('Gender')['Average'].mean()
hometown_ave = data.groupby('Hometown')['Average'].mean()
```
> The syntax calculates the average scores of students in the DataFrame data by grouping them based on their 'Track', 'Gender', and 'Hometown'. It creates three separate variables—track_ave, gender_ave, and hometown_ave—that store the average scores for each group, facilitating comparative analysis of student performance across these categories.
<br>

5.) Creating the Figure and Subplots
```
fig, ax = plt.subplots(1, 3, figsize=(15, 5))
```
> The syntax creates a figure (fig) with 3 subplots (ax) arranged in a single row.
<br>

6.) Plot 1: Average Grades for Each Track
```
ax[0].bar(track_ave.index, track_ave.values, color=colors[0])
ax[0].set_title('Average Grade - Track')
ax[0].set_xlabel('Track')
ax[0].set_ylabel('Average Grade')
```
> This block creates a bar chart for "Average Grade - Track".
<br> **ax[0]:** Refers to the second subplot (indexed at 0).
<br> **bar(gender_ave.index, gender_ave.values, color=colors[0]):** This creates the bar chart with the average grades for each gender, using 'green' as the color.
<br> <br> Note: Plot 2 and Plot 3 follows the same flow of this syntax.
<br>

7.) Adjusting Layout for Spacing
```
plt.tight_layout()
```
> This function adjusts the spacing between the subplots and prevents elements (titles, labels) from overlapping with each other. It ensures a cleaner and more professional appearance.
<br>

7.) Displaying the Plot
```
plt.show()
```
> This function renders and displays the figure with all three subplots. Without plt.show(), the plots may not appear (especially in script-based environments).

##

### Output and Graph Analysis: 
![Screen Shot 2024-09-19 at 8 20 08 AM](https://github.com/user-attachments/assets/e9ef94c8-51ce-4d4d-9d6e-6e78dd548b03)

#### Average Grade - Track:
* The first graph shows three tracks: Communication, Instrumentation, and Microelectronics.
* The average grades for all three tracks are relatively similar, each around the 60s mark. This suggests a consistent performance across the tracks in terms of grading.

#### Average Grade - Gender:
* The second graph compares the average grades between females and males.
* Both genders have almost identical average grades, again in the 60s, indicating no significant gender-based differences in grade outcomes for the sampled population.

#### Average Grade - Hometown:
* The third graph categorizes average grades by the students' hometown regions: Luzon, Mindanao, and Visayas.
* Similar to the other graphs, all three regions show nearly equal average grades, suggesting that the hometown region does not significantly influence the grading outcomes.
<br>

> Does chosen track in college, gender, or hometown contributes to a higher average score? <br>

Based on the graphs alone, these three factors (track, gender, or hometown) do not appear to contribute to a higher average score. The minimal variation in average grades across the categories—track (Communication, Instrumentation, Microelectronics), gender (Female, Male), and hometown (Luzon, Mindanao, Visayas)—shows that all groups scored around the 60s, a nearly identical average.



***
### References
* M, R. (2021, January 15). What Is Pyplot In Matplotlib. ActiveState. https://www.activestate.com/resources/quick-reads/what-is-pyplot-in-matplotlib/
* Electronics Engineering Department (September 2024). Data Wrangling and Data Visualization, PowerPoint Slides

***
### Submitted by:
Michelle Sophia. Abamonga
<br> 2023184181
<br> 2-ECEB





