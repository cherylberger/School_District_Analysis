# **PyCity_Schools_Challenge** 
# **School District Analysis **        -             *Data Analytics Module 4 Pandas*         
## Cheryl Berger
###  After identifying the potential for academic dishonesty in the 9th grade class at Thomas High School, the school board has informed (employer) that the recent School District Analysis must be revised to include only data that complies with the standards.  Therefore, the purpose of this PyCity Schools analysis is to repeat the distict level summary of reading and math scores as well as the more discreet school level summary of reading and math performance within the disctrict.  The students_complete.csv file will be scrubbed to remove the data for math and reading scores for all 9th grade students at Thomas high school and a new analysis will be provided containing a summary of the impact on the overall analysis with these changes. 

## Results: Using bulleted lists and images of DataFrames as support, address the following questions.
In order to prepare the data for reanalysis, load the dependencies for the analysis using jupyter notebook. 
'import pandas as pd'
'import numpy as np'

Read the School Data and Student Data and store into a Pandas DataFrame using the code steps below: 
'school_data_df = pd.read_csv(school_data_to_load)'
'student_data_df = pd.read_csv(student_data_to_load)'

Replace the math & reading scores for all 9th grade students at Thomas high school in the student data DataFrame using the code below. The values for each index with be replaced with NaN which indicates not a number. 
'student_data_df.loc[(student_data_df["school_name"] =="Thomas High School") & (student_data_df["grade"] =="9th"), "reading_score" ]=np.nan'

'student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "math_score"]=np.nan'
'student_data_df'
![image](https://user-images.githubusercontent.com/94234511/147896304-1b3cfa77-e0de-4003-b0ed-808bcd3499fb.png)
Combine the data into a new merged DataFrame and display the results 
school_data_complete_df = pd.merge(student_data_df, school_data_df, how="left", on=["school_name", "school_name"])
school_data_complete_df.head()
The new dataset contains all 39170 rows and 11 columns of data
![image](https://user-images.githubusercontent.com/94234511/147896450-d1f8a109-cf19-4f2e-ba25-bde8e1068f0f.png)

### How is the district summary affected?
      "Total Schools" 
      "Total Students"
      "Total Budget"
      "Average Math Score"
      "Average Reading Score"
      "% Passing Math"
      "% Passing Reading"
      "% Overall Passing"

### How is the school summary affected?
        "School Type"
        "Total Students"
        "Total School Budget"
        "Per Student Budget"
        "Average Math Score"
        "Average Reading Score"
        "% Passing Math": ths_passing_math_percentage,
        "% Passing Reading": ths_passing_reading_percentage,
        "% Overall Passing": ths_overall_passing_percentage})

### How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?

### How does replacing the ninth-grade scores affect the following:

  #### Math and reading scores by grade

  #### Scores by school spending

  #### Scores by school size

  ### Scores by school type

## Summary: Summarize four changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs.
