# Crop Yield Prediction (Under Development)

## Overview

Crop yield prediction is a crucial aspect of agricultural planning, helping farmers and policymakers make informed decisions. This project leverages machine learning to predict crop yields based on various factors, including weather conditions, soil quality, and historical crop data.

## Project Objectives

- Develop a machine learning model to predict crop yield.
- Use different machine learning algorithms to compare performance.
- Optimize hyperparameters for better accuracy.
- Save and deploy the best-performing model.

## Data Sources

The dataset used in this project is sourced from:

- **Kaggle**: [Crop Yield Prediction Dataset](https://www.kaggle.com/code/kushagranull/crop-yield-prediction)
- **FAO**: [FAO Crop Data](https://www.fao.org/faostat/en/#data/QCL)

## Learning Resources

- Stack Overflow, GitHub, and Kaggle discussions.
- Articles and research papers:
  - [Machine Learning in Agriculture](https://www.itransition.com/machine-learning/agriculture)
  - [Crop Yield Prediction Research](https://arxiv.org/abs/2308.08948)
  - [Nature Article on Crop Yield](https://www.nature.com/articles/s41598-020-80820-1)
  - [MDPI - Crop Yield Prediction](https://www.mdpi.com/2076-3417/13/16/9288)
  - [Data Science Projects in Agriculture](https://www.geeksforgeeks.org/5-data-science-projects-in-agriculture/)
  - [DataCamp - Crop Yield Project](https://www.datacamp.com/projects/1772)
  - [GitHub Repository Example](https://github.com/jordanwheeler7/capstone-crop-yield/blob/main/crop_yield.ipynb)
  - [Column Transformer in ML](https://medium.com/@noorfatimaafzalbutt/the-magic-of-column-transformer-in-machine-learning-5783c412e44c)

## Model Development

### Data Preprocessing

The dataset consists of:

- **Categorical features**: 'Item', 'Area'
- **Numerical features**: 'Pesticides', 'avg_temp', 'avg_precipitation'

Preprocessing steps:

1. **One-Hot Encoding** for categorical variables.
2. **Standardization/Normalization** for numerical variables.
3. **Splitting** into training and testing sets.

### Machine Learning Models Evaluated

1. **Random Forest Regressor**
2. **Gradient Boosting Regressor** _(Best performing model)_
3. **Decision Tree Regressor**
4. **K-Nearest Neighbors (KNN)**
5. **Multi-Layer Perceptron (MLP) Neural Network**

### Model Performance

- **Gradient Boosting Regressor** achieved the best results:
  - Training R-squared: **0.9994**
  - Testing R-squared: **0.9813**
  - Testing MAE: **4334.70**
  - Testing RMSE: **11,500.97**

## Model Saving and Deployment

### Prediction Pipeline

```python
import joblib
import pandas as pd

# Load the pre-trained model and preprocessor
model = joblib.load('gradient_boosting_model.pkl')
preprocessor = joblib.load('preprocessor.pkl')

def predict_yield(input_data):
    df = pd.DataFrame([input_data])
    transformed_data = preprocessor.transform(df)
    prediction = model.predict(transformed_data)
    return prediction[0]

# Example usage:
new_data = {
    'Item': 'Cassava',
    'Area': 'Angola',
    'Pesticides': 64.0,
    'avg_temp': 24.12,
    'avg_precipitation': 1010
}
print("Predicted Yield:", predict_yield(new_data))
```

## Future Improvements

- Improve neural network performance by tuning hyperparameters.
- Experiment with deep learning models.
- Gather more diverse datasets for training.

## License

This project is released under the **MIT License**.

## Contributors

- **Arif Haidari**

## Contact

For any questions or collaboration requests, feel free to reach out!
