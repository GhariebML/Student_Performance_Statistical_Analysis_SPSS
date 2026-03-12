# Statistical Analysis of Student Performance Using SPSS

![SPSS](https://img.shields.io/badge/IBM%20SPSS-Statistics%20v29-blue?style=flat-square)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Course](https://img.shields.io/badge/Course-Applied%20Statistics%20%26%20Data%20Analysis-orange?style=flat-square)

> **Course:** Applied Statistics and Data Analysis | MTC — Assignment 01  
> **Supervised by:** Dr. Noha Nabawy  
> **Date:** March 10, 2026

---

## 📋 Project Overview

A complete statistical analysis report of a **student performance dataset (n=20)** using **IBM SPSS Statistics v29**. The analysis covers the full data science pipeline: data preparation, outlier detection, descriptive statistics, inferential testing, and correlation analysis — with the aim of understanding the relationships between **gender, study hours, GPA, and attendance**.

---

## 🎯 Objectives

- Prepare the dataset: recode string variables, handle missing data, detect and treat outliers
- Compute descriptive statistics for StudyHours, GPA, and Attendance — disaggregated by gender
- Test whether GPA differs significantly between male and female students (independent-samples t-test)
- Quantify the linear association between weekly study hours and GPA (Pearson correlation)
- Present findings through professional tables and embedded SPSS output charts

---

## 📊 Dataset Description

| Variable | Type | Description | Scale |
|----------|------|-------------|-------|
| ID | Numeric | Unique student identifier | Nominal |
| Gender | String → Recoded | Student gender (Male/Female) | Nominal |
| StudyHours | Numeric | Weekly hours devoted to studying | Ratio |
| GPA | Numeric | Grade Point Average (0.0–4.0) | Ratio |
| Attendance | Numeric | Class attendance percentage (0–100) | Ratio |

---

## 🔍 Key Findings at a Glance

| Finding | Result | Statistical Status |
|---------|--------|--------------------|
| Missing GPA values | 1 of 20 (5%) | Excluded via listwise deletion |
| Outlier — Study Hours | Case 19: 200 hrs/week | Filtered — sensitivity analysis run |
| Female mean GPA | 3.41 | Slightly higher than males |
| Male mean GPA | 3.12 | Not significantly different |
| GPA gender difference | t(16) = -1.44, p = .170 | **Not statistically significant** |
| Study Hours vs. GPA | r = .876, p < .001 | **Strong positive correlation** |

> 📌 **Key Takeaway:** Study effort is a strong predictor of GPA, while gender differences are **not** statistically significant in this sample.

---

## 🛠️ Analysis Pipeline

### 1️⃣ Data Preparation
- Recoded string `Gender` variable to numeric using SPSS syntax (`RECODE`)
- Identified 1 system-missing GPA value (5%) — applied **listwise deletion**
- Retained all other variables for the missing case

### 2️⃣ Outlier Detection — StudyHours
- Detected extreme outlier: **Case 19 (Male) — 200 hrs/week** via Boxplot & Stem-and-Leaf plots
- Outlier inflated male mean from **13.0 → 31.7 hrs** and SD from **7.4 → 59.5** (706% inflation)
- Applied sensitivity filter: `StudyHours < 50` → N reduced to 19

### 3️⃣ Descriptive Statistics (Filtered, N=19)

| Variable | N | Min | Max | Mean | Std. Dev |
|----------|---|-----|-----|------|----------|
| StudyHours | 19 | 7 | 30 | 13.21 | 5.308 |
| GPA | 18 | 2.5 | 4.0 | 3.267 | 0.4393 |
| Attendance | 18 | 65 | 98 | 83.94 | 9.334 |

### 4️⃣ Independent-Samples t-Test (GPA by Gender)

**Hypotheses:**
- H₀: No significant difference in mean GPA between males and females
- H₁: Significant difference exists (α = .05, two-tailed)

**Results:**

| Group | N | Mean GPA | Std. Dev |
|-------|---|----------|----------|
| Male | 9 | 3.122 | 0.4969 |
| Female | 9 | 3.411 | 0.3408 |

- **Levene's Test:** F = 0.970, p = .339 → Equal variances assumed
- **t-Test:** t(16) = -1.44, p = .170 → **Fail to reject H₀**
- **Cohen's d = -0.678** → Medium effect size (small sample limits power)

### 5️⃣ Pearson Correlation (StudyHours & GPA)

- **r = .876**, n = 18, **p < .001** (filtered dataset)
- r² ≈ .77 → **~77% of GPA variance explained by study hours**
- Full-dataset scatterplot shows R² = 0.019 — demonstrates severe outlier suppression effect

---

## 📈 SPSS Syntax Used

```spss
# Gender Recoding
RECODE Gender ('Male'=1)('Female'=2) INTO Gendernum.
VARIABLE LABELS Gendernum '1=Male, 2=Female'.
EXECUTE.

# Outlier Filter
COMPUTE filter=StudyHours < 50.
VARIABLE LABELS filter 'StudyHours < 50 FILTER'.
FILTER BY filter.
EXECUTE.
```

---

## 🧰 Tech Stack

| Tool | Purpose |
|------|---------|
| IBM SPSS Statistics v29 | Full statistical analysis platform |
| Descriptive Statistics (EXAMINE) | Mean, SD, Skewness, Boxplots |
| Independent-Samples t-Test | GPA comparison by gender |
| Pearson Correlation (CORRELATIONS) | Study Hours vs. GPA relationship |
| Boxplots & Stem-and-Leaf Plots | Outlier detection & visualization |
| Bar Charts & Scatterplots | Result visualization |

---

## ⚠️ Limitations

- Small sample size (N=20) limits statistical power and generalizability
- One extreme outlier required exclusion, reducing male group to n=9
- Cross-sectional design prevents causal inference
- r=.876 may partly reflect confounds (prior ability, course difficulty)

---

## 📚 References

- IBM Corp. (2023). *IBM SPSS Statistics for Windows, Version 29.0*. Armonk, NY: IBM Corp.
- Cohen, J. (1988). *Statistical Power Analysis for the Behavioral Sciences* (2nd ed.). Lawrence Erlbaum.
- Field, A. (2018). *Discovering Statistics Using IBM SPSS Statistics* (5th ed.). SAGE Publications.
- Tabachnick, B. G., & Fidell, L. S. (2019). *Using Multivariate Statistics* (7th ed.). Pearson.

---

## 👨‍💻 Author

**Mohamed Abd Elsalam Mohamed Gharieb**  
Data Scientist & ML Engineer | IBM & Google Certified  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/ghariebml/)  
[![GitHub](https://img.shields.io/badge/GitHub-GhariebML-black?style=flat-square&logo=github)](https://github.com/GhariebML)

---

*Prepared under supervision of Dr. Noha Nabawy | Applied Statistics and Data Analysis — MTC | March 2026*
