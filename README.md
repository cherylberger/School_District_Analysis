# **PyCity_Schools_Challenge** 
## **School District Analysis **        -             *Data Analytics Module 4 Pandas*         
#### Cheryl Berger
###  **Project Overview**
#### After identifying the potential for academic dishonesty in the 9th grade class at Thomas High School, the school board has informed V. Isualize that the recent School District Analysis must be revised to include only data that complies with the standards.  Therefore, the purpose of this PyCity Schools analysis is to repeat the distict level summary of reading and math scores as well as the more discreet school level summary of reading and math performance within the disctrict.  The students_complete.csv file will be scrubbed to remove the data for math and reading scores for all 9th grade students at Thomas high school and a new analysis will be provided containing a summary of the impact on the overall analysis with these changes. 

### **Results:** 
#### In order to complete the project, the original data needed to be cleaned to remove the math and reading scores for the 9th grade students at Thomas High School. 
         First, prepare the data for reanalysis, load the dependencies for the analysis using jupyter notebook. 
                import pandas as pd
                import numpy as np

         Next, read the School Data and Student Data and store into a Pandas DataFrame using the code steps below: 
                school_data_df = pd.read_csv(school_data_to_load)
                student_data_df = pd.read_csv(student_data_to_load)

         Then, Replace the math & reading scores for all 9th grade students at Thomas high school in the student data DataFrame using the code below. The values for each index            with be replaced with "NaN" which indicates 'not a number'. 
                  student_data_df.loc[(student_data_df["school_name"] =="Thomas High School") & (student_data_df["grade"] =="9th"), "reading_score" ]=np.nan'
                  student_data_df.loc[(student_data_df["school_name"] == "Thomas High School") & (student_data_df["grade"] == "9th"), "math_score"]=np.nan'
                  student_data_df

         Combine the data into a new merged DataFrame and display the results 
                  school_data_complete_df = pd.merge(student_data_df, school_data_df, how="left", on=["school_name", "school_name"])
                  school_data_complete_df.head()

         Finally, the new dataset contains all 39170 rows and 11 columns of data but results for reading and math scores for 9th grade at Thomas High School are listed as 'NaN'
                  ![image](https://user-images.githubusercontent.com/94234511/147896450-d1f8a109-cf19-4f2e-ba25-bde8e1068f0f.png)

#### To compare the results of the analysis, calculate the new student count, the average math and readings scores as indicated in the code below:
         First, Get the number of students that are in ninth grade at Thomas High School.
                  ninth_grade_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["grade"]                                 =="9th")].count()["grade"]
                  ninth_grade_count
         Next, get the total student count 
                  student_count = school_data_complete_df["Student ID"].count()
         Subtract the number of students that are in ninth grade at Thomas High School from the total student count to get the new total student count.
                  new_total_student_count = student_count - ninth_grade_count
                  new_total_student_count
         Calculate the passing rates using the "clean_student_data".
                  passing_math_count = school_data_complete_df[(school_data_complete_df["math_score"] >= 70)].count()["student_name"]
                  passing_math_count
                  passing_reading_count = school_data_complete_df[(school_data_complete_df["reading_score"] >= 70)].count()["student_name"]
                  passing_reading_count
         Also calculate the percentage of students passing math, reading and both
                  passing_math_percentage = passing_math_count / new_total_student_count * 100
                  passing_math_percentage
                  passing_reading_percentage = passing_reading_count / new_total_student_count * 100
                  passing_reading_percentage
                  overall_passing_percentage = overall_passing_math_reading_count / new_total_student_count * 100
                  overall_passing_percentage

#### Create a revised district summary DataFrame to display the revised analysis, note that the keys for each function match the recalculated variables as applicable.   
          district_summary_df = pd.DataFrame(
          [{"Total Schools": school_count, 
          "Total Students": new_total_student_count, 
          "Total Budget": total_budget,
          "Average Math Score": average_math_score, 
          "Average Reading Score": average_reading_score,
          "% Passing Math": passing_math_percentage,
         "% Passing Reading": passing_reading_percentage,
        "% Overall Passing": overall_passing_percentage}])

         Format the "Total Students" to have the comma for a thousands separator and Total Budget" to have the comma for a thousands separator, a decimal separator and a "$".
                  district_summary_df["Total Students"] = district_summary_df["Total Students"].map("{:,}".format)'
                  district_summary_df["Total Budget"] = district_summary_df["Total Budget"].map("${:,.2f}".format)

         Format the remaining columns as indicated by the code below:
                  district_summary_df["Average Math Score"] = district_summary_df["Average Math Score"].map("{:.1f}".format)
                  district_summary_df["Average Reading Score"] = district_summary_df["Average Reading Score"].map("{:.1f}".format)
                  district_summary_df["% Passing Math"] = district_summary_df["% Passing Math"].map("{:.1f}".format)
                  district_summary_df["% Passing Reading"] = district_summary_df["% Passing Reading"].map("{:.1f}".format)
                  district_summary_df["% Overall Passing"] = district_summary_df["% Overall Passing"].map("{:.1f}".format)
                  district_summary_df'
      
#### **How is the district summary affected?**
         The results of the revised district summary are displayed below:
          ![image](https://user-images.githubusercontent.com/94234511/147903291-f4ef285b-4c08-4950-b2f5-98e8dd87117f.png)
  ![image](https://user-images.githubusercontent.com/94234511/147903291-f4ef285b-4c08-4950-b2f5-98e8dd87117f.png)              
          The results of the original analysis http://localhost:8888/notebooks/School_district_analysis2/PyCitySchools-Copy1.ipynb can be seen below:
         ![image](https://user-images.githubusercontent.com/94234511/147903319-ddca75f8-f09b-44a2-85f4-faed390c4e04.png)
![image](https://user-images.githubusercontent.com/94234511/147903319-ddca75f8-f09b-44a2-85f4-faed390c4e04.png)
         The impact of the changes are summarized below: 
                  * The total number of schools analyzed remained constant at 15
                  * The total number of students was reduced by 461 (the number of 9th graders at Thomas High School) from 39,170 to 38,709
                  * Total Budget" The total budget was unchanged in the updated analysis at $24,649,428
                  * Average math scores decreased from 81.9 to 78.9
                  * Average reading scores increased from 78.9 to 81.9
                  * The imapct to the passing math percentage was negligible from 74.9% to 74.8%
                  * The impact to the passing reading percentage was also negligible from 85.8% to 85.7%
                  * The overall passing percentage was slightly lower in the revised analysis from 65.2% to 64.9%
      

#### The second objective is to prepare a revised school summary using the clean data. 
         First, we must generate Using the Pandas DataFrame named school_data_complete_df from the original analysis, calculate the number of 10th-12th graders from Thomas High          School (THS) using the following code:
                  tenth_grade_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["grade"]                                 =="10th")].count()["grade"]
                  eleventh_grade_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["grade"]                             =="11th")].count()["grade"]
                  twelfth_grade_count = school_data_complete_df.loc[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["grade"]                              =="12th")].count()["grade"]
                  ths_student_count = tenth_grade_count + eleventh_grade_count + twelfth_grade_count
         
         Then, Create three new variables for Thomas high school student performance
                  ths_passing_math = school_data_complete_df.loc[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["math_score"] >=70)]
                  ths_passing_reading = school_data_complete_df.loc[(school_data_complete_df["school_name"] == "Thomas High School") & (school_data_complete_df["reading_score"]                   >=70)]
                  ths_passing_math_reading = school_data_complete_df.loc[(school_data_complete_df["school_name"] == "Thomas High School") &                                                         (school_data_complete_df["math_score"] >=70) & (school_data_complete_df["reading_score"] >=70)]'
         
         Calculate the percentage of 10th-12th grade students passing math, reading and both subjects from Thomas High School. 

                  ths_passing_math_count = school_data_complete_df[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["math_score"]                         >=70)].count()["math_score"]
                  ths_passing_math_percentage = ths_passing_math_count / ths_student_count  * 100

                  ths_passing_reading_count = school_data_complete_df[(school_data_complete_df["school_name"] =="Thomas High School") & (school_data_complete_df["reading_score"]                   >=70)].count()["reading_score"]
                  ths_passing_reading_percentage = ths_passing_reading_count / ths_student_count  * 100

                  ths_passing_math_reading_count = school_data_complete_df[(school_data_complete_df["school_name"] =="Thomas High School") &                                                       (school_data_complete_df["math_score"] >=70) & (school_data_complete_df["reading_score"] >=70) ].count()["math_score"]
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
         Replacing one variable at a time, screenshots of the data for Thomas high school are shown below: 
                  ![image](https://user-images.githubusercontent.com/94234511/147899814-d7119a76-8cf7-4323-a29d-be2eeec1ea0d.png)
                  ![image](https://user-images.githubusercontent.com/94234511/147899831-ec66b578-1948-4ea5-be5d-914cbfb25afa.png)
                  ![image](https://user-images.githubusercontent.com/94234511/147899847-73ef7f92-461b-4039-ae4e-c2c8ee5670cf.png)

### **How is the school summary affected?**   
         The results of the revised school summary 
![image](https://user-images.githubusercontent.com/94234511/147979984-d3ff3667-26b9-4815-a388-c40acc20fb86.png)
                  
         can be compared ot the orignal analysis http://localhost:8888/notebooks/School_district_analysis2/PyCitySchools-Copy1.ipynb.        
![image](https://user-images.githubusercontent.com/94234511/147980565-6e3fc156-6229-41fe-938c-74eb32f7be5e.png)
       
        * No impact to school type 
        * The total number of students was reduced from 39,170 to 38,709
        * The Total School Budget was unchanged
        * The Per Student Budget was unchanged
        * Average Math Scores were reduced from 79 to 77 in the revised analysis
        * Average Reading Score were slightly lower in the revised analysis 81& compared to 81.9% originally
        * The % Passing Math was only mildly impacted, decreasing from 75 to 74.8%
        * The % Passing Reading was slighly lower in the revised analysis from 85.8% to 85.7%
        * The % Overall Passing overall was also slighly lower in the revised analysis from 65.2% to 64.9% 

### How does replacing the ninth graders’ math and reading scores affect Thomas High School’s performance relative to the other schools?
The removal of 9th grade scores reduced the performance at Thomas High School compared to other schools. 

### How does replacing the ninth-grade scores affect the following:
 **Math scores by grade**
         Math Scores by grade were higher in the revised analysis, XX.X compared to XX.X after replacing the 9th grade scores

                  The original analysis of math scores by grade
![image](https://user-images.githubusercontent.com/94234511/147907534-01858725-cece-4304-b3f0-cc327dcf167b.png)                  
                  
                  The revised analysis:
                          
 ![image](https://user-images.githubusercontent.com/94234511/147907449-c9b2e5e8-16c3-40fe-98b5-f652dc08c6c5.png)
 
         
 **Reading scores by grade**
         Reading Scores by grade were higher in the revised analysis, XX.X compared to XX.X after replacing the 9th grade scores

                  The original analysis of reading scores by grade:
                           
![image](https://user-images.githubusercontent.com/94234511/147907569-03a272fc-e0e6-44f1-b7d5-8a7ad58fbd81.png)
                  
                  The revised analysis:
                            
  ![image](https://user-images.githubusercontent.com/94234511/147907474-fd2d703e-81c6-4e8e-b58e-36ecce80c36d.png)
  
 **Scores by school spending**
  The impact of the removal of 9th grade data impacted school spending for the $630 - $644 category only.        
                  The original analysis of scores by school spending is illustrated below:
                  ![image](https://user-images.githubusercontent.com/94234511/147900878-c63683cf-3352-4c0c-b854-b6cdb02039dd.png)

                  The revised analysis 
   ![image](https://user-images.githubusercontent.com/94234511/147975718-7824eeda-ec77-45b5-b6d2-9d05affd8782.png)
   
                  * The percentage passing math was reduced from 73% to 67%
                  
                  * The percentage passing reading was reduced from 84% to 77% 
                  
                  * The percentage passing both math and reading also feel from 63% to 56%
         
  **Scores by school size**
    The revised analysis of scores by school size indicates that only medium size schools were impacted       
         
                  The original analysis of scores by school size is illustrated below: 
                         
![image](https://user-images.githubusercontent.com/94234511/147900796-b8f3ada8-1bf8-49b8-9c78-a5b3794ac8fd.png)

                  The revised analysis: 
         ![image](https://user-images.githubusercontent.com/94234511/147976881-5d1c404a-c4fd-4ada-ad78-b3259edd54fb.png)

                  * The percentage passing math was reduced from 94% to 88%
                  
                  * The percentage passing reading was reduced from 97% to 91%
                  
                  * the overall passing percentage was also reduced to 91% from 85%
                  
  **Scores by school type**
    The revised analysis of scores by school type had an impact but only for the charter schools.        
         The original analysis of scores by type is illustrated below: 
                  ![image](https://user-images.githubusercontent.com/94234511/147900734-7ae801fe-e8c3-4985-8e5a-00be3c7b05bb.png)

         The revised analysis:
 ![image](https://user-images.githubusercontent.com/94234511/147976320-ae757c3d-91d8-42aa-80ab-f2c086e81839.png)
 
                  * The percentage passing math was reduced from 94% to 90%
                  
                  * The percentage passing reading was reduced from 98% to 93%
                  
                  * the overall passing percentage was also reduced to 87% from 90%
                  
## Summary: Summarize four changes in the updated school district analysis after reading and math scores for the ninth grade at Thomas High School have been replaced with NaNs.
Removing the reading and math scores for the 9th graders at Thomas High School has the following impact on the updated school district analysis

                  1. The overall Average math scores and average reading scores decreased however, the impact to the percentage passing each class was only marginally impacted                      due to the small sample size. 
                  
                  2.  The removal of 9th grade scores reduced the performance at Thomas High School compared to other schools.
                  
                  3.  The impact of the removal of the data for the 9th graders at Thomas high school had the largest impact on the categories evaluted in the school summary                       analysis.  For each category, school type, school size and budget per student categoy, a reduction in percentages of the passing math, passing reading and                       overall passing percentages was observed in the revised analysis suggesting that the 9th graders at Thomas High School scored high on both math and reading.                    Although cheating may or may not have occurred, results were negatively impacted by 3-6% in the school type, size and budget categories where Thomas High School                   9th grade student performance data was removed. 
                
