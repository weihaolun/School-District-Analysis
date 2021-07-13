# School District Analysis with Pandas

## I.  Overview

### Background
We have been assisting Maria, the Chief Data Scientist in City School District. We received two raw data sources for this project:
-	school_complete.csv: contains information of 15 schools. School names, type, size and budget.
-	student_cmplete.csv: contains student’s name, gender, grade, school name, reading and math score of each of the 39170 students from the district.
We aim to analyze the standard test scores (math and reading) and aggregate data to show the insight and performance trend in the school district. The result of this project will assist School Board in making decisions regarding to school budget and priorities.

Before this specific portion of the project, we have already conducted following steps to the dataset:
-	Clean up the data.
-	Merge two .csv data files into one DataFrame.
-	Created district summary DataFrame.
-	Created per school summary Dataframe with data of each school.
-	Rankings of top 5 and bottom 5 schools based on overall passing rate (rate of students passed both math and reading test).
-	Math & Reading scores by grades from 9th to 12th.
-	Score performance grouped by budget per student.
-	Score performance grouped by school size.
-	Score performance grouped by school type.


### Purpose
The School Board found out that there’s evidence of academic dishonesty in reading and math grades for Thomas High School ninth graders, specifically, the scores appear to have been altered. Therefore, for this part of the project, we are going to help Maria to replace the math and reading scores for Thomas High School ninth graders with NaNs while keeping the rest of the data intact. After conducting replacement, we will compare the data and summarize the changes. 

For this portion of the project, we will conduct the following steps to the dataset:
-	Clean up the data.
-	Replace Thomas High School ninth grader scores with NaNs.
-	Repeat the school district analysis with adjusted data.
-	Repeat per school summary with adjusted data.
-	Repeat school rankings with adjusted data.
-	Repeat Math & Reading scores by grades with adjusted data.
-	Repeat score performance grouped by budget per student with adjusted data.
-	Repeat score performance grouped by school size with adjusted data.
-	Repeat score performance grouped by school type with adjusted data.
-	Compare and analyze DataFrame before & after adjustment.

## II.  Results
### 1. How is the district summary affected?
- The result for overall District Summary is affected by removing Thomas High School ninth graders’ scores. The student count and scores are both adjusted. The number of Thomas High School ninth graders has been deducted from total student count, and their scores have been adjusted to NaNs.

- As shown in the tables below, _Average Math Score, Average Reading Score, % Passing Math, % Passing Reading and % Overall Passing_, all the metrics dropped after the adjustment. _Average Reading Score_ dropped very slightly but we can still see the change from the unformatted version.

![District Summary](https://user-images.githubusercontent.com/84211948/125428383-b6f13ded-912b-4bbf-8078-f6d82f983829.png)

- _Average Math Score_ changed from 79.0 to 78.9; _Average Reading Score_ changed from 81.87784 to 81.855796; _% Passing Math_ changed from 75.0 to 74.8; _% Passing Reading_ changed from 85.8 to 85.7; _% Overall Passing_ rate changed from 65.2 to 64.9.

### 2. How is the school summary affected?
- School summary DataFrame is a table for each school’s data. Each of the 15 schools has its own row, so that only the row for Thomas High School is affected by the adjustment. 

- Thomas High School data gets adjusted twice. The first change only adjusts _Average Math Score_ and _Average Reading Score_ to the correct values, while _% Passing Math, % Passing Reading and % Overall Passing_ all drop to 60%+ which are not correct yet.

  - Average scores gets adjusted correctly because all Thomas High School ninth graders’ scores are NaNs and the average calculation by the code below automatically skips NaNs data. Therefore, both total scores and students counts are correctly adjusted for this part of calculation.
  ```
  per_school_math = school_data_complete_df.groupby(["school_name"]).mean()["math_score"]
  per_school_reading = school_data_complete_df.groupby(["school_name"]).mean()["reading_score"]
  ```
  - % data needs further adjustment because only the number of passing students is adjusted (deducted NaNs) while the student counts is unchanged and still includes every student with label “Thomas High School”.

![School Summary1](https://user-images.githubusercontent.com/84211948/125429457-9a6bac53-4dff-4af7-9d64-3d6a3936d0a7.png)

- The second change corrects % data. We took a code block to calculate the % data separately for Thomas High School. We ensured that the total count in this calculation only includes 10th-12th graders. The final summary for Thomas High School is shown below:

![School Summary2](https://user-images.githubusercontent.com/84211948/125429478-08693343-71f7-4dc4-9c16-1f6837fac9d4.png)

### 3. How does replacing the ninth graders' math and reading scores affect Thomas High Schools's performance relative to the other schools?

### 4. How does replacing the ninth-grade scores affect the following:
- **Math and reading scores by grade**

- **Scores by school spending**

- **Scores by school size**

- **Scores by school type**


## III.  Summary
