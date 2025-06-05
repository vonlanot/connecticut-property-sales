# connecticut-property-sales

## Project Overview

This project undertakes a comprehensive analysis of property sales data from the Connecticut Office of Policy and Management (OPM). The core objective is to transform raw, heterogeneous property records into a structured and insightful dataset that can support robust exploratory data analysis, generate actionable business insights, and serve as a foundation for predictive modeling.

The analysis focuses on understanding factors influencing property sales, identifying different transaction types (e.g., standard sales, distressed properties, new constructions), and ultimately providing a clearer picture of the Connecticut real estate market. This project demonstrates proficiency in data cleaning, feature engineering, exploratory data analysis, and effective communication of results.

## Data Source

The dataset originates from the Connecticut Office of Policy and Management (OPM) and was accessed via **KaggleHub**.

**KaggleHub Download Code:**
```python
import kagglehub

# Download latest version of the dataset
path = kagglehub.dataset_download("joebeachcapital/house-prices-2001-2020")

print("Path to dataset files:", path)

The data includes information on `Sale Amount`, `Assessed Value`, `Sales Ratio`, `List Year`, `Date Recorded`, `Town`, and critical `OPM remarks` which contain unstructured text descriptions of sale conditions. Note that detailed building square footage or property construction year are not directly available in this dataset. The `Location` column (containing geographical coordinates) is also sparsely populated.

## Problem Statement / Business Questions

* How can unstructured textual `OPM remarks` be effectively categorized to differentiate various types of property sales (e.g., standard, distressed, commercial, invalid)?
* What is the distribution of different sale types within the dataset, and how do they impact key financial metrics like `Sale Amount` and `Assessed Value`?
* How do `Sales Ratio` and `Assessed Value` relate to `Sale Amount` across different property and sale types?
* Can a predictive model accurately estimate property `Sale Amount` based on available features?
* What insights can be derived to assist real estate professionals, assessors, or potential buyers/sellers in understanding the Connecticut real estate market?

## Methodology / Project Phases

### 1. Data Acquisition & Loading
* Raw property sales data was loaded into a Pandas DataFrame for initial inspection and processing.

### 2. Data Cleaning & Preprocessing
* **Initial Assessment:** Performed initial checks for data types, missing values (`df.isnull().sum()`), and understanding the distribution of key columns (`df.describe()`).
* **Handling Missing Values:** Strategically addressed missing data. For `OPM remarks`, NaN values were converted to strings and subsequently categorized as 'Standard Sale' if no other specific condition matched. Missing values in other columns (e.g., `Property Type`, `Residential Type`, `Non Use Code`, `Assessor Remarks`, `Location`) were also identified, and their implications for analysis were noted.
* **Data Type Conversion:** Ensured all columns were cast to appropriate data types. `Date Recorded` was converted to datetime objects, and numerical columns like `Assessed Value` and `Sale Amount` were confirmed as float64, facilitating accurate calculations.
* **`OPM remarks` Categorization (Feature Engineering - **Completed Phase**):**
    * **Challenge:** The `OPM remarks` column contained highly unstructured text, making direct analysis difficult. These remarks often denote non-arms-length transactions or specific property conditions crucial for accurate valuation.
    * **Solution:** Developed an iterative, regex-based categorization system using Python's Pandas and NumPy. This involved:
        * Defining a clear hierarchy of sale categories (e.g., `Invalid/Error Sale`, `Distressed/Non-Arms-Length`, `Standard Sale`, `Commercial Property`, `New Construction`, `Renovated/Updated Property`, `Specific Property Feature/Condition`, `Special Transaction Type`, `Assessment/Ratio Related`).
        * Crafting robust regular expressions (`regex`) to capture subtle keyword variations and multi-word phrases.
        * Implementing a prioritized conditional logic (`np.select`) to ensure critical, problematic sale types were accurately classified first, preventing miscategorization.
        * **Iterative Refinement:** Multiple rounds of review and refinement were conducted on the 'Other/Uncategorized' entries to enhance accuracy and reduce ambiguity, demonstrating a rigorous approach to data quality.
    * **Outcome:** A new, highly valuable categorical column, `Sale_Remarks_Category`, was created, allowing for precise filtering and analysis of different sale types. The raw text data is now structured and ready for analytical insights.

**Batch 3: Methodology (Remaining Phases) and Key Findings & Insights**
### 3. Exploratory Data Analysis (EDA)
* **[To be updated upon completion of EDA]**
* Analysis of data distributions for numerical features (`Sale Amount`, `Assessed Value`, `Sales Ratio`).
* Exploration of relationships between variables, including how `Sale_Remarks_Category` impacts financial metrics.
* Analysis of categorical distributions (e.g., `Property Type`, `Residential Type`, `Town`).
* Creation of informative visualizations (e.g., histograms, box plots, scatter plots) to communicate findings.

### 4. Feature Engineering (Advanced)
* **[To be updated upon completion of this phase]**
* Creation of time-based features (e.g., `Years Since Listing` derived from `List Year`).
* Development of location-based features (e.g., encoding `Town` categorically, or deriving aggregate statistics per town).
* Potential creation of interaction terms between existing numerical and categorical features.

### 5. Statistical Analysis / Hypothesis Testing
* **[To be updated upon completion of this phase]**
* Conducting statistical tests to validate assumptions or explore significant differences between groups. For example, comparing the mean `Sale Amount` across different `Sale_Remarks_Category` groups.
* Correlation analysis between key numerical features.

### 6. Predictive Modeling
* **[To be updated upon completion of this phase]**
* Development of machine learning models (e.g., Regression models) to predict property `Sale Amount`.
* Model selection, training, evaluation, and hyperparameter tuning using the cleaned and engineered features.

### 7. Insights & Recommendations
* **[To be updated upon completion of all analysis]**
* Summarizing key findings and providing actionable business recommendations derived from the data analysis, tailored for stakeholders in the real estate sector.

## Key Findings & Insights

* **[To be updated as insights are generated during EDA and modeling phases]**
* Example: "Initial findings from `Sale_Remarks_Category` show that 'Distressed/Non-Arms-Length' sales occur at a significantly lower average `Sale Amount` compared to 'Standard Sales', highlighting the importance of this categorization for accurate market valuation."

## Tools and Technologies Used

* **Python:** Programming language for all data analysis tasks.
* **Pandas:** Essential for data manipulation, cleaning, and analysis.
* **NumPy:** For numerical operations and efficient array computations.
* **KaggleHub:** For dataset acquisition.
* **Matplotlib / Seaborn:** (Will be added) For data visualization.
* **Scikit-learn:** (Will be added) For machine learning modeling.
* **Google Colab:** Interactive environment for development and documentation.
* **GitHub:** Version control and project hosting.

## How to Run / View the Project

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/vonlanot/connecticut-property-sales.git
    ```
2.  **Open in Google Colab:**
    * Navigate to the cloned directory.
    * Open the `Connecticut_Real_Estate_Sales.ipynb` (or similar name) notebook in Google Colab.
    * **[https://github.com/vonlanot/connecticut-property-sales/blob/main/Connecticut_Real_Estate_Sales.ipynb]**
3.  **Run Cells:** Execute the notebook cells sequentially to reproduce the analysis.

## Repository Structure

.
├── Connecticut_Real_Estate_Sales.ipynb
├── README.md
└── data/
└── # Raw data downloaded by KaggleHub code in notebook

## Acknowledgements

* Data provided by the Connecticut Office of Policy and Management (OPM), sourced via KaggleHub.

## Contact

* [Von Ellesse M. Lanot] - [https://www.linkedin.com/in/von-ellesse-lanot-21a91897/] - [vonlanot@gmail.com]
* Project Link: [https://github.com/vonlanot/connecticut-property-sales]