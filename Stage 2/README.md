###Task 2.3

##Metabolic Response Analysis

## Description

This Python script performs an analysis of the metabolic response of wild-type (WT) and mutant plants to pesticide treatment. The analysis involves comparing the change in metabolic response between these two groups over time (0h, 8h, and 24h), and detecting outliers in the data based on the residuals. Scatter plots and time series plots are generated to visualize the differences and highlight any outliers detected in the data.

Requirements
Python 3.x
Pandas
NumPy
Matplotlib
Seaborn
You can install the required libraries using pip:
pip install pandas numpy matplotlib seaborn
Code Walkthrough

Data Extraction:
The script begins by extracting data from a remote URL where the dataset is hosted. The dataset is a tab-separated values (TSV) file containing information on metabolic responses to pesticide treatment.
url = "https://raw.githubusercontent.com/HackBio-Internship/2025_project_collection/refs/heads/main/Python/Dataset/Pesticide_treatment_data.txt"
data = pd.read_csv(url, sep="\t")
Data Preparation:
The relevant columns for wild-type (WT) and mutant plants are extracted for each time point: WT_DMSO_1, WT_pesticide_8h_1, WT_pesticide_24h_1 for WT and mutant_DMSO_1, mutant_8h_1, mutant_pesticide_24h_1 for mutants.
wt_dmso = data[data["Unnamed: 0"] == "WT_DMSO_1"].iloc[:, 1:].values.flatten()
wt_8h = data[data["Unnamed: 0"] == "WT_pesticide_8h_1"].iloc[:, 1:].values.flatten()
wt_24h = data[data["Unnamed: 0"] == "WT_pesticide_24h_1"].iloc[:, 1:].values.flatten()
mutant_dmso = data[data["Unnamed: 0"] == "mutant_DMSO_1"].iloc[:, 1:].values.flatten()
mutant_8h = data[data["Unnamed: 0"] == "mutant_8h_1"].iloc[:, 1:].values.flatten()
mutant_24h = data[data["Unnamed: 0"] == "mutant_pesticide_24h_1"].iloc[:, 1:].values.flatten()
Metabolic Change Calculation:
The change in metabolic response (ΔM) for both WT and mutants is calculated as the difference between 24h and DMSO (control).
delta_wt = wt_24h - wt_dmso
delta_mutant = mutant_24h - mutant_dmso
Scatter Plot Generation:
A scatter plot is generated to show the relationship between the metabolic changes (ΔM) for WT and mutant plants. A reference line y = x is added to help visually assess the difference.
sns.scatterplot(x=delta_wt, y=delta_mutant)
Residuals Calculation:
The residuals (differences) between the WT and mutant ΔM are calculated, and a threshold (0.3) is used to color the points based on whether they are within or outside the threshold.
residuals = delta_mutant - delta_wt
color = np.where(np.abs(residuals) <= cutoff, "grey", "salmon")
Outlier Detection:
The metabolites with residuals greater than the threshold are identified as outliers, and their names are printed.
outliers = metabolites[np.abs(residuals) > cutoff].tolist()
Metabolic Response Time Series Plot:
If outliers are detected, a time series plot is generated for six randomly selected outliers, showing the metabolic response over time for both WT and mutant plants. The time points are 0h, 8h, and 24h.
plt.plot(time_labels, wt_values.iloc[0], marker='o', linestyle='-', color=color, label=f"{metabolite} (WT)")
plt.plot(time_labels, mut_values.iloc[0], marker='s', linestyle='--', color=color, label=f"{metabolite} (MUT)")
Output

Scatter Plot: Visualizes the relationship between ΔM for WT and mutants.
Residuals Plot: Displays the scatter plot with colored points based on residuals, indicating which points are outliers.
Time Series Plot: Shows the metabolic response over time for six selected metabolites, comparing WT and mutant groups.
Example Output

Scatter plot showing metabolic changes (ΔM) for WT vs Mutant.
Residuals plot highlighting data points that are outliers.
Line plot showing the metabolic response over 24h for selected metabolites.
