# DataScienceProject
MSc Data Science final semester dissertation project

Information about dataset used for this project

***

# Health Risk Profiling from Wearable Sensor Data: Activity Classification and Cardiovascular Stress Detection

## Project Overview

This repository contains code and documentation for conducting Human Activity Recognition (HAR) and cardiovascular stress detection using wearable sensor data from the **PAMAP2 dataset**. The dataset includes synchronized tri-axial accelerometer, gyroscope, and heart rate signals collected from multiple body locations, enabling multimodal analysis.

The project’s core objective is to develop machine learning pipelines that classify diverse physical activities and detect stress events by interpreting heart rate deviations within activity-specific baselines. It emphasizes preprocessing, feature engineering, handling class imbalance, and comparative evaluation of classical and ensemble machine learning methods.

***

## Main Features and Methodology

- **Data Preprocessing:**  
  - Filtering out unknown or transitional activity labels.  
  - Imputing missing heart rate and sensor values using mean imputation.  
  - Applying rolling window smoothing to heart rate signals to reduce noise.  
  - Standardizing sensor and physiological features for model compatibility.

- **Feature Engineering:**  
  - Extracting raw IMU sensor axes (accelerometer, gyroscope) from wrist, chest, and ankle sensors.  
  - Incorporating smoothed heart rate values and statistical features including activity-specific HR means and standard deviations for baseline modeling.

- **Class Imbalance Handling:**  
  - Using Synthetic Minority Oversampling Technique (SMOTE) to generate synthetic samples for underrepresented activity classes to prevent classifier bias.

- **Machine Learning Models:**  
  - **Random Forest (RF):** Bagging ensemble optimizing tree count and depth for classification accuracy and generalization.  
  - **Support Vector Machine (SVM):** Linear kernel with regularization tuning, serving as a baseline.  
  - **k-Nearest Neighbour (KNN):** Distance-based classifier with hyperparameter tuning sensitive to data imbalance.  
  - **XGBoost:** Gradient boosting framework tuned for tree depth and estimators for efficient handling of nonlinearities.  
  - **Logistic Regression (LR):** Interpretable linear model, employed both for HAR baseline and stress detection binary classification.

- **Stress Detection Framework:**  
  - Construction of dynamic, activity-specific heart rate baselines from training data.  
  - Binary labeling of samples as stress events when heart rate exceeds baseline by more than two standard deviations.  
  - Classification of stress using Random Forest and Logistic Regression models, evaluated by ROC-AUC, precision, recall, and F1-score.

***

## Repository Structure

```bash
├── data/                  # Raw and preprocessed data files (not always included due to size)
├── final_code/          # Python scripts for standalone preprocessing, modeling, and results generation; Output performance reports, charts, confusion matrices, and ROC curves
├── requirements.txt       # Python dependencies for easy environment setup
├── README.md              # Project overview and documentation (this file)
└── LICENSE                # MIT license file
```

***

## Installation and Setup

1. Clone the repository:

```bash
git clone https://github.com/yourusername/har-stress-detection.git
cd har-stress-detection
```

2. Install required Python packages:

```bash
pip install -r requirements.txt
```

3. Download the PAMAP2 dataset from the official source and place it in the `/data/` directory. (Refer to the `/data/README.md` for detailed instructions.)

***

## Usage Instructions

- **Data Preprocessing:**  
  Run the preprocessing notebook or script to clean, normalize, and impute missing values in sensor and heart rate data.

- **Feature Extraction:**  
  Execute feature engineering notebooks to create input features including sensor axes, smoothed HR, and activity-specific HR baselines.

- **Model Training:**  
  Train classifiers with hyperparameter tuning using GridSearchCV. Models save performance reports and confusion matrices to `/results/`.

- **Stress Detection:**  
  Generate binary stress labels using HR baseline thresholds and train RF and LR classifiers to detect stress with activity context.

***

## Evaluation Metrics

- **Human Activity Recognition:**  
  Accuracy, Macro F1-Score, Precision, Recall, and Confusion Matrices.

- **Stress Detection:**  
  ROC-AUC curves, Precision, Recall, F1-Score, and Confusion Matrices.

***

## Key Results (Summary)

- **HAR Accuracy:** XGBoost (83.2%) and Random Forest (81.8%) outperform others; ensemble methods excel at capturing nonlinear data relationships.

- **Stress Detection:** Activity-contextual HR baselines reduce false positives significantly. Random Forest achieves ROC AUC ~0.89; Logistic Regression closely follows with ~0.86.

- **SMOTE Impact:** Essential for KNN and Logistic Regression to improve recall on minority classes; ensembles are resilient to imbalance without oversampling.

***

## References
- Reiss, A., & Stricker, D. (2012). Introducing a new benchmarked dataset for activity monitoring. *ISWC*.  
- Healey, J. A., & Picard, R. W. (2005). Detecting stress during real-world driving. *IEEE Transactions on ITS*.  
- Koenig, J. et al. (2023). Wearable heart rate variability for stress detection. *Psychophysiology*.  
- Gjoreski, M., et al. (2017). Real-time stress detection using wearables. *Sensors*.

***

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

***
