# Airline Customer Satisfaction Prediction
## Background Overview

Customer satisfaction is a critical performance indicator in the airline industry, directly influencing customer retention, brand perception, and long-term profitability. Airlines operate in a highly competitive environment where service quality, operational efficiency, and customer experience must be continuously optimized.

This project focuses on understanding what truly drives customer satisfaction by leveraging data collected from a large international airline. The goal is not only to build predictive models capable of accurately classifying satisfaction levels, but also to extract actionable insights that can support decision-making.

The analysis integrates exploratory data analysis, dimensionality reduction techniques, and multiple machine learning models, with a strong emphasis on interpretability and real-world applicability.

## Data Structure Overview

The dataset consists of 129,880 passenger observations and 23 variables, each representing a complete flight experience.

### Variables included

#### Customer and Demographics
- Gender
- Customer Type
- Age

#### Travel Characteristics
- Type of Travel
- Class
- Flight Distance

#### Operational Metrics
- Departure Delay in Minutes
- Arrival Delay in Minutes

#### Service Ratings (scale 0 to 5)
- Seat comfort
- Departure/Arrival time convenient
- Food and drink
- Gate location
- Inflight wifi service
- Inflight entertainment
- Online support
- Ease of Online booking
- On-board service
- Leg room service
- Baggage handling
- Checkin service
- Cleanliness
- Online boarding

### Target Variable
- Satisfaction (binary classification)

### Data Collection Context

The data was collected through post-flight customer surveys, where passengers rated different aspects of their experience on a 0 to 5 scale, covering both onboard services and airport-related factors.

### Methodological Approach

#### 1. Data Preparation
- Missing value treatment, with median imputation for Arrival Delay in Minutes
- Encoding of categorical variables
- Feature selection

#### 2. Exploratory Data Analysis
- Distribution analysis
- Cross-variable comparisons
- Identification of satisfaction patterns
- Delay segmentation analysis using 30-minute intervals up to 180 minutes

#### 3. PCA (Dimensionality Reduction)

PCA was applied to identify latent structures among the service-related variables.

### PCA Components Identified
- Digital_Overall_Service_Experience
- Airport_Convenience_Basic_Travel_Comfort
- Onboard_Comfort_Operational_Service
- Entertainment_vs_Travel_Convenience
- Checkin_Service_Component
- Leg_Room_Comfort

These components group correlated service variables into broader experience dimensions.

#### 4. Predictive Modelling

The following models were tested:
- Logistic Regression
- Decision Tree
- Random Forest
- Bagging
- Gradient Boosting
- XGBoost
- Neural Networks

<img width="1570" height="790" alt="imagem" src="https://github.com/user-attachments/assets/aae52758-35e9-41e8-8c9d-36e3619069d6" />

#### 5. Model Optimization
- GridSearchCV applied across several models
- Neural network tuning, with one tuning configuration
- Baseline vs PCA comparison

#### 6. Model Explainability
- SHAP values for XGBoost
- Permutation importance for neural networks
  
<img width="794" height="940" alt="imagem" src="https://github.com/user-attachments/assets/b90ee37f-4791-499c-b3f6-7bb80fab28c2" />


## Executive Summary
### Overview of Findings

The best-performing model was XGBoost using the baseline dataset, achieving:

- F1 Score ≈ 0.959
- Accuracy ≈ 0.959
- AUC ≈ 0.959

The model revealed that customer satisfaction is primarily driven by service quality and experience-related variables.

### Most important positive drivers
- Seat comfort
- Customer Type
- Type of Travel

### Most important negative drivers
- Gender
- Cleanliness
- Online support

### Metrics and Achievements

- High predictive performance, with F1, Accuracy and AUC close to 0.96
- PCA identified 6 latent components that help explain how service preferences cluster together
- Reliable prediction of customer satisfaction with practical business relevance

### Practical Impact

The winning model can be used to:
- Predict dissatisfaction in real time
- Trigger proactive customer recovery actions
- Support service improvement strategies
- Help prioritize which service attributes deserve preventive investment

The variables identified as most influential also provide a clear roadmap for management, allowing the airline to improve the dimensions that matter most to customers before dissatisfaction becomes widespread.

## Insights Deep Dive

### Service Quality Dominates Satisfaction

Variables such as Seat comfort, Inflight entertainment, Baggage handling and Ease of Online booking emerge as highly relevant. This shows that customer satisfaction is largely determined by the perceived quality and consistency of the service experience.

### Customer Loyalty is Critical

Customer Type plays a major role, with loyal customers showing much higher satisfaction rates than disloyal customers. This reinforces the importance of retention, relationship management and loyalty strategies.

### Travel Context Matters

Type of Travel is one of the strongest predictors. Business travel appears to be associated with higher satisfaction, suggesting that customer expectations and usage patterns differ significantly across travel purposes.

### Delays Affect Satisfaction

Exploratory analysis showed a clear downward trend in satisfaction as delays increase. Although delay variables were not among the strongest overall predictors compared with service-related variables, they still play a meaningful role, particularly Departure Delay in Minutes.

### PCA Helped Explain Latent Service Dimensions

PCA uncovered six broader components that summarize the service ratings:
- Digital_Overall_Service_Experience
- Airport_Convenience_Basic_Travel_Comfort
- Onboard_Comfort_Operational_Service
- Entertainment_vs_Travel_Convenience
- Checkin_Service_Component
- Leg_Room_Comfort

These components were useful for understanding how customer perceptions group together, especially across digital experience, airport convenience and onboard comfort.

## Recommendations

### Use PCA for Exploration, Not for Prediction

PCA proved useful for exploratory analysis and for identifying how service dimensions cluster together. However, PCA-based models consistently underperformed relative to baseline models. For that reason, PCA should be used primarily as an exploratory and interpretive tool, rather than as the preferred feature set for predictive modelling.

### Prefer Tree-Based Models for This Problem

Tree-based models, especially XGBoost, Random Forest and Bagging, produced very strong results. XGBoost was the winning model, but the broader conclusion is that this family of models is highly effective for this type of structured tabular dataset.

### Neural Networks Are Not Necessary in This Case

Neural networks achieved good predictive performance, and the tuned version delivered competitive results. However, they were not necessary for this project, since other models already achieved very strong results, with simpler implementation, lower interpretive difficulty, and in some cases even better performance.

Neural network tuning also demanded substantial computational time and additional experimentation. One tuning process took approximately 3 hours to run. For this type of analysis, where tree-based methods already provide excellent results, neural networks do not appear to be the most efficient choice.

### Focus Operational Improvements on the Variables That Matter Most

The company should prioritize improvements in:
- Seat comfort
- Inflight entertainment
- Ease of Online booking
- Checkin service
- Baggage handling
- Online boarding
- On-board service
- Leg room service
- Departure and arrival convenience

These are the variables with the greatest potential to improve satisfaction and customer perception in a preventive way.

## Model Performance Comparison

| Model                              | F1 Score | Accuracy | AUC    |
|------------------------------------|----------|----------|--------|
| XGBoost Baseline                   | 0.9590   | 0.9593   | 0.9595 |
| Random Forest Baseline             | 0.9584   | 0.9587   | 0.9593 |
| Neural Network Tuning              | 0.9538   | 0.9541   | 0.9542 |
| Bagging Baseline                   | 0.9524   | 0.9527   | 0.9535 |
| GridSearch Bagging Baseline        | 0.9524   | 0.9527   | 0.9535 |
| Neural Network Baseline            | 0.9503   | 0.9506   | 0.9514 |
| GridSearch Decision Tree Baseline  | 0.9454   | 0.9458   | 0.9459 |
| Decision Tree Baseline             | 0.9386   | 0.9392   | 0.9383 |
| Random Forest PCA                  | 0.9252   | 0.9258   | 0.9252 |
| GridSearch Gradient Boosting (PCA) | 0.8989   | 0.8997   | 0.8993 |
| GridSearch Decision Tree PCA       | 0.8989   | 0.8997   | 0.8993 |
| Decision Tree PCA                  | 0.8864   | 0.8874   | 0.8864 |
| GridSearch Random Forest           | 0.8776   | 0.8788   | 0.8772 |
