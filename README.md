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

An issue was then brought up with the data involving falsified grades.  In order for the data to be re-evaluated, I needed to implement code that would remove the fraudulent test scores from the sample so that the analysis could be run again.

```python
# Example code
```

---

## Analysis
| Highest Performing School |
| -------- |
| Avg. Math Score   | Avg. Reading Score   |
| cell 3   | cell 4   |

| Lowest Performing School |
| -------- |
| Avg. Math Score   | Avg. Reading Score   |
| cell 3   | cell 4   |

---

## Challenge Summary
A big part of data anlysis is identifying, gathering, formatting, and cleaning large data sets.
