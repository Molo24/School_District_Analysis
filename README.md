# School_District_Analysis

## Overview & Purpose
The local School Board asked for an analysis to be done on student funding and student standardized test scores (math & reading) across the schools of the district. The goal is to aggregate the data and identify trends and/or relationships between funding and student success.

Further, Thomas High School 9th grade scores are suspect. Following the initial analysis, these scores will be replaced with "NaN" values and the analysis with be re-performed.

The analysis was undertaken using Python, Jupyter Notebook and Pandas

## Analysis
### Investigation and Cleaning the Data
The project consisted to two datasets (student data & school data).
#### Each of these had to be read in as a Panda DataFrame:
```
school_data_to_load = "Resources/schools_complete.csv"
student_data_to_load = "Resources/students_complete.csv"

school_data_df = pd.read_csv(school_data_to_load)
student_data_df = pd.read_csv(student_data_to_load)
```
#### Investigate each CSV file
```
school_data_df.count() # count lines
student_data_df.count() # count lines

school_data_df.isnull() # look for null values
student_data_df.isnull() # look for null values
```

#### The data was then inspected and student data was cleaned of any erroneous prefixes and/or suffixes:
```
prefixes_suffixes = ["Dr. ", "Mr. ","Ms. ", "Mrs. ", "Miss ", " MD", " DDS", " DVM", " PhD"]

for word in prefixes_suffixes:
    student_data_df["student_name"] = student_data_df["student_name"].str.replace(word,"")
```
#### Lastly, replace the Thomas High School 9th grade student math and readings scores with "Nan":
```
student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "reading_score"] = np.nan
student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "math_score"] = np.nan
```
Once the data has been investigated the analysis can begin.


**Before** = Analysis done before Thomas High School 9th grade math and reading scores were replaced by "Nan".

**After** = Analysis done after Thomas High School 9th grade math and reading scores were replaced by "Nan".


### Question 1
**How is the district summary affected following the replacement of Thomas High School 9th grade student's math and reading scores?**

We can see the District Summary DataFrames below:
* Total Students dropped
* Average Math Score went down
* Average Reading score stayed the same
* Percent Passing Math dropped
* Percent Passing Reading dropped
* Overall Passing % dropped

Before
![District_Summary_Full](https://user-images.githubusercontent.com/89284280/134444025-5d83c564-041c-44a0-9b39-8682e5f5f438.PNG)
After
![District_Summary_After](https://user-images.githubusercontent.com/89284280/134444935-66db799b-601c-45ce-86e3-fe17f7de0d91.PNG)

### Question 2
**How is the school summary affected following the replacement of Thomas High School 9th grade student's math and reading scores?**\
Thomas High School's % Passing Math, % Passing Reading and % Overall Passing increased following the removal of the 9th grader scores.

Before
![School_Summary_Before](https://user-images.githubusercontent.com/89284280/134446487-db597386-8b2e-49e6-b8dc-341203f0f4fe.PNG)

After
![School_Summary_After](https://user-images.githubusercontent.com/89284280/134446818-1e5b26c4-4789-40c4-86e8-da079798c379.PNG)

### Question 3
**What are the top 5 and bottom 5 performing schools, based on the overall passing rate?**

No changes in ranking of Top 5 or Bottom 5

Top 5 (Before)
![top_schools_before](https://user-images.githubusercontent.com/89284280/134447579-42d7bbe8-b184-4441-9cde-8b585341697a.PNG)

Top 5 (After)
![top_schools_after](https://user-images.githubusercontent.com/89284280/134447595-ab6d6482-f718-4066-a8ca-58cc915261b9.PNG)

Bottom 5 (Before)
![bottom_schools_before](https://user-images.githubusercontent.com/89284280/134447806-0828f564-18b0-462c-8c0c-27e1c68c9788.PNG)


Bottom 5 (After)
![bottom_schools_after](https://user-images.githubusercontent.com/89284280/134447621-0ea68ea7-8506-4a15-ba77-ac85be914d6a.PNG)

### Question 4
**How does replacing the ninth-grade scores affect math and reading scores by grade?**\
Only change here is for Thomas High School 9th grade which now shows "Nan".

Math (Before)\
![math_scores_before](https://user-images.githubusercontent.com/89284280/134448186-92991270-2a7f-4bd5-8840-25b168b9e3df.PNG)

Math (After)\
![math_scores_after](https://user-images.githubusercontent.com/89284280/134448190-694d9ea3-5dc8-48c0-b6ca-dfa46efd642a.PNG)

Reading (Before)\
![reading_scores_before](https://user-images.githubusercontent.com/89284280/134448210-ac49db69-b74f-4ff4-bbd0-30ef045b0dec.PNG)

Reading (After)\
![reading_scores_after](https://user-images.githubusercontent.com/89284280/134448220-eff9452b-e14d-464c-aa45-142646c4052b.PNG)

### Question 5
**How does replacing the ninth-grade scores affect scores by school spending?**\
Based on the rounding rules, there is no discernable changes in scores by spending bin.\

Before\
![scores_spending_before](https://user-images.githubusercontent.com/89284280/134448715-8dce0581-780f-460d-b039-167bd3b5bcc9.PNG)

After\
![scores_spending_after](https://user-images.githubusercontent.com/89284280/134448720-1eac4280-2193-4fdd-9303-93431586a376.PNG)

### Question 6
**How does replacing the ninth-grade scores affect scores by school size?**\
Based on the rounding rules, there is no discernable changes in scores by school size.\

Before\
![scores_size_before](https://user-images.githubusercontent.com/89284280/134448982-d7e4b734-5d63-4bcd-8c87-80907b610c2f.PNG)

After\
![scores_size_after](https://user-images.githubusercontent.com/89284280/134448986-7dcd3cbb-cc94-4863-9665-f43ff43e220d.PNG)

### Question 7
**How does replacing the ninth-grade scores affect scores by school type?**\
Based on the rounding rules, there is no discernable changes in scores by school size.\

Before\
![scores_type_before](https://user-images.githubusercontent.com/89284280/134449125-6edd68b9-c658-474b-b66b-d213f6d46b16.PNG)

After\
![scores_type_after](https://user-images.githubusercontent.com/89284280/134449128-013aa2ed-95d3-4a4d-b3b0-caa55db3ab6f.PNG)

## Summary
In all, the removal of the Thomas High School (THS) 9th grade Math and Reading scores had the biggest impact on the passings rates for THS. When aggregating all the school data together, this removal of the THS 9th grade data had minimal impact on the overall analysis and no impact on the other schools.

The major changes were to THS's '% Math Passing', '% Reading Passing' and '% Overall Passing' scores.\



Python, Anaconda, Jupyter Notebook
