# Python_CDC_Project

## Created an in-depth notebook project by coding and visualizing with Python to help provide valuable insights to the CDC. 

Employing t-tests, Pearson correlation tests, and the computation of confidence intervals, I conducted analyses to assess means, correlations, and distinctions across various groups.

This Jupyter Notebook provides an analysis of drug overdose death rates based on different factors, including drug types and gender.
The analysis involves data sourced from the CDC (Centers for Disease Control and Prevention) and employs statistical tests to draw conclusions regarding drug overdose deaths.


## IMPORTANT: Data Source
This analysis uses data from the CDC, which can be accessed via the following link:
https://data.cdc.gov/api/views/95ax-ymtc/rows.csv?accessType=DOWNLOAD

1. To begin, make sure to install the necessary libraries by running the following imports: import pandas as pd
 from scipy import stats

  from scipy.stats.stats import ttest_ind
 
  import matplotlib.pyplot as plt
 
  import seaborn as sns
 
  %matplotlib inline

  sns.set()
 
  import warnings
 
   warnings.filterwarnings("ignore")

3. The data is loaded into a Pandas DataFrame using the read_csv function: df = pd.read_csv('Drug_overdose_death_rates__by_drug_type__sex__age__race__and_Hispanic_origin__United_States.csv')

4. Data Inspection - You can check the columns of the dataset using: df.columns

5. Handling Missing Values - The FLAG column's NaN values are filled with 'NO', and the ESTIMATE column's NaN values are filled with 0:
 df['FLAG'] = df['FLAG'].fillna('NO')
 df['ESTIMATE'] = df['ESTIMATE'].fillna(0)

## Hypothesis #1: Correlation between Drug Types

5. Analysis:
- Three drug types are selected: Methadone, Heroin, and Synthetic Opioids.
- Data for each drug type is extracted and combined into a new DataFrame.
- T-tests are conducted to compare the death rates for each drug pair.
- Pearson correlation is calculated to assess the correlation between these drug types
- Example t-test
print(stats.ttest_ind(pivoted_df['Methadone'], pivoted_df['Heroin']))



## Hypothesis #2: Gender and Death Rates
6. Analysis:
 - Data is separated into Male and Female datasets.
 - Independent samples t-test is performed to test if there's a significant difference in death rates between Male and Female.
 - Example t-test
  stats.ttest_ind(male_deaths_df['ESTIMATE'], female_deaths_df['ESTIMATE'])

  
## Summary of Findings
Summarize the findings for each hypothesis, including statistical results and conclusions : 
### Hypothesis #1
- Result: There is no significant correlation between death rates for different drug types.
- Conclusion: Null hypothesis is supported.

### Hypothesis #2
- Result: There is a significant difference in death rates between genders, with males having higher rates.
- Conclusion: Null hypothesis is rejected.
