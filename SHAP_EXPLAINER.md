Why SHAP?

In healthcare AI, "Black Box" models are insufficient.
We need to know why a model predicts a specific outcome to ensure safety and trust.

I chose the SHAP (SHapley Additive exPlanations) Force Plot because it breaks down a complex
prediction into a simple "Push and Pull" mechanic based on Game Theory.

How to Read the Force PlotThe plot visualizes the battle between different health markers:

The Base Value (0.26): The starting point, representing the average risk in the dataset.

Red Arrows (Positive SHAP): Features that increase the risk of diabetes. 

In my test case, Pregnancies (+0.69) acted as a risk factor.

Blue Arrows (Negative SHAP): Protective features that lower the risk.

For this patient, Glucose (-0.78) and Insulin (-0.79) were the strongest forces pulling the prediction toward "Healthy."

The Result f(x): The final point where these forces balance out.

For this specific case, the result was 0.00, indicating a negative diagnosis.

The Value of this ApproachBy using SHAP, we can verify that the model is making decisions for the right reasons 
(e.g., prioritizing Glucose levels over less relevant noise), which is a critical step in deploying responsible AI.
