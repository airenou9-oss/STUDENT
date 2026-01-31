Student Dropout Early Warning System – Short Report
1. Data Cleaning

Dataset: xAPI-Edu-Data

Target column Class converted to binary Dropout (1 = dropout, 0 = continue)

Dropped original Class column after conversion

Checked for missing values: none found

Categorical columns: One-hot encoded

Numerical columns: Standard scaled

Focused only on early-semester features (academic activity, basic student info)
2. Features Used

Categorical Features:

Gender, Nationality, PlaceofBirth, StageID, GradeID, SectionID, Relation, Topic, etc.

One-hot encoded

Numerical Features:

Student activity metrics: RaisedHands, VisitedResources, AnnouncementsView, Discussion

Standard scaled

Target:

Dropout (binary)
Reason:

Robust to noisy/incomplete data

Handles mixed categorical + numerical features

Easy to explain using feature importance

Evaluation (Train/Test split 80/20):

Accuracy: ~92%

Recall (dropout class): prioritized to catch as many dropouts as possible

Precision: balanced to avoid too many false alarms

Pipeline:

Preprocessing + classifier in a single pipeline (Coding1.joblib)

4. Risk Thresholds

Risk score = predicted probability of dropout

Labels:
Risk Score	Risk Label
0 – 0.4	Low
0.4 – 0.7	Medium
0.7 – 1.0	High

High-risk students flagged for immediate intervention

5. Key Reasons Behind Dropout Predictions

Most important features (from Random Forest):

Low engagement: RaisedHands, VisitedResources, Discussion

Participation: AnnouncementsView

Academic stage: StageID, GradeID

Interpretation for advisors:

Students with low participation metrics early in the semester are more likely to drop outLack of interaction in online learning predicts high risk

3. Model Choice & Metrics

Model: Random Forest Classifier (200 trees, random_state=42)
