Project Title: Interpretable Diabetes Prediction with SVM

Overview:
This project uses a Support Vector Machine (SVM) to predict diabetes risk based on the Pima Indians Diabetes Dataset. Beyond simple classification, the goal was to implement Explainable AI (XAI) to understand the model's decision-making process.

Technical Stack

Language: Python

Libraries: Scikit-Learn (SVM), SHAP (Interpretability), Pandas/NumPy (Data Processing)

Model: SVC with a linear kernel

The Debugging Log (Lessons Learned) During development, I encountered several "real-world" hurdles that required deep dives into documentation:

The Environment Gap: Resolved a ModuleNotFoundError for SHAP by using %pip install directly within the Jupyter kernel and performing a manual kernel restart.

Algorithm Compatibility: Initially attempted to use TreeExplainer, which is incompatible with SVMs. I successfully pivoted to KernelExplainer, a model-agnostic tool, to generate feature attribution.

Data Structure Mismatch: Encountered a numpy.ndarray object has no attribute 'iloc' error after data scaling. I resolved this by transitioning from Pandas .iloc indexing to NumPy slicing ([row, col]) to maintain compatibility with the scaled data format.

second phase: model optimization and evaluation 

1. Hyperparameter Tuning (The Search for the Best "Brain")
2. 
I implemented GridSearchCV to systematically test 32 different combinations of parameters.

The Goal: To find the optimal balance between the kernel type (Linear vs. RBF) and the C value (penalty for misclassification).

The Result: The search confirmed that a Linear Kernel with C=1 was the optimal configuration.

Technical Insight: The fact that the Linear kernel outperformed the RBF (Radial Basis Function) kernel suggests that the relationship between the health features and diabetes risk is largely linear in this dataset.

2. Cross-Validation
   
Instead of relying on a single train/test split, I used 5-Fold Cross-Validation.

The Logic: This process splits the data five different ways and averages the scores to ensure the model isn't just "getting lucky" on a specific subset of data.

The Score: We achieved a stable cross-validated accuracy of 78.1%.

3. Algorithm Comparison (SVM vs. Random Forest)
   
To prove the SVM was the right tool, I ran a "Champion vs. Challenger" test against a Random Forest Classifier.

SVM Score: 78.1%

Random Forest Score: 76.7%

Conclusion: The SVM remains the superior model for this specific tabular dataset. Random Forest, while powerful, likely over-complicated the clean linear boundaries found by the SVM.
