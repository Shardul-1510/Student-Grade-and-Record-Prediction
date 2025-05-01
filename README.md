# Student Grade Analysis and Prediction

## Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Model Implementation](#model-implementation)
- [GUI](#gui)
- [Results](#results)
- [Directory Structure](#directory-structure)
- [Contributing](#contributing)

## Project Overview
This repository contains the implementation of a Machine Learning (ML) project focused on predicting student academic performance using a dataset of 1,500 student records. The system leverages classification algorithms to identify at-risk students and provide actionable insights for educators. The project employs Random Forest, XGBoost, and a Meta-Model (ensemble of Random Forest and XGBoost) to achieve high prediction accuracy, with the Meta-Model reaching 91% accuracy.

The project aims to:
- Analyze key factors affecting student performance (e.g., attendance, continuous assessment scores).
- Implement and compare multiple ML models for accurate grade prediction.
- Provide interpretable insights to support early interventions and personalized learning strategies.

## Features
- **Data Preprocessing**: Handles missing values, feature scaling, and encoding categorical variables.
- **Exploratory Data Analysis (EDA)**: Visualizes trends like attendance-grade correlations using bar charts, scatter plots, and heatmaps.
- **Machine Learning Models**:
  - Random Forest: Robust ensemble method with 88% accuracy.
  - XGBoost: Advanced gradient boosting with 90% accuracy.
  - Meta-Model: Combines Random Forest and XGBoost for 91% accuracy.
- **Feature Importance Analysis**: Identifies critical predictors (e.g., attendance, CCA scores).
- **Performance Evaluation**: Uses accuracy, precision, recall, and F1-score for model comparison.
- **Actionable Insights**: Translates predictions into practical recommendations for educators.

## Dataset
The dataset consists of 1,500 student records with 15 features related to academic performance. Key attributes include:

| Feature Name                          | Description                                      | Data Type         |
|---------------------------------------|--------------------------------------------------|-------------------|
| Score                                 | Total score obtained by the student              | Numerical (Float) |
| Attended the Components (CCA, LCA)    | Attendance in course assessments                 | Categorical       |
| cca_1_10_marks                        | Marks in CCA assessment 1 (out of 10)            | Numerical         |
| cca_2_5_marks                         | Marks in CCA assessment 2 (out of 5)             | Numerical         |
| cca_3_mid_term_15_marks               | Mid-term CCA marks (out of 15)                   | Numerical         |
| Overall Score                         | Final performance score                          | Numerical (Float) |
| avg_cca                               | Average score across CCA components              | Numerical (Float) |
| avg_lca                               | Average score across LCA components              | Numerical (Float) |

### Preprocessing Steps
- **Missing Values**: No missing values in the dataset.
- **Encoding**: Categorical variables (e.g., attendance) encoded as binary (1 = Present, 0 = Absent).
- **Scaling**: Numerical features normalized using Min-Max Scaling.
- **Class Balancing**: Synthetic Minority Over-sampling Technique (SMOTE) applied if needed.

## Installation
To set up the project locally, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/student-grade-prediction.git
   cd student-grade-prediction
   ```

2. **Install Dependencies**:
   Ensure Python 3.8+ is installed. Install required packages using:
   ```bash
   pip install -r requirements.txt
   ```

3. **Requirements**:
   The `requirements.txt` includes:
   ```
   pandas
   numpy
   scikit-learn
   xgboost
   matplotlib
   seaborn
   imbalanced-learn
   ```

4. **Dataset**:
   Place the dataset (`cleaned_student_data.csv`) in the `data/` directory. (Note: The dataset is not included in this repository due to privacy concerns.)

## Usage
1. **Prepare the Dataset**:
   Ensure the dataset is in CSV format and placed in `data/`.

2. **Run the Pipeline**:
   Execute the main script to preprocess data, train models, and generate predictions:
   ```bash
   python app.py
   ```

3. **Visualize Results**:
   Graphs and visualizations (e.g., correlation heatmaps, feature importance plots) are saved in `eda_plots/`.

4. **View Insights**:
   Model performance metrics and feature importance rankings are printed to the console and saved in `model_results/`.

## Model Implementation
The project implements three ML models:

1. **Random Forest**:
   - Uses bootstrap sampling and random feature selection.
   - Configured with 100 trees to reduce overfitting.
   - Evaluated using Gini importance for feature ranking.

2. **XGBoost**:
   - Employs gradient boosting with L1/L2 regularization.
   - Optimized via Grid Search for hyperparameters (e.g., learning rate, max depth).
   - Uses SHAP values for interpretability.

3. **Meta-Model**:
   - Combines predictions from Random Forest and XGBoost using Logistic Regression as the meta-learner.
   - Achieves the highest accuracy (91%) through ensemble learning.

### Training Process
- **Data Split**: 80% training (1,200 records), 20% testing (300 records).
- **Evaluation Metrics**:
  - Accuracy
  - Precision
  - Recall
  - F1-Score

### Performance Comparison
| Model         | Accuracy | Precision | Recall | F1-Score |
|---------------|----------|-----------|--------|----------|
| Random Forest | 88%      | 85%       | 86%    | 85%      |
| XGBoost       | 90%      | 88%       | 87%    | 88%      |
| Meta-Model    | 91%      | 89%       | 90%    | 89%      |


## GUI
![Screenshot 2025-05-01 180026](https://github.com/user-attachments/assets/af999118-f47a-4e13-9ada-a4a52805fb41)
![Teacher Dashboard](https://github.com/user-attachments/assets/77ecc3ad-31bd-4748-b0a9-f92fa3b3178c)
![Student Dashboard](https://github.com/user-attachments/assets/798ac7f7-a282-46a6-8c7d-727dc4d6c1d6)
![Screenshot 2025-05-01 174728](https://github.com/user-attachments/assets/10d68556-f998-4a26-a194-f3f30053afea)
![Screenshot 2025-05-01 174737](https://github.com/user-attachments/assets/f9645287-8e4c-4e9f-93d5-fd028b798226)
![Screenshot 2025-05-01 174651](https://github.com/user-attachments/assets/3abcfe2e-157f-4e63-a2ed-a1af221bc22b)
![Screenshot 2025-05-01 174657](https://github.com/user-attachments/assets/6108c677-5f2e-45e9-be71-dd5bc4a61f44)

## Results

- **Key Findings**:
  - Attendance is the most significant predictor (32% contribution).
  - CCA scores and final exam performance are critical drivers.
  - The Meta-Model outperforms individual models, reducing bias and variance.
- **Practical Implications**:
  - Early identification of at-risk students (e.g., low attendance → 72% failure rate).
  - Recommendations for interventions (e.g., tutoring for students with CCA scores <7.5).
- **Visualizations**:
  - Correlation heatmaps highlight feature relationships.
  - Bar charts show grade distributions by attendance.
  - Feature importance plots identify key predictors.

## Directory Structure
```
student-grade-and-record-prediction/
├── data/
│   └── cleaned_student_data.csv   # Dataset (not included)
│   └── final_student_data.csv     # Processed dataset (not included)
├── eda_plots/                     # Visualizations (e.g., heatmaps, scatter plots)
├── model_results/                 # Model performance metrics
├── models/                        # Trained model files
├── app.py                         # Main script for pipeline
├── model_training.py              # Model training and evaluation
├── preprocess.py                  # Data preprocessing functions
├── visualization.py               # EDA and result visualizations
├── package-lock.json              # Node.js dependency lock file
├── package.json                   # Node.js dependencies
└── README.md                      # Project documentation
```

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/new-feature`).
3. Commit changes (`git commit -m "Add new feature"`).
4. Push to the branch (`git push origin feature/new-feature`).
5. Open a Pull Request.

Please ensure code follows PEP 8 standards and includes relevant tests.
