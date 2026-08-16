# Student Performance Prediction

## Virexo Internship — Week 1 Task (AI & ML)

A machine learning model that predicts whether a student will pass or fail based on study hours, attendance, previous marks, and assignment scores.

---

## Overview

This project builds a binary classifier to identify students at risk of failing, using four academic and behavioral indicators. Two models are trained and compared — Logistic Regression as a baseline, and Random Forest as the final model — with the goal of demonstrating a complete, correctly evaluated ML pipeline rather than a single black-box result.

---

## Dataset

* **Size:** 200 records
* **Type:** Synthetic, generated in-script (no real student data was available for this task)
* **Features:**

  * Study Hours (1–10)
  * Attendance % (50–100)
  * Previous Marks % (40–95)
  * Assignment Score % (30–100)
* **Target:** Pass / Fail

Labels are generated from a weighted combination of the four features plus random noise, so the target isn't a perfectly deterministic function of the inputs — this keeps the prediction task realistic instead of trivially solvable.

---

## Models

| **ModelTest Accuracy**   |     |
| ------------------------ | --- |
| Logistic Regression      | 80% |
| Random Forest Classifier | 85% |

**Random Forest** was selected as the final model because it handles non-linear relationships better than Logistic Regression. For example, the relationship between study hours and passing probability is not a straight line—students who study less than 4 hours almost always fail, but beyond 6 hours the benefit plateaus. Random Forest naturally captures these thresholds without requiring manual feature engineering like polynomial terms.

### Feature Importance (Random Forest)

| **FeatureImportance** |       |
| --------------------- | ----- |
| Study Hours           | 65.0% |
| Attendance            | 13.0% |
| Previous Marks        | 12.5% |
| Assignment Score      | 9.6%  |

**Key Insight:** Study hours is by far the strongest predictor. The most actionable insight: A student with >6 study hours, >80% attendance, and >70% previous marks has a 90%+ chance of passing. This kind of insight can help teachers intervene early with at-risk students.

---

## Tech Stack

* Python 3
* pandas, NumPy
* scikit-learn
* Matplotlib, Seaborn

---

## Project Structure

text

```
├── student_performance_prediction.py   # Main script
├── student_performance_dataset.csv     # Generated dataset
├── correlation_heatmap.png             # EDA output
├── pairplot.png                        # EDA output
├── confusion_matrix.png                # Model evaluation output
├── feature_importance.png              # Model evaluation output
└── README.md
```

---

## How to Run

bash

```
pip install pandas numpy matplotlib seaborn scikit-learn
python student_performance_prediction.py
```

This generates the dataset, trains both models, prints accuracy and classification metrics to the console, and saves all plots to the working directory.

---

## Tools / Technologies Used

I kept the stack simple and focused. Python 3 was the backbone, with pandas and numpy for generating the student dataset. For visuals, I used matplotlib and seaborn to plot the correlation heatmap, pairplot, confusion matrix, and feature importance charts. Scikit-learn did all the heavy lifting for the models—Logistic Regression and Random Forest—including train-test split, scaling, and the classification metrics. Everything was built inside a Jupyter Notebook, which made it easy to iterate and experiment.

---

## Challenges Faced

The biggest frustration was a silly math bug that took me way too long to find. I had set the pass/fail threshold to 12, but my feature engineering pipeline physically couldn't produce a number higher than 9.9. Because of that, every single one of my 200 students was labeled as "Fail". When I tried to run the classification report, it crashed with a "only one class" error. I only caught it because I printed the class distribution before training—which I should have done in the first place.

After fixing that, I ran the model again and got 100% accuracy. For a split second I was happy, but then my gut told me that was a huge red flag. I realized I had accidentally created a "cheating" dataset—the model was just reverse-engineering the exact formula I used to generate the labels. To fix this, I added random noise to the label logic so the model actually had to learn a pattern, not just memorize my formula. That dropped the accuracy to around 82-85%, which actually felt way better because it now behaves like a messy, real-world dataset.

---

## What Did You Learn?

The biggest takeaway? Never trust your data pipeline just because it runs without throwing an error. A simple `value_counts()` on my target variable would have saved me an hour of debugging. I also learned that 100% accuracy on your first try isn't a flex—it usually means you leaked the answer key into the features without realizing it.

This project really solidified the practical difference between Logistic Regression (which needs scaling to work properly) and Random Forest (which held up really well without any scaling on my tabular data). Most importantly, I learned that a code comment that doesn't match the logic is worse than no comment at all—it completely misled me when I was scanning for the bug.

---

## Limitations

* Dataset is synthetic; results are not validated against real student records.
* No hyperparameter tuning was performed — Random Forest uses default settings (100 estimators).
* Sample size (200) is small for a production-grade model.

---

## Future Improvements

* Validate on a real academic dataset
* Add hyperparameter tuning and cross-validation
* Include additional features (e.g., socio-economic background, study habits)
* **Deploy as a simple web dashboard** where teachers can input daily attendance and get a real-time "risk score" for each student. This would shift the model from a static prediction tool to an actionable early-warning system.

---

## Author

**Hamza Ali**
BS Software Engineering, COMSATS University Islamabad — Lahore Campus
