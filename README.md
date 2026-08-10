# 🎓 Student Performance Prediction

## 📌 Overview

This project focuses on predicting whether a student will **pass or fail** based on key academic and behavioral factors. By leveraging machine learning techniques, the model aims to assist educational institutions in identifying **at-risk students early** and enabling timely interventions.

---

## 🚀 Features

* Predicts student performance (Pass/Fail)
* Uses multiple input factors:

  * Study Hours
  * Attendance
  * Previous Marks
  * Assignment Scores
* Compares multiple machine learning models
* Provides feature importance analysis

---

## 🧠 Model Selection

Two models were evaluated for this task:

* **Logistic Regression**
* **Random Forest Classifier**

The **Random Forest Classifier** was selected as the final model because it:

* Captures **non-linear relationships** effectively
* Handles feature interactions better
* Achieved **higher accuracy** compared to Logistic Regression

---

## 📊 Dataset

* Total Records: **200**
* Type: **Synthetic dataset**
* Features:

  * Study Hours
  * Attendance
  * Previous Marks
  * Assignment Scores
* Target Variable:

  * Pass / Fail

---

## 📈 Model Evaluation

The model performance was evaluated using:

* **Confusion Matrix** – to measure classification accuracy
* **Feature Importance Analysis** – to understand key influencing factors

### 🔍 Key Insights

* **Study Hours** is the most significant factor affecting student performance
* Followed by **Previous Marks**
* Attendance and Assignment Scores also contribute but with relatively lower impact

---

## 💡 Use Case

This system can be used by:

* Schools and universities
* Academic advisors
* EdTech platforms

### Benefits:

* Early identification of struggling students
* Data-driven academic support strategies
* Improved student success rates

---

## 🛠️ Tech Stack

* Python
* Scikit-learn
* Pandas
* NumPy

---

## 📌 Future Improvements

* Use real-world datasets for better generalization
* Add more features (e.g., socio-economic factors, study habits)
* Deploy as a web-based dashboard for real-time predictions

---

## 👤 Author

**Hamza Ali**
BS Software Engineering Student
COMSATS University Islamabad, Lahore Campus

---
