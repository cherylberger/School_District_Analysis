# **PyCity_Schools_Challenge** 
# **School District Analysis **        -             *Data Analytics Module 4 Pandas*         
## Cheryl Berger
###  After identifying the potential for academic dishonesty in the 9th grade class at Thomas High School, the school board has informed (employer) that the recent School District Analysis must be revised to include only data that complies with the standards.  Therefore, the purpose of this PyCity Schools analysis is to repeat the distict level summary of reading and math scores as well as the more discreet school level summary of reading and math performance within the disctrict.  The students_complete.csv file will be scrubbed to remove the data for math and reading scores for all 9th grade students at Thomas high school and a new analysis will be provided containing a summary of the impact on the overall analysis with these changes. 

## Results: Using bulleted lists and images of DataFrames as support, address the following questions.
### In order to prepare the data for reanalysis, load the dependencies for the analysis using jupyter notebook. 
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

##### Create a district summary DataFrame to display the revised analysis
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
      #### "Total Schools" The total number of schools analyzed remained constant at 15
      #### "Total Students" The total number of students was reduced by 461 from 39170 to 38709
      ##### "Total Budget" The total budget was unchanged in the updated analysis at $24,649,428
      #### "Average Math Score" average math scores decreaded from 81.9 to 78.9
      #### "Average Reading Score" average reading scores increased from 78.9 to 81.9
      #### "% Passing Math" the imapct to the passing math percentage was negligible from 74.9% to 74.8%
      #### "% Passing Reading" the impact to the passing reading percentage was also negligible from 85.8% to 85.7%
      #### "% Overall Passing" the overall passing percentage was slightly lower in the revised analysis from 65.2% to 64.9%
      
#### How is the school summary affected?
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
