# DiabetesData_PowerBI
## About the Dataset  
This dataset was collected as part of a prospective observational study to evaluate the effects of type 2 diabetes mellitus (DM) on cerebral vasoregulation, perfusion and functional outcomes, measured by blood flow responses to hypocapnia and hypercapnia, Valsalva maneuver, head-up tilt, and sit-to-stand test. The dataset comprises of observations from 69 diabetic and control participants (aged 55 to 75 years) with continuous measurements of cerebral blood flow using transcranial Doppler and MRI (magnetic resonance imaging), heart rate, blood pressure, and respiratory parameters, balance, walking, laboratory and retinopathy measures at baseline, and 41 subjects who completed the two-years of follow-up. 

## My Responsibility  
I led the data modeling and data cleaning in my team(9 teammates in total) using **PowerBI Query Editor**. Categorized 150 medical records into Demographics, Medical history, Medication, Labs, Blood Presure, MRI, Opthalmology & Walking & Cognitive Tests.     
**Data modeling** improves performance, provides better organization, imporved collaboration, most importantly, it greatly increased the flexibility working in a team. We can change data source, add new tables or columns without changing the entire table. After modeling the original dataset into 11 relational tables, I focused on demographic KPI analysis, patients' medical history, medicine intake and the effects on lipid profile and cognitive decline. 
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/e0dbc041-4ec1-4017-8074-ed7a84384b1b)  

**Data Cleaning**  took about 1/4 of the workload. Simply as _removing_ duplicates, _filtering_ rows, _merging_ data, _transforming_ data types, more advanced like _mapping_ description texts to scaled numbers, _recaculating_ outfliers, _replacing_ values according to column constrains, even using _Power Query's functional language_ 'M' to pivot and transform abnormal values. 
- Example1: Mapping description texts to scaled numbers; Create new relational tables (One-to-Many Cardinality):   
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/ce4d6023-dc6f-4c98-9608-0a32d2047280)
- Example2: Power Query M language to add new conditional column and transform abnormal values:  
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/5f8e35ce-7ed1-4566-a540-a794a0784fba)
**KPI and Patient History Visulization**
Question: individuals with diabetes are more likely to develop hypertension or the opposite?
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/73b8b947-a7dd-499e-a1e4-42ad9408d77c)  
Insights: 
-Most patients started diagnosised diabetes around the age of 40 to 60: `DM Age = demographic[Age] - demographic[Diabetes Duration]`.  
[CDC](https://www.healthline.com/health/type-2-diabetes-age-of-onset): Adults aged 45–64 receive the majority of new diabetes diagnoses in U.S.
-There are 50 patients among 77 who labeled either DM or HTN: `DM||HTN Patients = IF(demographic[Group] = "DM" || demographic[HTN] = "HTN", 1, 0)`.  
-56% developed hypertension after diagnosed diabetes: 'DD to HTN? = IF(demographic[Diabetes Duration]- RELATED(patient_history[htn_years])>0, "Diabetes->Hypertension", IF(demographic[Diabetes Duration]- RELATED(patient_history[htn_years])<0, "Hypertension->Diabetes","Same Year"))'  
[NIH](https://pubmed.ncbi.nlm.nih.gov/29556093/): Diabetes patients experience increased peripheral artery resistance caused by vascular remodeling and increased body fluid volume associated with insulin resistance
**Patient History: Alcohol and Tabacco Use**
Question: Will diabetes patients tend to change their Alcohol and Tabacco use habit?
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/3c64daeb-e7bb-4723-a431-f7855d648ea1)  
Based on their reported previous use and current use, I categorized them into four groups: never stop using, never use, start using and stop using.
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/96380358-21ec-4259-86cc-4b94259db0ed)
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/e8845e17-9898-446b-9fbc-0265cc578c87)
Insights:
-Majority patients never changed their alcohol habit.
-Remarkable propotion of patients who listened to their doctor and stop using tobacco.
-More patients in control group who drinking. While the propotion of smoking are quite similiar in DM and control gourps.  
**Effects on Lipid Profile**
**Question**: Are patients' lipid profile differ much in DM and control group? Further more, do they differ much in mild cognitive declined group(failed <=2/10 cognitive tests) and cognitive declined group(failed >2/10 cognitive tests)?!  
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/e92c25a3-f5e4-4617-a3c1-eac23fbd0248)
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/79a69ce1-51c9-48c5-a2c3-f80eade71dbb)  
**Doubts**: Based on the research, diabetes patients tend to have higher triglycerides and LDL level and lower HDL. And abonormal lipid profile usually associate with an increased risk of cognitive decline. Higher Triglycerides and LDL, lower HDL are expected in DM and cognitive declined group. However, the results displayed here did not align with my anticipated outcome. 
**Problem Solving**: My team suspected, maybe patients were using medicine to control their particular medical condition. That's why the distingtion was not clear. So I loaded \_additional data source\_ and extracted these patients' medication usage information. The following two dashboards are done to reveal the hidden information beyond the origional dataset.  
**Medicine Intake**  
There are four categories: diabetes, hypertension and heart related, lipid, and cognitive. Most patients are taking lipid and diabetes related medicine. 11 of them are using insulin. 
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/022f70f4-a2a0-4457-8b34-d2c16100ef65)
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/97d436aa-1e6d-444d-9b2e-5ae0ebfc1502)


