# Data-Science-for-bus-app-Project
# Smart Discount Optimization Using Uplift Modeling

## 1. Project Overview

This project focuses on helping businesses make better decisions when giving discounts to customers. Instead of sending discounts to everyone, we want to find out which customers are more likely to buy something because they received a discount.

We are using the Hillstrom Marketing Dataset, which contains information about customers and three promotional groups: Discount, Buy One Get One (BOGO), and No Offer.

Our goal is to understand customer purchasing behavior and use uplift modeling to help businesses avoid unnecessary discounts and improve their marketing strategies.

## 2. Business Problem

Many businesses offer discounts to customers without knowing whether those customers would have purchased anyway. This could lead to unnecessary spending and lower profits.

**Our main business question is:**

Which customers are more likely to purchase because they receive a discount compared with receiving no promotional offer?

**Our objectives are to:**

- Understand how customers respond to different promotions.
- Compare the conversion rates of Discount, BOGO, and No Offer.
- Identify customers who may benefit from receiving discounts.
- Reduce unnecessary promotional spending.
- Use machine learning to support better marketing decisions.

## 3. Dataset Information

We used the **Hillstrom Marketing Dataset**, originally published by Kevin Hillstrom.

Dataset reference: [Demo Uplift Modeling in Marketing — Kaggle](https://www.kaggle.com/code/maianhdang/demo-uplift-modeling-in-marketing)

The original dataset contains **64,000 rows and 9 columns**.

| Column          | Meaning                                           |
| --------------- | ------------------------------------------------- |
| `recency`       | How many months since the customer last purchased |
| `history`       | How much the customer spent in the past           |
| `used_discount` | Whether the customer used a discount before       |
| `used_bogo`     | Whether the customer used BOGO before             |
| `zip_code`      | Customer location category                        |
| `is_referral`   | Whether the customer came through a referral      |
| `channel`       | Shopping channel used by the customer             |
| `offer`         | Type of promotion the customer received           |
| `conversion`    | Whether the customer purchased or not             |

The dataset contains three promotional groups:

| Offer    | Customers |
| -------- | --------: |
| Discount |    21,307 |
| BOGO     |    21,387 |
| No Offer |    21,306 |

**Dataset versions**

For our project, we worked with different versions of the data.

- **Original dataset:** The dataset before we made any changes.
- **Messy dataset:** We intentionally added missing values, invalid values, inconsistent formats, and extreme spending values to practice data cleaning.

The original dataset was used for the EDA graphs currently saved in our notebook.

**Dataset licence:** To be confirmed from the original source.

## 4. Project Methodology

We followed the CRISP-DM methodology, which helps organize a data science project into different stages.

1. **Business Understanding:** Identify the business problem and what we want to achieve.
2. **Data Understanding:** Explore the dataset and check for problems.
3. **Data Preparation:** Clean the data and create useful features.
4. **Modeling:** Build machine learning models.
5. **Evaluation:** Check how well the models perform.
6. **Deployment:** Create a Streamlit application to show the results.

## 5. Milestone 3 — Data Preparation

### 5.1 Data Cleaning

We checked the messy dataset for missing values, incorrect data types, invalid values, duplicates, and outliers.

During cleaning, we:

- Corrected incorrect data types and spelling mistakes.
- Changed invalid values into missing values.
- Used the median to fill missing numerical values.
- Used the mode to fill missing categorical and binary values.
- Kept duplicate-looking rows because the dataset does not have a unique customer ID.
- Capped the 10 artificially introduced extreme spending values at $3,345.93.

**Cleaning Results**

| Check            | Before cleaning | After cleaning |
| ---------------- | --------------: | -------------: |
| Total rows       |          64,000 |         64,000 |
| Missing values   |             112 |              0 |
| Duplicate rows   |           6,583 |          6,598 |
| Maximum spending |         $25,000 |      $3,345.93 |

The IQR method identified 3,599 possible spending outliers. However, we did not remove all of them because some customers may genuinely spend more than others.

We only capped the 10 extreme values that we intentionally added to the messy dataset.

### 5.2 Exploratory Data Analysis (EDA)

We created different graphs to understand customer purchasing behavior and compare promotional offers.

Our graphs included:

- Conversion rates by promotional offer.
- Conversion rates by shopping channel.
- Historical spending distribution.
- Historical spending compared with conversion.
- Conversion rates based on recency.
- Conversion rates based on previous Discount and BOGO usage.

**Main Results**

| Offer    | Conversion Rate |
| -------- | --------------: |
| Discount |          18.28% |
| BOGO     |          15.14% |
| No Offer |          10.62% |

The Discount group had the highest conversion rate, while the No Offer group had the lowest.

We also noticed that customers who purchased more recently generally had higher conversion rates.

These results help us understand customer behavior, but we still need uplift modeling to estimate which customers actually benefit from receiving discounts.

### 5.3 Feature Engineering

We created three new features to make the data more useful for future machine learning.

| New Feature       | Meaning                                                                       |
| ----------------- | ----------------------------------------------------------------------------- |
| `recent_customer` | Shows whether a customer purchased within the last three months               |
| `used_any_promo`  | Shows whether a customer used Discount or BOGO before                         |
| `history_log`     | Changes historical spending values to reduce the effect of very high spending |

These features may help us understand customer behavior and improve our future models.

## 6. Uplift Modeling — Next Stage

In Milestone 4, we plan to start building uplift models.

Normal machine learning models predict whether a customer is likely to purchase.

Uplift modeling focuses on estimating whether a customer is more likely to purchase **because they received a promotion**.

We plan to compare different machine learning models and investigate a T-Learner approach.

The goal is to help BrightMart decide which customers should receive discounts and which customers may purchase without them.

**Status:** Modeling has not been completed yet.

## 7. Tools Used

| Tool                   | Purpose                                 |
| ---------------------- | --------------------------------------- |
| Python                 | Data cleaning and analysis              |
| Pandas                 | Working with datasets                   |
| NumPy                  | Numerical calculations                  |
| Matplotlib and Seaborn | Creating graphs                         |
| Scikit-learn           | Data preprocessing and machine learning |
| SciPy                  | Statistical analysis                    |
| Google Colab           | Writing and running Python code         |
| GitHub                 | Storing and organizing project files    |

## 8. Repository Structure

Our GitHub repository is organized into folders to make the project easier to understand.

```text
Smart-Discount-Optimization/
│
├── DataSets/
│   ├── README.md
│   ├── brightmart messy dataset.csv
│   └── data.csv
│
├── Docs/
│   ├── Data Dictionary.docx
│   ├── dataset_search_evidence.docx
│   └── read
│
├── Notebooks/
│   ├── 01__data_understanding.ipynb
│   ├── 02__data_cleaning.ipynb
│   ├── 03__exploratory_data_analysis.ipynb
│   ├── 04_Feature_Engineering.ipynb
│   └── UPDATED-03_exploratory_data_...
│
└── README.md
```

The `DataSets` folder contains the datasets used in the project.

The `Docs` folder contains the data dictionary and dataset search evidence.

The `Notebooks` folder contains our Python code for data understanding, cleaning, EDA, and feature engineering.

The final notebook filename shown above is shortened and should be replaced with its complete filename.

## 9. How to Run the Code

To run the project:

1. Download the GitHub repository.
2. Open the Python notebooks in Google Colab or Jupyter Notebook.
3. Install the required libraries using `pip install -r requirements.txt` once the file is added.
4. Make sure the dataset file paths are correct.
5. Run the notebooks in order, starting with data understanding.
6. Check the outputs and graphs.

## 10. Team Members and Contributions

| Team Member               | Contribution                |
| ------------------------- | --------------------------- |
| Shaikha Ali               | Worked on Milestone 1 (Business Problem Formulation), cleaned the dataset using Python, created EDA charts, and completed the first part of feature engineering. also organized and formatted the Word report and created and set up the GitHub repository. |
| Mona Asghar               | Worked on Milestone 2 (Dataset Selection and Validation), created the messy dataset by adding data quality issues, and uploaded the datasets. also created EDA charts and completed the remaining part of feature engineering |

## 11. Project Progress

| Project Stage          | Status      |
| ---------------------- | ----------- |
| Business Understanding | Completed   |
| Dataset Selection      | Completed   |
| Data Understanding     | Completed   |
| Data Cleaning          | Completed   |
| EDA                    | Completed   |
| Feature Engineering    | Completed   |
| Uplift Modeling        | Not started |
| Model Evaluation       | Not started |
| Streamlit Application  | Not started |

## 12. Expected Business Value

We hope this project will help businesses make better decisions about promotional offers.

By understanding which customers may respond positively to discounts, businesses could reduce unnecessary promotional spending and improve marketing efficiency.

In the next milestones, we will use machine learning to investigate whether more targeted promotions could provide better results than sending discounts to everyone.

## 13. Streamlit Application

The Streamlit application will be developed in Milestone 5.

**Live App:** Coming soon.

## 14. AI Tools Used

We used ChatGPT to help with understanding Python code, debugging, explaining data cleaning methods, and organizing project documentation.



## 15. Project Information

**Project:** Smart Discount Optimization Using Uplift Modeling

**Course:** Data Science for Business Application (CDS4003)

**Methodology:** CRISP-DM

**Current Progress:** Milestones 1, 2, and 3
