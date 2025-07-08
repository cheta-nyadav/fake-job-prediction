## 🛑 Problem Statement

In today's digital job market, distinguishing between real and fake job postings has become increasingly difficult. Scammers often mimic legitimate job advertisements — using the same platforms such as online job boards, social media, newspapers, and even TV or radio. These fraudulent postings are designed to steal sensitive personal information or money from unsuspecting job seekers.

This project aims to build a machine learning model capable of identifying whether a job posting is real or fake based on its content. By analyzing patterns in text-based and categorical features, the model attempts to detect deceptive indicators and reduce the risk for job applicants.

---

## 🗃️ Dataset

The dataset used in this project is sourced from [Kaggle](https://www.kaggle.com/datasets/amruthjithrajvr/recruitment-scam). 
It includes over 17,000 job listings, both real and fake, along with various features like:

- Job title, location, department
- Company profile, job description, requirements, benefits
- Employment type, experience, education level, etc.
- A `fraudulent` column indicating the label (t= fake, f = real)

---
## 🧼 Data Preparation

The following preprocessing steps were performed in basic data preparation:

1. **Importing the data** using Pandas
2. **Initial EDA**: shape, info, value counts, head/tail of dataset
3. **Handled missing values**:
   - Dropped `salary_range` column due to >80% missing
   - Filled missing values in other columns with placeholders like `"Other"`, `"Not specified"`, or `"Unknown"` <br>
4. **Cleaned text columns** that had html tags and links using '"BeautifulSoup"' and Regular Expressions.
   5. **checked for class imbalance** — that will be handled in the next step

You can find the complete preprocessing code in the notebook [here](https://github.com/cheta-nyadav/fake-job-prediction/blob/main/Data%20Preparation.ipynb)

---
## ⚖️ Class Imbalance Handling

The dataset was highly imbalanced, with ~95% real jobs and only ~5% fake. This skews model performance, making it biased toward predicting all jobs as real. 

To address this, we used *Random Undersampling*, which balances the data by randomly reducing the majority class to match the minority class.
Though it discards some data, it's a fast and effective method. This gave us a balanced dataset, ready for model training.


---
## 📊 Exploratory Data Analysis (EDA)

We conducted exploratory analysis to understand patterns in job titles, categories, and text features that could indicate fraudulent postings.

Key steps included:

- Reviewing class distribution (post-undersampling)
- Identifying the most frequent job titles overall and among fake postings
- Analyzing key categorical features like `employment_type`, `required_experience`, and `industry`
- Creating a combined `text` column to consolidate multiple textual fields (`description`, `requirements`, etc.) for wordcloud

---

