# Asthma Research Cohort Analysis

SQL solution for selecting eligible patients for an asthma research study based on clinical data.

## Project Overview

This project analyses healthcare data to identify patients suitable for an asthma research study. The analysis focuses on selecting patients who meet specific clinical criteria while ensuring appropriate geographic distribution.

## Steps

1. **Install and set up Microsoft SQL Server 2019 Express** and Microsoft SQL Server Management Studio for data and database management. This combination was chosen because:
   - SQL Server Express is free and provides sufficient capabilities for this analysis
   - Healthcare data benefits from SQL Server's robust security features
   - SSMS offers a user-friendly interface for data exploration and querying

2. **Create database and tables**
   - Created tables with the appropriate data types for each column
   - Structured tables to match the healthcare data model (patient, observation, medication, clinical_codes)
   - Added appropriate NULL handling for optional fields

3. **Import data** using one of these methods:
   - SQL Server Import Wizard
   - BULK INSERT: Alternative for handling large datasets
   - CLI 

4. **Data preparation and cleaning**:
   - Identified NULL values in key fields
   - Handled duplicate clinical codes using ROW_NUMBER() partitioning
   - Added PRIMARY KEY and FOREIGN KEY constraints
   - Created indexes to optimise query performance

5. **Part 1: Patient Distribution Analysis**:
   - Analysed patient distribution by postcode area and gender
   - Calculated percentages of male, female, undetermined and unknown patients in each area
   - Selected top 2 postcode areas based on patient count

6. **Part 2: Patient Selection**:
   - Applied inclusion criteria:
     - Current asthma diagnosis (refset 999012891000230104)
     - Prescribed specified medications
   - Applied exclusion criteria:
     - Current smoker status
     - Weight below 40kg
     - COPD diagnosis
     - Research opt-outs
   - Generated final patient list with full demographic information

## Key Findings

- LS99 and S72 are the postcode areas with highest patient counts
- Many patients have asthma diagnoses (398 records)
- Large number of patients (982) are smokers so were excluded
- Patient inclusion

## Technical Approach

- Used Common Table Expressions (CTEs) for readable queries
- Created foreign keys to maintain referential integrity
- Employed data cleaning techniques to handle NULL values and duplicates

## Future Improvements

- Fix data relationship between the medication_clean table and the other tables to be able to  return results related to the medication table
- Create indexes to improve query performance to assist with scalability