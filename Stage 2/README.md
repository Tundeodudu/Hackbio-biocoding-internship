### Task 2.3

## Metabolic Response Analysis

## Description

This Python script performs an analysis of the metabolic response of wild-type (WT) and mutant plants to pesticide treatment. The analysis involves comparing the change in metabolic response between these two groups over time (0h, 8h, and 24h), and detecting outliers in the data based on the residuals. Scatter plots and time series plots are generated to visualize the differences and highlight any outliers detected in the data.

## Requirements
Python 3.x
Pandas
NumPy
Matplotlib
Seaborn

## Data Extraction:
The script begins by extracting data from a remote URL where the dataset is hosted. The dataset is a tab-separated values (TSV) file containing information on metabolic responses to pesticide treatment.

## Data Preparation:
The relevant columns for wild-type (WT) and mutant plants are extracted for each time point: WT_DMSO_1, WT_pesticide_8h_1, WT_pesticide_24h_1 for WT and mutant_DMSO_1, mutant_8h_1, mutant_pesticide_24h_1 for mutants.

## Metabolic Change Calculation:
The change in metabolic response (ΔM) for both WT and mutants is calculated as the difference between 24h and DMSO (control).

## Scatter Plot Generation:
A scatter plot is generated to show the relationship between the metabolic changes (ΔM) for WT and mutant plants. A reference line y = x is added to help visually assess the difference.

## Residuals Calculation:
The residuals (differences) between the WT and mutant ΔM are calculated, and a threshold (0.3) is used to color the points based on whether they are within or outside the threshold.

## Outlier Detection:
The metabolites with residuals greater than the threshold are identified as outliers, and their names are printed.

## Metabolic Response Time Series Plot:
If outliers are detected, a time series plot is generated for six randomly selected outliers, showing the metabolic response over time for both WT and mutant plants. The time points are 0h, 8h, and 24h.

## Output
Scatter Plot: Visualizes the relationship between ΔM for WT and mutants.
Residuals Plot: Displays the scatter plot with colored points based on residuals, indicating which points are outliers.
Time Series Plot: Shows the metabolic response over time for six selected metabolites, comparing WT and mutant groups.

## Example Output
Scatter plot showing metabolic changes (ΔM) for WT vs Mutant.
Residuals plot highlighting data points that are outliers.
Line plot showing the metabolic response over 24h for selected metabolites.




### Task 2.1

# Growth Curve Analysis

## Overview
This project analyzes bacterial growth curves using time-series optical density (OD600) data. The script processes raw data, generates growth curves, calculates key metrics, and performs statistical analysis to determine the effect of mutations on bacterial growth.

## Dataset
The dataset is imported from an online source:
```
https://raw.githubusercontent.com/HackBio-Internship/2025_project_collection/refs/heads/main/Python/Dataset/mcgc.tsv
```
It contains time-series OD600 measurements for different bacterial strains under wild-type (WT) and mutant (MUT) conditions.

## Features
- Reads and processes OD600 growth data.
- Converts time-series data for easy analysis.
- Processes metadata to link sample IDs with experimental conditions.
- Generates growth curves using Matplotlib.
- Computes the time required to reach 80% carrying capacity.
- Visualizes results using scatter and box plots.
- Performs statistical analysis (Mann-Whitney U test) to compare WT and MUT growth rates.

## Dependencies
Ensure you have the following Python libraries installed:
```sh
pip install pandas numpy matplotlib seaborn scipy
```

## Usage
Run the script to execute the full analysis:
```sh
python script.py
```

## Output
- Growth curve plots for WT and MUT strains.
- Scatter plot comparing time to 80% carrying capacity.
- Box plot illustrating differences in growth rates.
- Statistical results:
  - Mann-Whitney U test to check for significant differences.
  - Mean growth times for WT and MUT strains.

### Example Output:
```
W statistic: 171.50
P-value: 0.775
WT Mean Time: 663.33 min
MUT Mean Time: 644.17 min
```
From this, we conclude that knockout manipulation did not significantly impact bacterial growth.



### Task 2.4
# SIFT and FoldX Mutation Analysis

## Overview
This project analyzes protein mutations using SIFT and FoldX scores. It identifies high-impact mutations and investigates the amino acids most affected by mutations.

## Dataset
The script retrieves data from the following sources:
- **SIFT dataset:** [sift.tsv](https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/R/datasets/sift.tsv)
- **FoldX dataset:** [foldX.tsv](https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/R/datasets/foldX.tsv)

## Features
- Reads and merges SIFT and FoldX datasets based on protein and amino acid identifiers.
- Identifies deleterious mutations (SIFT score < 0.05 and FoldX score > 2).
- Extracts and analyzes the frequency of mutated amino acids.
- Visualizes findings with bar and pie charts.

## Dependencies
Ensure the following Python libraries are installed:
```sh
pip install pandas requests matplotlib seaborn
```

## Usage
Run the script to execute the full analysis:
```sh
python script.py
```

## Output
- **Bar plot:** Frequency of original amino acids undergoing mutations.
- **Pie chart:** Proportion of amino acids affected by mutations.
- **Key findings:**
  - Alanine (A) is the most frequently mutated residue, making up 15.7% of high-impact mutations.
  - Valine (V) follows with 8.3% of mutations.
  - Cysteine (C) and Tryptophan (W) mutations are rare due to structural and evolutionary constraints.



### Task 2.7

# NHANES Data Analysis

## Overview
This project analyzes the NHANES dataset to explore health-related variables such as BMI, weight, income, and physical activity. The analysis includes data cleaning, visualization, and statistical tests.

## Dataset
The dataset is retrieved from:
- **NHANES dataset:** [nhanes.csv](https://raw.githubusercontent.com/HackBio-Internship/public_datasets/main/R/nhanes.csv)

## Features
- Cleans missing data by replacing NaN values with appropriate defaults.
- Generates histograms for BMI, weight, age, and other key variables.
- Creates scatter plots to visualize relationships between weight, height, diabetes, and smoking status.
- Conducts t-tests to compare distributions across different demographic groups.

## Dependencies
Ensure the following Python libraries are installed:
```sh
pip install pandas matplotlib seaborn numpy scipy
```

## Usage
Run the script to perform the analysis:
```sh
python script.py
```

## Output
- **Histograms:** Display distributions of BMI, weight, and age.
- **Scatter Plots:** Visualize weight vs height by gender, diabetic status, and smoking status.
- **Statistical Tests:** T-tests comparing age, alcohol consumption, and BMI across different groups.

## Key Findings
- Summary statistics of pulse rate, blood pressure, and income variations.
- Differences in weight and BMI across genders and diabetic status.
- Relationship status and alcohol consumption patterns analyzed using t-tests.

## Author
This project was developed as part of the HackBio Internship public dataset analysis.
