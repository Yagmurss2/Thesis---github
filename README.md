# Thesis---github
Revisiting the 19th century Art World : Computational Anlaysis of Women Artists in the Levende Meesters Exhibitions.
This repository contains a pipeline for analyzing 19th-century exhibition records from an Excel dataset. The goal of this project is to extract, clean, and analyze data related to artists, artworks, and prices from these historical records, with a particular focus on understanding the representation and market value of female artists in my thesis.


Dataset
The analysis is based on an Excel file containing exhibition records from the 19th century. The dataset includes information such as artist names, artwork titles, prices, gender of the artist, exhibition details, and location.


Pipeline Overview
The pipeline consists of several steps implemented as Python scripts within a Jupyter notebook environment (like Google Colab). The main stages include:


Data Loading and Initial Cleaning: Reading the raw exhibition data from Excel files and performing initial cleaning steps such as standardizing column names, handling missing values, and converting data types.
Gender Identification and Standardization: Identifying and standardizing the gender of artists, including using external tools (like potentially the OpenAI API, as suggested by some code cells) for difficult cases and marking foreign artists.
Location Standardization: Standardizing city and place names to ensure consistency across the dataset.
Price Extraction and Cleaning: Extracting price information from the records and cleaning the data by converting it to a numeric format and handling invalid or missing price entries.
Data Enrichment (e.g., Fuzzy Matching): Using techniques like fuzzy matching to link artists across different records or datasets and potentially assign gender based on external lists.
Quantitative Analysis: Performing statistical analysis to understand the distribution of artists by gender, total counts of artworks and exhibitions, and descriptive statistics for artwork prices.
Statistical Testing: Conducting statistical tests (like the Mann-Whitney U test) to compare distributions, such as the price distributions between male and female artists.
Evaluation: Evaluating the accuracy of data extraction and cleaning steps, particularly for numerical data like prices.
Key Code Snippets and Their Purpose
Here's a breakdown of some key code sections found in the notebook:


import pandas, matplotlib.pyplot, seaborn: Standard libraries for data manipulation and visualization.
pd.read_excel(...): Loading data from Excel files.
Data Filtering and Cleaning: Various lines using .copy(), .dropna(), .str.lower(), .str.strip(), .astype(), pd.to_numeric(..., errors='coerce') to clean and prepare data.
Grouping and Aggregation: Using .groupby() and .size(), .mean() to calculate statistics like artwork counts per artist or average prices.
Merging DataFrames: Using pd.merge() to combine information from different tables.
Fuzzy Matching (fuzzywuzzy): Code utilizing process.extractOne to find approximate matches for artist names.
OpenAI API Integration: Code showing potential use of the OpenAI API (openai.OpenAI, client.chat.completions.create) for tasks like identifying Dutch locations based on text descriptions. (Note: API key management is crucial and should be handled securely).
Statistical Tests (scipy.stats.mannwhitneyu): Performing the Mann-Whitney U test to compare distributions.
Data Standardization Functions: Custom Python functions like standardize_city_name to clean specific columns.
Evaluation Metrics: Code to compare cleaned data against an original or gold standard dataset and calculate accuracy.


How to Use
Clone or Download: Obtain the notebook file and the associated Excel dataset(s).
Set up Environment: Ensure you have Python installed with the necessary libraries (pandas, matplotlib, seaborn, fuzzywuzzy, openai, scipy). Using a virtual environment is recommended. If using Colab, these libraries are mostly pre-installed, though you might need to install fuzzywuzzy and openai (pip install fuzzywuzzy python-Levenshtein openai).
Upload Data: Upload your Excel file(s) to the designated path(s) mentioned in the notebook (e.g., /content/).
API Key (if applicable): If using the OpenAI API, set up your API key securely (e.g., using Colab's Secrets Manager or environment variables) and update the notebook code accordingly. Do not hardcode API keys directly in the notebook.
Run Cells: Execute the notebook cells sequentially. Pay attention to the comments and outputs to understand each step.
Review Outputs: Examine the printed outputs, generated plots, and output Excel files to interpret the results of the analysis.
The pipeline generates various outputs, including:

Cleaned and standardized Excel files (e.g., standardized_cities.xlsx, gpt4o_checked_output.xlsx, checked_output_updated_females.xlsx, catalog_with_gender_mej_mevr.xlsx, catalog_with_gender_fuzzy.xlsx).
Statistical summaries printed to the console.
Data visualizations displayed within the notebook.
Evaluation reports (e.g., matches.xlsx, mismatches.xlsx, not_found_in_extraction.xlsx, full_comparison_results.xlsx).
