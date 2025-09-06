# Semih Aşdan - semih.asdan@gmail.com

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1YcxYUoHb0_un5Ub0v9c1L4dzyLL25J45?usp=sharing)
**[RUN ALL CODE IN COLAB]** - Execute the complete pipeline with a single "Run All" button

## Data Science Intern Case Study - Physical Medicine & Rehabilitation

### Project Overview
This repository contains my solution for the Data Science Intern Case Study focusing on a physical medicine & rehabilitation dataset. The goal was to conduct in-depth Exploratory Data Analysis (EDA) and prepare the data for potential predictive modeling around the target variable `TedaviSuresi` (Treatment Duration).

### Dataset Description
The dataset consists of 2,235 observations with 13 features related to patients in a physical medicine and rehabilitation setting:
- **HastaNo**: Anonymized patient ID
- **Yas**: Age
- **Cinsiyet**: Gender
- **KanGrubu**: Blood type
- **Uyruk**: Nationality
- **KronikHastalik**: Chronic conditions (comma-separated list)
- **Bolum**: Department/Clinic
- **Alerji**: Allergies (may be single or comma-separated)
- **Tanilar**: Diagnoses
- **TedaviAdi**: Treatment name
- **TedaviSuresi**: Treatment duration in sessions (TARGET VARIABLE)
- **UygulamaYerleri**: Application sites
- **UygulamaSuresi**: Application duration

### Tasks Completed

#### 1. Exploratory Data Analysis (EDA)
- Comprehensive exploration of the dataset using Python libraries (Pandas, Matplotlib, Seaborn)
- Identification of data types, anomalies, and missing data patterns
- Data visualization techniques including histograms, scatter plots, and heatmaps
- Analysis of relationships between variables

#### 2. Data Pre-processing
Based on EDA findings, the following data cleaning and preprocessing steps were implemented:

##### Text Data Cleaning
- Turkish text normalization handling special characters (İ→i, I→ı)
- Removal of invisible Unicode characters and garbage text
- Standardization of spacing and formatting inconsistencies
- Correction of spelling errors and typos using fuzzy string matching

##### Missing Data Handling
- Strategic use of duplicate patient records to fill missing values
- Mode-based imputation for categorical variables
- Treatment name-based imputation for application sites
- Mutual reference imputation between diagnoses and treatment names

##### Feature Engineering
- **Body Part Extraction**: Automated extraction of anatomical regions from treatment descriptions
- **Frequency Encoding**: Advanced frequency encoding for categorical variables
- **Medical Condition Scoring**: Derived health score based on chronic conditions
- **Treatment Complexity Metrics**: Count-based features for diagnoses and chronic conditions
- **Age Grouping**: Creation of age brackets for better pattern recognition
- **Body Region Classification**: Categorization of treatment areas (Upper Extremity, Lower Extremity, Trunk, etc.)

##### Data Transformation
- One-Hot Encoding for blood types and allergies
- Binary encoding for gender and department
- Standardization of numerical features using StandardScaler
- Target variable transformation from continuous to categorical (Treatment Duration Categories)

### Key Challenges Addressed
1. **Data Quality Issues**: Inconsistent text data with multiple representations of the same information
2. **Missing Values**: Significant missing data across multiple columns (Alerji: 42%, KanGrubu: 30%)
3. **Duplicate Records**: Multiple entries for same patients with slight variations
4. **Complex Text Data**: Comma-separated values in medical fields requiring special processing
5. **Turkish Language Specifics**: Proper handling of Turkish characters and linguistic features

### Technologies Used
- Python (Pandas, NumPy, Scikit-learn)
- Data Visualization (Matplotlib, Seaborn, Missingno)
- Text Processing (thefuzz, regex)
- Machine Learning (PyTorch for final model testing)

### Repository Structure
```
├── README.md                           # This file
├── TalentDocSemihAsdan.pdf             # Detailed project documentation
├── PUSULA_SEMIH_ASDAN.ipynb           # Jupyter notebook with complete analysis
├── Pusula_Semih_Asdan.py              # Python script version
├── Talent_Semih_Asdan_Final_Data.xlsx # Final processed dataset
├── X_train.xlsx                       # Training features
├── X_test.xlsx                        # Test features  
├── X_final.xlsx                       # Complete feature set
├── y_train.xlsx                       # Training targets
└── y_test.xlsx                        # Test targets
```

### How to Run
1. Click the "Open In Colab" badge at the top to access the Jupyter notebook
2. Execute the complete pipeline with a single "Run All" button
3. Alternatively, run the Python script locally with required dependencies installed

### Submission Requirements Met
- ✅ GitHub repository with code
- ✅ README.md file with project overview
- ✅ Name, surname, and email at the top of README
- ✅ Document summarizing findings (TalentDocSemihAsdan.pdf)
- ✅ Proper repository naming (Pusula_Semih_Asdan)
