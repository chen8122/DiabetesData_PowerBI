# DiabetesData_PowerBI  
## Overview    
My role in the project was to lead the data modeling and data cleaning efforts using Power BI Query Editor, categorizing the dataset into different categories for improved organization and collaboration.  

My analysis work primarily centered around demographic data and patients' medical history, leading to the creation of multiple interactive dashboards that effectively visualize the findings. Through these dashboards, I revealed insights on the relationships between diabetes and hypertension, changes in alcohol and tobacco use among diabetes patients, and the effects of diabetes and cognitive decline on lipid profiles. 
Driven by a desire to unravel unexpected outcomes, I delved deeper into the analysis to explore the impact of medication intake on lipid profiles and cognitive decline. I proactively leveraged additional data sources to extract medication usage information. This allowed me to extract medication usage information and reveal hidden insights that went beyond the scope of the original dataset.  

Overall, my work demonstrated a strong combination of **technical expertise in data modeling**, a dedication to **data accuracy and validity**, a talent for creating user-friendly **interactive dashboards**, and effective **problem-solving skills**.  

## About the Dataset  
This dataset was collected as part of a prospective observational study to evaluate the effects of type 2 diabetes mellitus (DM) on cerebral vasoregulation, perfusion and functional outcomes, measured by blood flow responses to hypocapnia and hypercapnia, Valsalva maneuver, head-up tilt, and sit-to-stand test. The dataset comprises of observations from 69 diabetic and control participants (aged 55 to 75 years) with continuous measurements of cerebral blood flow using transcranial Doppler and MRI (magnetic resonance imaging), heart rate, blood pressure, and respiratory parameters, balance, walking, laboratory and retinopathy measures at baseline, and 41 subjects who completed the two-years of follow-up.   

## Data modeling  
I took the approach of refering the original consolidated dataset into various sub-tables such as demographics, medical history, medication, labs, blood pressure, MRI, ophthalmology, walking, and cognitive tests. To establish relationships between these sub-tables, I created a primary key called 'id' by combining the 'patientID' and 'visit' columns. This unique identifier allowed me to establish relationships or connections between the sub-tables, making them relational tables.  
Data Modeling improved performance, organization, and collaboration within the team. It allowed for flexibility in changing data source, adding new calculations, groups, bins, columns or tables without any major setbacks. We could create derived columns, define custom groups based on specific criteria, or apply calculations that were crucial for our analysis.   
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/e0dbc041-4ec1-4017-8074-ed7a84384b1b)  

## Data Cleaning  
Data Cleaning constituted a significant portion of the workload. I employed various techniques, including removing duplicates, filtering rows, merging data, transforming data types, mapping descriptions to scaled numbers, recalculating outliers, and replacing values based on column constraints. Advanced techniques such as using Power Query's functional language "M" were also utilized to pivot and transform abnormal values.     
- Example1: Mapping description texts to scaled numbers; Create new relational tables (One-to-Many Cardinality):   
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/ce4d6023-dc6f-4c98-9608-0a32d2047280)
- Example2: Power Query M language to add new conditional column and transform abnormal values:  
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/5f8e35ce-7ed1-4566-a540-a794a0784fba)  

## Dashboard: KPI and Patient History Visulization  
**Question**: Are individuals with diabetes more likely to develop hypertension or vice versa?  
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/73b8b947-a7dd-499e-a1e4-42ad9408d77c)  
**Insights**:   
-Most patients were diagnosed with diabetes between the ages of 40 and 60:  
`DM Age = demographic[Age] - demographic[Diabetes Duration]`  
According to the [CDC](https://www.healthline.com/health/type-2-diabetes-age-of-onset#age-at-diagnosis), adults aged 45–64 receive the majority of new diabetes diagnoses in the U.S.  
-Out of 77 patients, 50 have been labeled with either DM or HTN:  
`DM||HTN Patients = IF(demographic[Group] = "DM" || demographic[HTN] = "HTN", 1, 0)`     
-56% of the patients developed hypertension after being diagnosed with diabetes:    
`DD to HTN? = IF(demographic[Diabetes Duration]- RELATED(patient_history[htn_years])>0, "Diabetes->Hypertension", IF(demographic[Diabetes Duration]- RELATED(patient_history[htn_years])<0, "Hypertension->Diabetes","Same Year"))`      
Research from the [NIH](https://pubmed.ncbi.nlm.nih.gov/29556093/) suggests that diabetes patients experience increased peripheral artery resistance caused by vascular remodeling and increased body fluid volume associated with insulin resistance.   

## Dashboard: Patient History - Alcohol and Tabacco Use   
**Question**: Do diabetes patients tend to change their alcohol and tobacco use habits?  
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/3c64daeb-e7bb-4723-a431-f7855d648ea1)  
Based on their reported previous use and current use, the patients were categorized into four groups: never stopped using, never used, started using, and stopped using.    
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/96380358-21ec-4259-86cc-4b94259db0ed)
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/e8845e17-9898-446b-9fbc-0265cc578c87)
**Insights**:  
-The majority of patients never changed their alcohol consumption habits.  
-A significant proportion of patients listened to their doctors and stopped using tobacco.  
-There are more patients in the control group who drink alcohol, while the proportion of smokers is similar between the DM and control groups.  

## Dashboard: Effects on Lipid Profile  
**Question**: Do patients' lipid profiles differ significantly between the DM and control groups? Furthermore, do they differ significantly between the mild cognitive decline group (failed <=2/10 cognitive tests) and the cognitive decline group (failed >2/10 cognitive tests)?  
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/e92c25a3-f5e4-4617-a3c1-eac23fbd0248)  
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/79a69ce1-51c9-48c5-a2c3-f80eade71dbb)  
**Doubts**: Based on research, diabetes patients tend to have higher triglyceride and LDL levels and lower HDL levels, and an abnormal lipid profile is usually associated with an increased risk of cognitive decline. Therefore, it was expected to observe higher triglycerides and LDL levels and lower HDL levels in both the DM and cognitive decline groups. However, the results displayed here did not align with the anticipated outcome.    
**Problem Solving**: To investigate the potential reasons for the unclear distinction, my team suspected that patients might be using medication to control their specific medical conditions, which could have influenced the lipid profile results. As a result, I /_loaded an additional data source/_ and extracted the medication usage information for these patients. The following two dashboards were created to reveal hidden information beyond the original dataset.    

## Dashboard: Medicine Intake
**Question**: Did medication intake mislead the lipid profile performance in diabetes patients and patients with cognitive decline?  
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/022f70f4-a2a0-4457-8b34-d2c16100ef65)  
**Insights**:
-There are four medication categories: diabetes, hypertension and heart-related, lipid, and cognitive. Most patients are taking lipid and diabetes-related medicine, and 11 of them are using insulin.   
-Almost all diabetes patients are taking medication for diabetes, nearly all hyperlipidemia patients are taking lipid medication, and all hypertension patients are taking medication for hypertension and heart-related conditions.  
-Almost half of the patients are taking medication for both diabetes and lipid control, while 65% are taking medication for hypertension and heart-related conditions.  
-Among the patients who failed the most cognitive tests (cognitive scores == 4 or 5), only one of them did not take any medication. One patient even took seven different kinds of medication. 
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/5d53e665-19dd-41f6-9a17-170516a3252a)  

## Dashboard: Medicine Effect on Lipid Profile and Cognitive Decline  
**Question**: Does medication play a negative role in cognitive decline? Should patients avoid taking lipid control medication?  
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/97d436aa-1e6d-444d-9b2e-5ae0ebfc1502)  
**Insights**:    
-Group(CognitiveScore==0): Most of them do not use any lipid control medication. Only one patient had slightly abnormal HDL levels, while the rest of the lipid profile was normal.  
-Group(CognitiveScore==5): All of them are taking lipid control medication, with one patient showing abnormal LDL levels and four patients having slightly abnormal HDL levels.    
-More than half of the patients who take lipid medication are in the cognitive decline group, while only 26% of those who do not take any medication are in the cognitive decline group.  
-86% of the patients with cognitive decline have been diagnosed with hyperlipidemia and are required to take lipid control medication.  
There are ongoing debates in academia and the industry about the effects of lipid medication on cognitive decline. Reference 1: [Effect of Combined Antihypertensive and Lipid-Lowering Therapies on Cognitive Function](https://www.hindawi.com/journals/crp/2020/1484357/) and 2: [Harvard Medical School: do Statins increase the risk of dementia?](https://www.health.harvard.edu/staying-healthy/do-statins-increase-the-risk-of-dementia). The suggestions they offer are somewhat similar to the recommendation I provide: listen to the doctor's advice and follow prescribed medication regimens.

## Conclusion: 
In conclusion, my work on this project showcased my proficiency in data modeling and my commitment to ensuring the accuracy and validity of the data through meticulous data cleaning processes. Moreover, my expertise in creating user-friendly interactive dashboards proved instrumental in visualizing complex information in a clear and intuitive manner. Additionally, my problem-solving skills came into play when confronted with unexpected results during the analysis. Instead of accepting them at face value, I proactively investigated potential reasons behind these outcomes. This led me to leverage additional data sources, allowing for a deeper exploration of the impact of medication intake on lipid profiles and cognitive decline. 
