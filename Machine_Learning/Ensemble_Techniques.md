### 🎯 Core Ensemble Techniques

These are the foundational approaches:

- **Bagging (Bootstrap Aggregating)**
    
    - Trains multiple models independently on random subsets of the data
    - Reduces variance and helps prevent overfitting
    - Example: **Random Forest**
- **Boosting**
    
    - Trains models sequentially, each correcting the errors of the previous
    - Reduces bias and improves accuracy
    - Examples: **AdaBoost**, **Gradient Boosting**, **XGBoost**, **LightGBM**, **CatBoost**
- **Stacking (Stacked Generalization)**
    
    - Combines predictions from multiple models using a meta-model
    - Can mix different types of base learners for better performance

### 🧠 Simple Ensemble Strategies

These are more straightforward but still effective:

- **Voting**
    
    - **Hard Voting**: Majority class wins
    - **Soft Voting**: Averages predicted probabilities
- **Averaging**
    
    - Takes the mean of predictions (used in regression)
- **Weighted Averaging**
    
    - Assigns different weights to models based on their performance

### 🧪 Specialized Variants

These build on the core techniques:

- **Blending**
    
    - Similar to stacking but uses a holdout set for the meta-model
    - Faster but less robust than stacking
- **Random Subspace Method**
    
    - Trains models on random subsets of features
    - Enhances diversity among models

### 📊 Summary Table

|Technique|Strategy|Common Use Case|
|---|---|---|
|Bagging|Parallel training|Reduce variance|
|Boosting|Sequential training|Reduce bias|
|Stacking|Meta-modeling|Combine diverse models|
|Voting|Majority decision|Classification|
|Averaging|Mean prediction|Regression|
|Weighted Averaging|Weighted mean|Regression/Classification|
|Blending|Holdout meta-model|Fast ensemble|
|Random Subspace|Feature sampling|Increase diversity|
