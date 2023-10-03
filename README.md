# Python_CDC_Project

**Introduction:**

The Python_CDC_Project is an in-depth notebook project created to analyze drug overdose death rates using Python. This project provides valuable insights for the CDC (Centers for Disease Control and Prevention) by exploring differences in overdose death rates based on different drug types and gender.

## Data Source and Software

**Installing Anaconda:**

Follow the steps in this guide to install Anaconda on your system: https://www.geeksforgeeks.org/how-to-install-conda-in-windows/

**Installing Jupyter Notebook using Anaconda:**

Refer to this guide for installing Jupyter Notebook through Anaconda: https://www.geeksforgeeks.org/how-to-install-jupyter-notebook-in-windows/

**Data Source:**

The analysis utilizes data from the CDC, which can be accessed via this link: https://data.cdc.gov/api/views/95ax-ymtc/rows.csv?accessType=DOWNLOAD

**Required Libraries:**

    import pandas as pd
    from scipy import stats
    import matplotlib.pyplot as plt
    import seaborn as sns
    %matplotlib inline
    sns.set()
    import warnings
    warnings.filterwarnings("ignore")

## Data Inspection and Cleaning

• The dataset is loaded into a Pandas DataFrame using the read_csv function.
• Missing values in the 'FLAG' column are filled with 'NO', and NaN values in the 'ESTIMATE' column are filled with 0.

## Hypothesis #1: Correlation between Drug Types

**Analysis Steps:**

• Three drug types are selected: Methadone, Heroin, and Synthetic Opioids.

• Data for each drug type is extracted and combined into a new DataFrame.

• T-tests are conducted to compare the death rates for each drug pair.

• Pearson correlation is calculated to assess the correlation between these drug types.

**Example T-Test:**

    print(stats.ttest_ind(pivoted_df['Methadone'], pivoted_df['Heroin']))

**Conclusion:**

• Result: There is no significant correlation between death rates for different drug types.

• Conclusion: Null hypothesis is supported.


3. The data is loaded into a Pandas DataFrame using the read_csv function:

       df = pd.read_csv('Drug_overdose_death_rates__by_drug_type__sex__age__race__and_Hispanic_origin__United_States.csv')

5. Data Inspection - You can check the columns of the dataset using: df.columns

6. Handling Missing Values - The FLAG column's NaN values are filled with 'NO', and the ESTIMATE column's NaN values are filled with 0:

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

CONTACT: If you have any questions or need further assistance, please feel free to contact the project maintainer at vanburen.kyle@yahoo.com.
