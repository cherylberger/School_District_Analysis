# **PyCity_Schools_Challenge** 
# **School District Analysis **        -             *Data Analytics Module 4 Pandas*         
## Cheryl Berger
###  After identifying the potential for academic dishonesty in the 9th grade class at Thomas High School, the school board has informed (employer) that the recent School District Analysis must be revised to include only data that complies with the standards.  Therefore, the purpose of this PyCity Schools analysis is to repeat the distict level summary of reading and math scores as well as the more discreet school level summary of reading and math performance within the disctrict.  The students_complete.csv file will be scrubbed to remove the data for math and reading scores for all 9th grade students at Thomas high school and a new analysis will be provided containing a summary of the impact on the overall analysis with these changes. 

## Results: 
### In order to complete the project, the original data needed to be cleaned to remove the math and reading scores for the 9th grade students at Thomas High School. In order to prepare the data for reanalysis, load the dependencies for the analysis using jupyter notebook. 
####        'import pandas as pd'
####        'import numpy as np'

### Read the School Data and Student Data and store into a Pandas DataFrame using the code steps below: 
####        'school_data_df = pd.read_csv(school_data_to_load)'
####        'student_data_df = pd.read_csv(student_data_to_load)'

### Replace the math & reading scores for all 9th grade students at Thomas high school in the student data DataFrame using the code below. The values for each index with be replaced with NaN which indicates not a number. 
####        'student_data_df.loc[(student_data_df["school_name"] =="Thomas High School") & (student_data_df["grade"] =="9th"), "reading_score" ]=np.nan'
####        'student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "math_score"]=np.nan'
####        'student_data_df'

### Combine the data into a new merged DataFrame and display the results 
####        'school_data_complete_df = pd.merge(student_data_df, school_data_df, how="left", on=["school_name", "school_name"])'
####        'school_data_complete_df.head()'
### The new dataset contains all 39170 rows and 11 columns of data
####        ![image](https://user-images.githubusercontent.com/94234511/147896450-d1f8a109-cf19-4f2e-ba25-bde8e1068f0f.png)

### Create a district summary DataFrame to display the revised analysis
#### 'district_summary_df = pd.DataFrame(
          [{"Total Schools": school_count, 
          "Total Students": student_count, 
          "Total Budget": total_budget,
          "Average Math Score": average_math_score, 
          "Average Reading Score": average_reading_score,
          "% Passing Math": passing_math_percentage,
         "% Passing Reading": passing_reading_percentage,
        "% Overall Passing": overall_passing_percentage}])'

#### Format the "Total Students" to have the comma for a thousands separator.
#### 'district_summary_df["Total Students"] = district_summary_df["Total Students"].map("{:,}".format)'

#### Format the "Total Budget" to have the comma for a thousands separator, a decimal separator and a "$".
#### 'district_summary_df["Total Budget"] = district_summary_df["Total Budget"].map("${:,.2f}".format)

#### Format the columns as indicated by the code below:
#### 'district_summary_df["Average Math Score"] = district_summary_df["Average Math Score"].map("{:.1f}".format)
      district_summary_df["Average Reading Score"] = district_summary_df["Average Reading Score"].map("{:.1f}".format)
      district_summary_df["% Passing Math"] = district_summary_df["% Passing Math"].map("{:.1f}".format)
      district_summary_df["% Passing Reading"] = district_summary_df["% Passing Reading"].map("{:.1f}".format)
      district_summary_df["% Overall Passing"] = district_summary_df["% Overall Passing"].map("{:.1f}".format)
      district_summary_df'
      
### How is the district summary affected?
#### The results of the revised district summary are displayed below: 
![image](https://user-images.githubusercontent.com/94234511/147898494-51b7b31a-640d-49c1-a3fd-03f911d4e138.png)

#### When compared to the original analysis http://localhost:8888/notebooks/School_district_analysis2/PyCitySchools-Copy1.ipynb. 
![image](https://user-images.githubusercontent.com/94234511/147899995-e5a421d5-307a-4c14-9b39-3b74c00bc513.png)

# Assign district summary df the new column order.
district_summary_df = district_summary_df[new_column_order]
district_summary_df
The impact of the changes are summarized below: 
      #### "Total Schools" The total number of schools analyzed remained constant at 15
      #### "Total Students" The total number of students was reduced by 461 (the number of 9th graders at Thomas High School) from 39,170 to 38,709
      ##### "Total Budget" The total budget was unchanged in the updated analysis at $24,649,428
      #### "Average Math Score" average math scores decreased from 81.9 to 78.9
      #### "Average Reading Score" average reading scores increased from 78.9 to 81.9
      #### "% Passing Math" the imapct to the passing math percentage was negligible from 74.9% to 74.8%
      #### "% Passing Reading" the impact to the passing reading percentage was also negligible from 85.8% to 85.7%
      #### "% Overall Passing" the overall passing percentage was slightly lower in the revised analysis from 65.2% to 64.9%
      
#### How is the school summary affected?

#### Using the Pandas DataFrame named school_data_complete_df from the original analysis, ![image](https://user-images.githubusercontent.com/94234511/147898895-3ee10eed-eaab-#### 40ed-a2e9-42a8a24fdef4.png) calculate the number of 10th-12th graders from Thomas High School (THS) using the following code:
####      'tenth_grade_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["grade"] =="10th")].count()["grade"]'
####      'tenth_grade_count'
####      'eleventh_grade_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["grade"] =="11th")].count()["grade"]'
####      eleventh_grade_count
####      twelfth_grade_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["grade"] =="12th")].count()["grade"]'
####      twelfth_grade_count
####      ths_student_count = tenth_grade_count + eleventh_grade_count + twelfth_grade_count
####      ths_student_count
ths_passing_math = school_data_complete_df.loc[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["math_score"] >=70)]

ths_passing_reading = school_data_complete_df.loc[(school_data_complete_df["school_name"] == "Thomas High School") & (school_data_complete_df["reading_score"] >=70)]

ths_passing_math_reading = school_data_complete_df.loc[(school_data_complete_df["school_name"] == "Thomas High School") & (school_data_complete_df["math_score"] >=70) & (school_data_complete_df["reading_score"] >=70)]
# Step 9. Calculate the percentage of 10th-12th grade students passing math from Thomas High School. 

ths_passing_math_count = school_data_complete_df[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["math_score"] >=70)].count()["math_score"]
ths_passing_math_percentage = ths_passing_math_count / ths_student_count  * 100

ths_passing_reading_count = school_data_complete_df[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["reading_score"] >=70)].count()["reading_score"]

ths_passing_reading_percentage = ths_passing_reading_count / ths_student_count  * 100

ths_passing_math_reading_count = school_data_complete_df[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["math_score"] >=70) & (school_data_complete_df["reading_score"] >=70) ].count()["math_score"]
ths_passing_math_reading_count

ths_passing_overall_percentage = ths_passing_math_reading_count / ths_student_count  * 100
ths_passing_overall_percentage

Replace the passing math, reading and overaall percent for Thomas High School in the per_school_summary_df to compare to the original results. 
per_school_summary_df = pd.DataFrame({
             "School Type": per_school_types,
             "Total Students": per_school_counts,
             "Total School Budget": per_school_budget,
             "Per Student Budget": per_school_capita,
             "Average Math Score": per_school_math,
           "Average Reading Score": per_school_reading,
           "% Passing Math": ths_passing_math_percentage,
           "% Passing Reading": ths_passing_reading_percentage,
           "% Overall Passing": ths_passing_overall_percentage})
per_school_summary_df
snips of the data for Thomas high school are shown below: 
![image](https://user-images.githubusercontent.com/94234511/147899814-d7119a76-8cf7-4323-a29d-be2eeec1ea0d.png)
![image](https://user-images.githubusercontent.com/94234511/147899831-ec66b578-1948-4ea5-be5d-914cbfb25afa.png)
![image](https://user-images.githubusercontent.com/94234511/147899847-73ef7f92-461b-4039-ae4e-c2c8ee5670cf.png)

#### The results of the revised school summary can be compared ot the orignal analysis http://localhost:8888/notebooks/School_district_analysis2/PyCitySchools-Copy1.ipynb.
![image](https://user-images.githubusercontent.com/94234511/147899894-80d44308-9e23-4686-b876-0b1e75ac7b59.png)

#### The impact of the changes are summarized below:       
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
The original analysis of scores by school spending is illustrated below:
![image](https://user-images.githubusercontent.com/94234511/147900878-c63683cf-3352-4c0c-b854-b6cdb02039dd.png)
The revised analysis ![image](https://user-images.githubusercontent.com/94234511/147900854-c78d17df-e44c-40d6-862b-3335b35ae308.png)

  #### Scores by school size
The original analysis of scores by school size is illustrated below: 
![image](https://user-images.githubusercontent.com/94234511/147900796-b8f3ada8-1bf8-49b8-9c78-a5b3794ac8fd.png)
The revised analysis ![image](https://user-images.githubusercontent.com/94234511/147900816-147e262c-d4f6-42df-b3e8-d225da4d8d64.png)

  ### Scores by school type
The original analysis of scores by type is illustrated below: 
![image](https://user-images.githubusercontent.com/94234511/147900734-7ae801fe-e8c3-4985-8e5a-00be3c7b05bb.png)
The revised analysis ![image](https://user-images.githubusercontent.com/94234511/147900757-f63c1931-792d-4834-a72f-f78f1c134d89.png)


## Summary: Summarize four changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs.
