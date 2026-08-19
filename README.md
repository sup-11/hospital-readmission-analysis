# 30-Day Hospital Readmission Analysis for Patients with Diabetes
SQL analysis of 30-day hospital readmissions among patients with diabetes.

## Business Problem

Hospital readmissions are costly and can place additional strain on healthcare resources. This project examines hospital encounters involving patients with diabetes to understand what factors are linked to readmission within 30 days and identify patient groups that may need additional follow-up after discharge.

## Business Question

Which patient groups should be prioritized for post-discharge follow-up to help reduce 30-day readmissions?

## Dataset Overview

This project uses the Diabetes 130-US Hospitals dataset from the UCI Machine Learning Repository. The dataset contains 101,766 hospital encounters involving patients with diabetes across 130 U.S. hospitals from 1999 to 2008.

The data includes information on patient demographics, hospital utilization, admission and discharge details, laboratory results, diagnoses, medications, and readmission status.

## Database Design & Data Preparation

The original dataset was organized into a relational database to make the analysis easier to manage and reduce repeated descriptive information.

The database was structured into the following tables:

- patient_encounters – core encounter information and readmission status
- clinical_details – diagnoses and laboratory results
- medication_details – diabetes medications and treatment information
- admission_type – admission type descriptions
- admission_source – admission source descriptions
- discharge_disposition – discharge destination descriptions

Before analysis, the data was checked for missing values, duplicate encounters, inconsistent values, and unusual records.

## Analysis Approach

The analysis began with a broad review of potential readmission factors and gradually narrowed to the factors that showed the most meaningful patterns.

The analysis focused on:

- Establishing the overall 30-day readmission rate as a baseline
- Evaluating prior healthcare utilization, including inpatient, emergency, and outpatient visits
- Examining hospitalization factors such as length of stay, admission type, admission source, discharge disposition, and       medical specialty
- Analyzing diabetes-related factors including A1C results, glucose levels, diabetes medication use, medication changes, and   insulin status
- Combining the stronger factors to identify patient groups with elevated 30-day readmission rates

## Key Findings

- The overall 30-day readmission rate was approximately **11.16%**, which was used as the baseline for comparison.

- **Prior inpatient utilization showed one of the strongest patterns.** The readmission rate increased substantially among     patients with more prior inpatient visits.

- **Prior emergency utilization also showed increasing readmission rates**, particularly among patients with frequent          emergency visits.

- **Discharge disposition helped identify higher-risk groups.** Patients discharged or transferred to rehabilitation           facilities, skilled nursing facilities (SNF), and some other care settings showed elevated readmission rates.

- **Insulin treatment status showed meaningful differences.** Encounters where insulin dosage was decreased or increased had   higher readmission rates than those with steady or no insulin treatment.

- A1C results and glucose levels did not show sufficiently consistent patterns to serve as primary indicators in the final     patient segmentation.

## High-Risk Patient Profiles

The final analysis combined prior inpatient visits, prior emergency visits, discharge disposition, and insulin status to identify patient groups with elevated 30-day readmission rates.

Key patterns included:

- Patients with **4+ prior inpatient visits** consistently appeared among the higher-readmission groups across different discharge destinations and insulin statuses.

- Among patients with **4+ prior inpatient visits who were discharged home**, 30-day readmission rates ranged from approximately **25% to 32%** across insulin treatment groups.

- Patients discharged or transferred to **rehabilitation facilities** also appeared in several higher-readmission groups.

- Insulin status provided additional differentiation, but **prior inpatient utilization showed a more consistent pattern** across the final patient segments.

These results suggest that a patient's history of hospital utilization, combined with discharge destination and treatment information, can help identify groups that may benefit from additional post-discharge follow-up.

## Business Recommendations

- Prioritize post-discharge follow-up for patients with frequent prior inpatient hospitalizations, particularly those with 4 or more prior inpatient visits.

- Consider both prior inpatient and emergency visit history when identifying patients who may need additional support after discharge.

- Provide additional attention to high-risk patients discharged to rehabilitation facilities, skilled nursing facilities, or home health care.

- Use diabetes treatment information, such as changes in insulin dosage, as an additional indicator when assessing follow-up needs.

- Consider combining these factors into a readmission-risk screening process to help care teams identify patients who may benefit from earlier follow-up.


## SQL Skills Demonstrated

- Data profiling and cleaning
- Aggregate functions: COUNT(), SUM(), MIN()
- Conditional aggregation
- CASE statements for grouping patient utilization
- INNER JOINs across normalized tables
- GROUP BY using multiple columns
- HAVING to filter grouped results
- Common Table Expressions (CTEs)
- Window functions using RANK()
- Subqueries
- Filtering and sorting using WHERE and ORDER BY
- Readmission rate calculations
