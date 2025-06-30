# 🏡 London Property Price Prediction – 2024

This project applies machine learning regression techniques to predict housing prices in London using real data from 2024. The analysis includes data cleaning, transformation, model evaluation, and hyperparameter tuning. The goal is to develop a reliable model to estimate property prices based on features such as number of bedrooms, bathrooms, size in square feet, and property type.

---

## 📁 Dataset Overview

- Source: [Kaggle – Real Estate Data London 2024](https://www.kaggle.com/datasets/kanchana1990/real-estate-data-london-2024)
- 1019 records, 9 features
- Key variables:
  - `addedOn` (date listed)
  - `bedrooms`, `bathrooms`, `sizeSqFeetMax`
  - `propertyType`, `description`
  - `Price` (target)

---

## 🧹 Data Preprocessing

### 🔧 Data Cleaning

- Removed null values in: `addedOn`, `sizeSqFeetMax`, `bedrooms`, `bathrooms`
- Converted `Price` from text (with £ symbol) to float
- Outliers were retained for their potential significance

### 🔁 Data Transformation

- `propertyType` encoded as dummy variables (Boolean)
- Applied **log transformation** to `Price` to improve linearity
- Used **StandardScaler** on `bedrooms`, `bathrooms`, and `sizeSqFeetMax`

### ⚠️ Underfitting Test

- Models trained with subsets (10%, 15%, 25%) showed lower R² and higher MSE
- Indicates insufficient data can limit learning of variable relationships

---

## 🧪 Models & Evaluation

### 🔍 Initial Models Tested

- **Linear Regression**
- **Decision Tree Regressor**
- **Random Forest Regressor**
- **K-Nearest Neighbors**
- **Support Vector Regressor**

> ✅ **Best initial model:** Random Forest  
> 📈 **Initial R²:** 54.7%  
> ✅ **Low MSE**, **low MAE**, suggesting relatively accurate and consistent predictions.

### 🔁 Cross-Validation (5-Fold)

- Low standard deviation across folds
- Consistent model behavior = good generalization

---

## 🔧 Hyperparameter Tuning

### ⚙️ GridSearchCV for Random Forest

- Tested multiple combinations of parameters
- Improved model accuracy and variance explanation

> 📈 **Post-tuning R²:** 62.5%  
> 📉 **Lower MSE**, better predictive performance  
> 🔁 Cross-validation showed slightly more variability, but still low = stable model

---

## 📊 Key Insights

- The strongest predictor of price is **`sizeSqFeetMax`**, with **73% correlation** to the target.
- Feature engineering, log transformation, and scaling significantly improved model performance.
- Proper **hyperparameter tuning** led to a +7% boost in R² score, proving its impact.

---

## 🧠 Conclusion

This project demonstrates that careful **preprocessing**, appropriate **model selection**, and **hyperparameter optimization** are essential to building accurate predictive models in real estate. The final model (Random Forest with tuned parameters) offers reliable estimates of housing prices and can serve as a foundation for future deployment or integration in pricing tools.

---

## 📚 References

- Kanchana1990 (2024). *Real Estate Data London 2024*. [Kaggle](https://www.kaggle.com/datasets/kanchana1990/real-estate-data-london-2024)
- Mitchell, T. (1997). *Machine Learning*. [PDF](https://www.cin.ufpe.br/~cavmj/Machine%20-%20Learning%20-%20Tom%20Mitchell.pdf)
- Molin, S. (2021). *Hands-On Data Analysis with Pandas*. [Google Books](https://www.google.ie/books/edition/Hands_On_Data_Analysis_with_Pandas/Eh4sEAAAQBAJ)
