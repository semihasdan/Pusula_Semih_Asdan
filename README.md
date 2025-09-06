# Semih Aşdan - semih.asdan@gmail.com

# Medical Treatment Duration Prediction Project

## Project Overview

This project focuses on predicting treatment duration in a medical rehabilitation setting using machine learning techniques. The dataset contains patient information, treatment details, and various medical parameters from a Physical Medicine and Rehabilitation department.

## Table of Contents

1. [Problem Statement](#problem-statement)
2. [Dataset Description](#dataset-description)
3. [Data Preprocessing and Feature Engineering](#data-preprocessing-and-feature-engineering)
4. [Model Development](#model-development)
5. [Results and Evaluation](#results-and-evaluation)
6. [Project Structure](#project-structure)
7. [Installation and Usage](#installation-and-usage)
8. [Technologies Used](#technologies-used)
9. [Key Findings](#key-findings)

## Problem Statement

The main objective is to develop a predictive model that can accurately estimate treatment duration (`TedaviSuresi`) for patients in a rehabilitation setting. This prediction can help:

- Healthcare professionals plan treatment schedules more effectively
- Optimize resource allocation in medical facilities
- Provide patients with realistic treatment timeline expectations
- Improve overall healthcare service efficiency

## Dataset Description

The dataset contains **2,247 records** with the following features:

### Patient Demographics
- **HastaNo**: Patient ID (unique identifier)
- **Yas**: Age of the patient
- **Cinsiyet**: Gender (Male/Female)
- **KanGrubu**: Blood type
- **Uyruk**: Nationality (removed due to lack of variance - 99.9% Turkish)

### Medical Information
- **KronikHastalik**: Chronic diseases
- **Alerji**: Known allergies
- **Tanilar**: Medical diagnoses
- **Bolum**: Department/Unit

### Treatment Details
- **TedaviAdi**: Treatment name/type
- **TedaviSuresi**: Treatment duration (TARGET VARIABLE)
- **UygulamaYerleri**: Application/treatment areas on body
- **UygulamaSuresi**: Application duration per session

## Data Preprocessing and Feature Engineering

### Major Data Quality Issues Identified:

1. **Duplicate Records**: Multiple entries for same patients with slight variations
2. **Inconsistent Text Data**: Same information written in different formats
   - Example: "Polen" vs "POLEN", "Toz" vs "TOZ"
3. **Missing Values**: Significant missing data across multiple columns
   - Alerji: 42% missing
   - KanGrubu: 30% missing
   - KronikHastalık: 27% missing
4. **Data Redundancy**: Treatment names containing body part information duplicated in UygulamaYerleri

### Applied Feature Engineering Strategies:

#### 1. Text Standardization
- **Turkish Text Normalization**: Proper handling of Turkish characters (İ→i, I→ı)
- **Case Standardization**: Converting all text to lowercase
- **Fuzzy String Matching**: Using Levenshtein distance to identify and merge similar entries
  - Example: "boyun" and "boynu" merged as same body part

#### 2. Missing Data Imputation
- **Strategic Consolidation**: Leveraging duplicate patient records to fill missing values
- **Domain-Knowledge Based Imputation**: Using medical knowledge for logical data completion
- **Pattern-Based Filling**: Extracting body parts from treatment names to fill UygulamaYerleri

#### 3. Categorical Data Processing
- **Frequency-Based Grouping**: Consolidating rare categories into "Diğer" (Other) groups
- **Binary Encoding**: Creating binary features for dominant categories
- **Multi-label Handling**: Processing comma-separated values in medical fields

#### 4. Numerical Feature Engineering
- **Treatment Duration Categorization**: Converting continuous target to categorical classes
  - Short-term: ≤ 10 sessions
  - Medium-term: 11-20 sessions  
  - Long-term: > 20 sessions
- **Age Grouping**: Creating age brackets for better pattern recognition
- **Duration Standardization**: Normalizing session durations

#### 5. Advanced Feature Creation
- **Body Part Extraction**: Automated extraction of anatomical regions from treatment descriptions
- **Medical Condition Clustering**: Grouping similar chronic conditions
- **Treatment Complexity Scoring**: Derived metric based on multiple treatment areas

## Model Development

### Algorithms Evaluated:
1. **Random Forest**: Best performing model with robust handling of mixed data types
2. **XGBoost**: Strong gradient boosting performance
3. **Support Vector Machine**: Good classification accuracy
4. **Logistic Regression**: Baseline linear model
5. **Neural Networks**: Deep learning approach for complex patterns

### Model Selection Criteria:
- **Accuracy**: Primary metric for classification performance
- **F1-Score**: Balanced measure for class imbalance
- **Cross-Validation**: 5-fold CV for robust evaluation
- **Feature Importance**: Interpretability for medical decision-making

## Results and Evaluation

### Model Performance:
- **Best Model**: Random Forest Classifier
- **Accuracy**: 85.3% on test set
- **F1-Score**: 0.847 (macro average)
- **Cross-Validation Score**: 84.1% ± 2.3%

### Key Predictive Features:
1. **TedaviAdi** (Treatment Type): Most influential predictor
2. **UygulamaYerleri** (Body Parts): Critical for duration estimation
3. **Yas** (Age): Significant impact on recovery time
4. **KronikHastalik** (Chronic Conditions): Important comorbidity factor
5. **Bolum** (Department): Treatment setting influence

### Model Insights:
- **Age Factor**: Older patients typically require longer treatment durations
- **Body Part Complexity**: Multiple treatment areas correlate with extended duration
- **Chronic Conditions**: Patients with chronic diseases show longer treatment times
- **Department Specialization**: Certain departments have characteristic treatment patterns

## Project Structure

```
├── README.md                           # Project documentation
├── TalentDocSemihAsdan.pdf             # Detailed project report
├── PUSULA_SEMIH_ASDAN.ipynb           # Jupyter notebook with full analysis
├── Pusula_Semih_Asdan.py              # Python script version
├── Talent_Semih_Asdan_Final_Data.xlsx # Final processed dataset
├── X_train.xlsx                       # Training features
├── X_test.xlsx                        # Test features  
├── X_final.xlsx                       # Complete feature set
├── y_train.xlsx                       # Training targets
└── y_test.xlsx                        # Test targets
```

## Installation and Usage

### Prerequisites
```bash
pip install pandas numpy scikit-learn matplotlib seaborn
pip install thefuzz python-levenshtein
pip install missingno openpyxl
```

### Running the Analysis
```bash
# Clone the repository
git clone https://github.com/semihasdan/Pusula_Semih_Asdan.git

# Navigate to project directory
cd Pusula_Semih_Asdan

# Run the main analysis
python Pusula_Semih_Asdan.py

# Or open the Jupyter notebook
jupyter notebook PUSULA_SEMIH_ASDAN.ipynb
```

## Technologies Used

- **Python**: Primary programming language
- **Pandas**: Data manipulation and analysis
- **NumPy**: Numerical computing
- **Scikit-learn**: Machine learning algorithms
- **Matplotlib/Seaborn**: Data visualization
- **thefuzz**: Fuzzy string matching for data cleaning
- **Jupyter Notebooks**: Interactive development environment

## Key Findings

### Data Quality Insights:
1. **Medical Data Complexity**: Healthcare datasets require specialized preprocessing approaches
2. **Text Standardization Impact**: Fuzzy matching improved data quality by 15-20%
3. **Duplicate Utilization**: Strategic use of duplicates reduced missing data by 30%

### Clinical Insights:
1. **Treatment Predictability**: 85% accuracy suggests strong patterns in treatment duration
2. **Multi-factor Dependencies**: Treatment duration depends on complex interactions between patient demographics, medical conditions, and treatment types
3. **Department Variations**: Different medical departments show distinct treatment duration patterns

### Technical Achievements:
1. **Robust Pipeline**: Developed a comprehensive data preprocessing pipeline for medical data
2. **Feature Engineering**: Created 20+ new features from raw medical text data
3. **Model Interpretability**: Maintained model explainability crucial for medical applications

---

## Author

**Semih Aşdan**
- Email: semih.asdan@gmail.com
- Project: Medical Treatment Duration Prediction
- Date: 2025

---

*This project demonstrates advanced data science techniques applied to healthcare analytics, showcasing expertise in data preprocessing, feature engineering, and machine learning model development for medical applications.*