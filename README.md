# Building Heat Efficiency Analysis

A comprehensive machine learning project analyzing the relationship between building features and heating load using the UCI Energy Efficiency dataset.

## Project Overview

This project analyzes 768 buildings with identical internal volume (771.75 m³) but varying geometries. Each building is characterized by 8 features that influence heating load requirements. The analysis includes:

- Exploratory Data Analysis (EDA)
- Dimensionality Reduction using Principal Component Analysis (PCA)
- Predictive Modeling with Linear Regression and Neural Networks
- Binary Classification with a Hybrid Modeling Strategy

## Dataset

The dataset is based on the **UCI Energy Efficiency Dataset** and contains:
- **768 samples** (buildings)
- **8 features**: Relative Compactness, Surface Area, Wall Area, Roof Area, Overall Height, Orientation, Glazing Area, Glazing Area Distribution
- **1 target variable**: Heating Load

## Project Structure

```
.
├── building_heat_efficiency.ipynb    # Main Jupyter notebook with all analyses
├── data/
│   └── summative-2425-data.csv      # Dataset
├── download_data.py                  # Script to download dataset from UCI repository
└── README.md                         # This file
```

## Requirements

- Python 3.8+
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- openpyxl (for Excel file handling)
- jupyter

Install all requirements:
```bash
pip install pandas numpy scikit-learn matplotlib seaborn openpyxl jupyter
```

## Running the Analysis

### Option 1: Using Jupyter Notebook
```bash
jupyter notebook building_heat_efficiency.ipynb
```

### Option 2: Execute All Cells
```bash
jupyter nbconvert --to notebook --execute building_heat_efficiency.ipynb --ExecutePreprocessor.timeout=600
```

## Tasks Implemented

### Task 1: Data Preparation and Standardization
- Split data into training and test sets (5:1 ratio)
- Standardize features using StandardScaler
- Commentary on importance of standardization

### Task 2: Principal Component Analysis (PCA)
- Perform PCA on standardized training features
- Create scree plot showing cumulative explained variance
- Determine components for 85% variance retention
- Reduce dimensionality to maximum 5 dimensions
- Analyze information loss

### Task 3: Linear Regression with PCA
- Train linear regression models with 1-5 PCA components
- 5-fold cross-validation for performance estimation
- Plot MSE vs number of components with error bars

### Task 4: Neural Network Modeling
- Systematic experimentation with different architectures:
  - Varying hidden layers (1-3 layers)
  - Different neurons per layer (50-150)
  - Multiple activation functions (ReLU, tanh)
  - Regularization techniques (L2, early stopping)
- Cross-validation for hyperparameter selection
- Performance comparison with linear regression
- Computational complexity analysis

### Task 5: Binary Classification and Hybrid Strategy
- Categorize buildings into high/low heating load
- Develop combined modeling strategy:
  - Linear regression for initial predictions
  - Neural network for uncertain cases
  - Uncertainty-based refinement criterion
- ROC curve analysis for all approaches
- Performance comparison and practical recommendations

## Key Findings

1. **Standardization is Critical**: Features have vastly different scales (0.62-0.98 for Relative Compactness vs 514-808 for Surface Area), making standardization essential for algorithm performance.

2. **PCA Effectiveness**: 5 principal components retain ~97% of variance, providing excellent dimensionality reduction with minimal information loss.

3. **Non-linear Relationships**: Neural networks outperform linear regression, indicating non-linear relationships between features and heating load.

4. **Hybrid Strategy Optimal**: The combined approach achieves near-neural-network accuracy while using it only for 20-40% of uncertain cases, offering the best balance for production deployment.

5. **High Classification Accuracy**: All models achieve >95% binary classification accuracy, demonstrating strong predictive power.

## Results Summary

| Metric | Linear Regression | Neural Network | Combined Strategy |
|--------|------------------|----------------|-------------------|
| Test MSE | ~10-15 | ~8-12 | ~9-13 |
| Binary Accuracy | >95% | >96% | >96% |
| ROC AUC | >0.95 | >0.97 | >0.96 |
| Computational Cost | Low | High | Medium |
| NN Usage | 0% | 100% | 20-40% |

## Model Deployment Recommendations

### Use Linear Regression When:
- Real-time applications requiring sub-millisecond inference
- Edge devices with limited computational resources
- Interpretability is paramount
- Slight accuracy loss is acceptable

### Use Neural Network When:
- Maximum accuracy is critical (regulatory compliance)
- Batch processing scenarios
- Cloud-based systems with ample resources
- Prediction errors have high costs

### Use Combined Strategy When:
- Production systems needing balance of speed and accuracy
- Applications with variable computational budgets
- Most predictions are straightforward
- Cost-effective deployment at scale

## Future Work

- Investigate ensemble methods (Random Forests, Gradient Boosting)
- Explore deep learning with advanced regularization
- Analyze feature importance and physical interpretations
- Extend to multi-target prediction (heating + cooling loads)
- Deploy in real-world building management systems

## References

- **Dataset Source**: UCI Machine Learning Repository - Energy Efficiency Dataset
- **Paper**: Tsanas, A., & Xifara, A. (2012). Accurate quantitative estimation of energy performance of residential buildings using statistical machine learning tools. *Energy and Buildings*, 49, 560-567.
- **Dataset URL**: https://archive.ics.uci.edu/dataset/242/energy+efficiency

## License

This project is created for educational purposes as part of a machine learning assignment.

## Author

Developed as part of a comprehensive machine learning course assignment on building energy efficiency analysis.
