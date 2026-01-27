Project Title: Interpretable Diabetes Prediction with SVM

Overview This project uses a Support Vector Machine (SVM) to predict diabetes risk based on the Pima Indians Diabetes Dataset. Beyond simple classification, the goal was to implement Explainable AI (XAI) to understand the model's decision-making process.

Technical Stack

Language: Python

Libraries: Scikit-Learn (SVM), SHAP (Interpretability), Pandas/NumPy (Data Processing)

Model: SVC with a linear kernel

The Debugging Log (Lessons Learned) During development, I encountered several "real-world" hurdles that required deep dives into documentation:

The Environment Gap: Resolved a ModuleNotFoundError for SHAP by using %pip install directly within the Jupyter kernel and performing a manual kernel restart.

Algorithm Compatibility: Initially attempted to use TreeExplainer, which is incompatible with SVMs. I successfully pivoted to KernelExplainer, a model-agnostic tool, to generate feature attribution.

Data Structure Mismatch: Encountered a numpy.ndarray object has no attribute 'iloc' error after data scaling. I resolved this by transitioning from Pandas .iloc indexing to NumPy slicing ([row, col]) to maintain compatibility with the scaled data format.
