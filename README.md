# DiabetesData_PowerBI
## About the Dataset  
This dataset was collected as part of a prospective observational study to evaluate the effects of type 2 diabetes mellitus (DM) on cerebral vasoregulation, perfusion and functional outcomes, measured by blood flow responses to hypocapnia and hypercapnia, Valsalva maneuver, head-up tilt, and sit-to-stand test. The dataset comprises of observations from 69 diabetic and control participants (aged 55 to 75 years) with continuous measurements of cerebral blood flow using transcranial Doppler and MRI (magnetic resonance imaging), heart rate, blood pressure, and respiratory parameters, balance, walking, laboratory and retinopathy measures at baseline, and 41 subjects who completed the two-years of follow-up. 

## My Responsibility  
I led the data modeling and data cleaning in my team(9 teammates in total) using **PowerBI Query Editor**. Categorized 150 medical records into Demographics, Medical history, Medication, Labs, Blood Presure, MRI, Opthalmology & Walking & Cognitive Tests.     
**Data modeling** improves performance, provides better organization, imporved collaboration, most importantly, it greatly increased the flexibility working in a team. We can change data source, add new tables or columns without changing the entire table. After modeling the original dataset into 11 relational tables, I focused on demographic KPI analysis, patients' medical history, medicine intake and the effects on lipid profile and cognitive decline. 
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/e0dbc041-4ec1-4017-8074-ed7a84384b1b)  

**Data Cleaning**  took about 1/4 of the workload. Simply as removing duplicates, filtering rows, merging data, transforming data types, more advanced like mapping description texts to scaled numbers, recaculating outfliers, replacing values according to column constrains, even using Power Query's functional language 'M' to pivot and transform abnormal values. 
- Example1: Mapping description texts to scaled numbers; Create new relational tables (0ne-to-Many Cardinality):   
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/ce4d6023-dc6f-4c98-9608-0a32d2047280)
- Example2: Power Query M language to add new conditional column and transform abnormal values:  
![image](https://github.com/chen8122/DiabetesData_PowerBI/assets/9794705/5f8e35ce-7ed1-4566-a540-a794a0784fba)


