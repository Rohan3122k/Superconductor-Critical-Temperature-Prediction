# Superconductor Critical Temperature Prediction

## 1. Introduction
Superconductors are materials that exhibit zero electrical resistance below a certain temperature, known as the critical temperature (`critical_temp`). These materials are crucial for various industries, including MRI machines, energy-efficient power grids, and quantum computing. However, identifying new superconductors through laboratory experiments is time-consuming and expensive.

This project applies machine learning (ML) techniques to predict the critical temperature of superconductors based on their atomic and physical properties. By leveraging data science, we can accelerate the discovery of high-temperature superconductors that could revolutionize modern technology.

## 2. Problem Statement
- The challenge in superconductor research is identifying which materials can become superconducting at higher temperatures.
- Traditional methods rely on trial-and-error experiments, which are slow and costly.
- **Goal:** Develop a predictive machine learning model to estimate the `critical_temp` of a material using its atomic properties, reducing reliance on experimental testing.

## 3. Dataset Overview
### Data Source
The dataset used in this project comes from:
**Hamidieh, K. (2018). Superconductivity Data [Dataset]. UCI Machine Learning Repository.**  
[https://doi.org/10.24432/C53P47](https://doi.org/10.24432/C53P47)

### Key Features in the Dataset
- **Mean Atomic Mass** → Average atomic mass of the material.
- **Mean Valence Electrons** → Affects bonding and electrical properties.
- **Atomic Entropy** → Related to material stability.
- **Density & Atomic Radius** → Impact how electrons move through the material.
- **Critical Temperature (`critical_temp`)** → The target variable to predict.

### Initial Insights
- The highest recorded `critical_temp` in the dataset is ~185K, making it a candidate for high-temperature superconductivity.
- Many materials have `critical_temp` < 20K, meaning they require extreme cooling for superconductivity.

## 4. Data Processing & Feature Engineering
### Data Cleaning & Preprocessing
- Checked for missing values → No missing values found.
- Scaled the data using StandardScaler to normalize features.
- Applied correlation analysis to understand feature relationships.

### Principal Component Analysis (PCA)
- PCA was applied to reduce 82 features to 17 components while keeping 95% of data variance.
- This improved model efficiency without losing predictive power.

## 5. Machine Learning Models & Results
### Baseline Model: Linear Regression
- **R² Score:** 0.6121 → Explained only 61.21% of the variance.
- **Mean Squared Error (MSE):** 446.48 → High error.
- **Conclusion:** Too simple to capture complex material behaviors.

### Best Model: Random Forest Regressor
- **R² Score (Before Tuning):** 0.9171 → Much better fit.
- **MSE:** 95.39 → Lower error.
- **Conclusion:** Random Forest is better at capturing nonlinear relationships in superconducting properties.

## 6. Model Optimization – Hyperparameter Tuning
- Used RandomizedSearchCV to optimize Random Forest parameters.
- **Best Parameters Found:**
  - `n_estimators = 400` (Number of decision trees).
  - `max_depth = 30` (Tree depth).
  - `min_samples_split = 2` (Minimum samples per split).

### Final Model Performance
- **R² Score:** 0.9181 → 91.81% of variance explained.
- **MSE:** 94.32 → Lowest prediction error after tuning.

## 7. Model Evaluation & Insights
### Residual Analysis & Validation
- **Residual Plot:** Showed randomly distributed errors, indicating no major issues.
- **Prediction vs. Actual Plot:** Verified that predicted values align well with actual values.

### Feature Importance Analysis
- The most important atomic properties influencing `critical_temp`:
  - Mean Atomic Mass
  - Mean Valence Electrons
  - Atomic Entropy & Density

## 8. Industry Impact & Future Applications
### Why This Research Matters
- **Superconductors are vital for modern energy & technology:**
  - Power Grids: Superconducting cables reduce energy loss.
  - Medical (MRI Machines): Used for strong magnetic fields.
  - Quantum Computing: Enable superconducting qubits.

- **AI-Driven Material Discovery Can Save Millions**
  - Instead of costly lab experiments, AI can predict material properties in seconds.
  - Machine learning accelerates high-temperature superconductor discovery, benefiting energy & computing industries.

## 9. Next Steps & Future Work
- Improve Feature Engineering: Test more complex interactions between atomic properties.
- Try XGBoost: Explore boosting algorithms for even better performance.
- Deploy the Model: Build a Flask API for real-time superconductor prediction.
- Expand Dataset: Integrate experimental data from real-world superconductors.

### Final Thoughts
- This project demonstrates AI in materials science.
- The model can help scientists discover new superconductors faster and cheaper.
- A high-impact machine learning solution for scientific advancements.

