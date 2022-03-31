# School_District_Analysis

#### Christopher Madden

---

## Project Overview
Here is the list of deliverables for the analysis of the school district: 

  - A high-level snapshot of the district's key metrics, presented in a table format
  - An overview of the key metrics for each school, presented in a table format
  - Tables presenting each of the following metrics:
    - Top 5 and bottom 5 performing schools, based on the overall passing rate
    - The average math score received by students in each grade level at each school
    - The average reading score received by students in each grade level at each school
    - School performance based on the budget per student
    - School performance based on the school size 
    - School performance based on the type of school

---

## Resources

GitHub Repository URL:

https://github.com/maddenc33/School_District_Analysis

### Data Sources

 - schools_complete.csv

 - students_complete.csv

### Software

 - Python 3.9.7

 - Jupyter Notebook 6.4.5

 - Anaconda 4.12.0

  >  conda version : 4.12.0
  > 
  >  conda-build version : 3.21.6
  > 
  >  python version : 3.9.7.final.0

---

# Summary

---

## Challenge Overview
The first challenge I faced involved cleaning the data.  The following python methods were performed to clean the data:
  1. Find missing values.  Methods used include: .count(), .isnull() and .notnull().
  2. Handle missing data: .dropna() and .fillna().
  3. Determine data types: .dtypes
  4. Replace inccorect student names: .len(), .to_list() .split(), .set(), .strip(), and .replace().
  5. Generate a new merged dataframe: .merge().

Once the data was clean and ready for analysis, I performed basic statistical calculations on the data, then formatted and reordered the dataframe to create a new **School District Summary**.

The **School District Summary** is a high-level snapshot of the district's key metrics:

- Total number of students
- Total number of schools
- Total budget
- Average math score
- Average reading score
- Percentage of students who passed math
- Percentage of students who passed reading
- Overall passing percentage

In order to generate the **School Summary**, I had to manipulate the data further, using similar methods as before:
  1. Set the index to the school name.
  2. Get the student count per school.
  3. Calculate the budget per student.
  4. Calculate the score averages per school.
  5. Calculate the passing percentages per school.
  6. Create the new dataframe and clean it up.
Once the dataframes were clean and ready for analysis, I could make statistical calulations on the data to determine the highest and lowest performing schools.

An issue was then brought up with the data involving falsified grades.  In order for the data to be re-evaluated, I needed to implement code that would remove the fraudulent test scores from the sample so that the analysis could be run again.  Below is an example of the code used to accomplish the removal of bad data:

```python

# Get the number of 10th-12th graders from Thomas High School (THS).
thomas_10_to_12 = student_data_df.loc[((student_data_df["grade"] == "10th") | (student_data_df["grade"] == "11th") | (student_data_df["grade"] == "12th")) & (student_data_df["school_name"] == "Thomas High School"), "Student ID"].count()

# Get all the students passing math from THS
thomas_passing_math_df = student_data_df.loc[((student_data_df["grade"] == "10th") | (student_data_df["grade"] == "11th") | (student_data_df["grade"] == "12th")) & (student_data_df["math_score"] >= 70) & (student_data_df["school_name"] == "Thomas High School")]

# Get all the students passing reading from THS
thomas_passing_reading_df = student_data_df.loc[((student_data_df["grade"] == "10th") | (student_data_df["grade"] == "11th") | (student_data_df["grade"] == "12th")) & (student_data_df["reading_score"] >= 70) & (student_data_df["school_name"] == "Thomas High School")]

# Get all the students passing math and reading from THS
thomas_passing_both_df = student_data_df.loc[((student_data_df["grade"] == "10th") | (student_data_df["grade"] == "11th") | (student_data_df["grade"] == "12th")) & (student_data_df["math_score"] >= 70) & (student_data_df["reading_score"] >= 70) & (student_data_df["school_name"] == "Thomas High School")]

# Calculate the percentage of 10th-12th grade students passing math from Thomas High School.
thomas_math_percent = thomas_passing_math_df["Student ID"].count() / thomas_10_to_12 *100

# Calculate the percentage of 10th-12th grade students passing reading from Thomas High School.
thomas_reading_percent = thomas_passing_reading_df["Student ID"].count() / thomas_10_to_12 *100

# Calculate the overall passing percentage of 10th-12th grade from Thomas High School. 
thomas_ovr_percent = thomas_passing_both_df["Student ID"].count() / thomas_10_to_12 *100

# Replace the passing math percent for Thomas High School in the per_school_summary_df.
per_school_summary_df.loc["Thomas High School","% Passing Math"] = thomas_math_percent

# Replace the passing reading percentage for Thomas High School in the per_school_summary_df.
per_school_summary_df.loc["Thomas High School","% Passing Reading"] = thomas_reading_percent

# Replace the overall passing percentage for Thomas High School in the per_school_summary_df.
per_school_summary_df.loc["Thomas High School","% Overall Passing"] = thomas_ovr_percent

```

---

## Analysis
The following is a summary of some of the key overall findings:

| Highest Performing School | Cabrera High School |
| --- | --- |
| Avg. Math Score   | 94.1% |
| Avg. Reading Score   | 97.0% |
| Overall Avg. Score | 91.3% |

| Lowest Performing School | Rodriguez High School |
| --- | --- |
| Avg. Math Score   | 66.4% |
| Avg. Reading Score   | 80.2% |
| Overall Avg. Score | 53.0% |

Scores by School Spending:

| Spending Ranges (Per Student) | Average Math Score |	Average Reading Score	| % Passing Math |	% Passing Reading |	% Overall Passing	 |		
| --- | --- | --- | --- | --- | --- |
| <$586	| 83.5 |	83.9 |	93	| 97	| 90 |
| $586-630 |	81.9	| 83.2 |	87 |	93 |	81 |
| $631-645	|78.5 |	81.6 |	73 |	84 |	63  |
| $646-675 |	77.0	| 81.0	| 66	| 81	| 54 |

Scores by School Size:

| School Size | Average Math Score |	Average Reading Score	| % Passing Math |	% Passing Reading |	% Overall Passing	|
| --- | --- | --- | --- | --- | --- |
| Small (<1000)	| 83.8 |	83.9 |	94 |	96 |	90 |
| Medium (1000-1999)	| 83.4	| 83.9	| 94	| 97	| 91 |
| Large (2000-5000)	| 77.7	| 81.3 |	70	| 83 |	58 |

Scores by School Type:

| School Type | Average Math Score |	Average Reading Score |	% Passing Math |	% Passing Reading	| % Overall Passing	|	
| --- | --- | --- | --- | --- | --- |
| Charter |	83.5 |	83.9 |	94 |	97 |	90 |
| District	| 77.0	| 81.0	| 67	| 81	| 54 |

---

## Challenge Summary
A big part of data anlysis is identifying, gathering, formatting, and cleaning large data sets.  Not only did we have to perform a lot of cleaning and formatting of the data initially, I also have to have the ability to retroactively reclean and reformat the data if an issue arises, as is the case here with fraudulent test scores.  Python, through the Pandas library, makes handling and manipulating large data sets like these much easier to automate.

An analysis of this particular data demonstrates how the outcome changed based on the inclusion or exclusion of the now fraudulent Thomas High School 9th grade reading and math score data.  The following are some of the statistical metrics that changed when we removed the fraudulent data:

 - Thomas High School saw a drop in overall passing percentage of less than 1% and remained the #2 overall highest scoring school.
 - It seems as though, in this dataset, there exists a negative correlation between school spending and the resulting test scores.
 - Larger schools seem to correlate to lower overall passing percentage.  There is a negative correlation.
 - Charter schools generally outperform district schools.
 - Reading scores are overall higher than math scores.
