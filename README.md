# 🧠 Analyzing Students' Mental Health

> **Does studying abroad affect your mental health?**  
> This project explores that question using real survey data from a Japanese international university — analyzed with PostgreSQL and visualized with Python (Plotly).

---

## 📌 Project Overview

A Japanese international university surveyed its students in 2018 and published the findings in 2019, approved by multiple ethical and regulatory boards. The original study found that:

- International students face a **higher risk of mental health difficulties** than the general population
- **Social connectedness** and **acculturative stress** are key predictors of depression

This project replicates and extends that analysis using SQL and Python to examine whether **length of stay** is also a contributing factor.

---

## 📂 Dataset

- **Source:** Japanese International University Student Survey (2018)
- **Total Records:** 286 students
- **Subset Analyzed:** 201 international students

### Column Reference

| Field | Description |
|-------|-------------|
| `inter_dom` | Type of student — International or Domestic |
| `japanese_cate` | Japanese language proficiency level |
| `english_cate` | English language proficiency level |
| `academic` | Academic level — Undergraduate or Graduate |
| `age` | Current age of the student |
| `stay` | Length of stay in Japan (years) |
| `todep` | Total depression score (PHQ-9 test) |
| `tosc` | Total social connectedness score (SCS test) |
| `toas` | Total acculturative stress score (ASISS test) |

---

## ❓ Key Questions Answered

1. Do international students with longer stays show higher depression scores?
2. Does lower social connectedness correlate with higher depression?
3. Does higher acculturative stress correlate with higher depression?

---

## 📊 Key Findings

| Stay (Years) | No. of Students | Avg Depression (PHQ-9) | Avg Social Connectedness | Avg Acculturative Stress |
|:---:|:---:|:---:|:---:|:---:|
| 1 | 95 | 7.48 | 38.11 | 72.80 |
| 2 | 39 | 8.28 | 37.08 | 77.67 |
| 3 | 46 | 9.09 | 37.13 | 78.00 |
| 4 | 14 | 8.57 | 33.93 | 87.71 |
| 6 | 3 | 6.00 | 38.00 | 58.67 |
| 7 | 1 | 4.00 | 48.00 | 45.00 |
| 8 | 1 | 10.00 | 44.00 | 65.00 |
| 10 | 1 | 13.00 | 32.00 | 50.00 |

> ⚠️ *Groups with stay = 5, 7, 8, and 10 years contain only 1 student each — results for these groups should be interpreted with caution due to very small sample sizes.*

### 🔍 Insights

- **Longer stays tend to correlate with higher depression scores** — students staying 10 years averaged a PHQ-9 score of 13, compared to 7.48 for first-year students, suggesting cumulative psychological strain over time.
- **Social connectedness is negatively correlated with depression** — students with higher SCS scores consistently show lower PHQ-9 depression scores, confirming the original study's findings.
- **Acculturative stress is positively correlated with depression** — students experiencing greater difficulty adjusting to Japanese culture show higher depression scores, further validating the 2019 research.
- **Length of stay appears to be a contributing factor** to mental health outcomes among international students.

---

## 🛠️ Tools & Technologies

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-239120?style=for-the-badge&logo=plotly&logoColor=white)

- **PostgreSQL** — Data querying, aggregation, and filtering
- **Python (Pandas)** — Data manipulation
- **Plotly Express** — Interactive visualizations

---

## 📈 Visualizations

The project includes three visualizations:

1. **Bar Chart** — Average Depression Score (PHQ-9) by Length of Stay<img width="1400" height="1000" alt="DataLab plot" src="https://github.com/user-attachments/assets/89d646c6-4736-4fe3-8e57-6ea6970a38a7" />

2. **Scatter Plot** — Social Connectedness Score vs. Depression Score (with OLS trendline)<img width="1400" height="1000" alt="DataLab plot" src="https://github.com/user-attachments/assets/afa59daf-c4f7-44bc-818f-98675bf24c8f" />

3. **Scatter Plot** — Acculturative Stress Score vs. Depression Score (with OLS trendline)<img width="1400" height="1000" alt="DataLab plot" src="https://github.com/user-attachments/assets/afb1af26-3979-4f20-916e-cf7d94a420ce" />


---

## 💻 SQL Highlight

```sql
SELECT stay,
       COUNT(*) AS count_int,
       ROUND(AVG(todep), 2) AS average_phq,
       ROUND(AVG(tosc), 2) AS average_scs,
       ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
```

---

## 🚀 How to Run

1. Clone the repository
   ```bash
   git clone https://github.com/vedanshusingh/students-mental-health-sql-analysis.git
   ```
2. Load the `students` dataset into your PostgreSQL instance
3. Run the SQL queries in sequence as shown in the notebook
4. Execute the Python cells to reproduce the visualizations

---

## 📁 Repository Structure

```
students-mental-health-sql-analysis/
│
├── notebook.ipynb        # Main analysis notebook
├── README.md             # Project documentation
└── data/
    └── students.csv      # Raw dataset 
```

---

## 🔗 References

- Original Study: *Mental Health of International University Students — Japanese University Survey (2019)*
- PHQ-9 (Patient Health Questionnaire): Depression screening tool
- SCS (Social Connectedness Scale): Measures sense of belonging
- ASISS (Acculturative Stress Inventory for International Students): Measures cultural adjustment stress

---

## 👤 Author

**Vedanshu Singh**  
 Data Analyst  
📧 vedanshus.work@gmail.com  
🔗 [GitHub](https://github.com/vedanshusingh)

---

*This project was completed as part of the DataCamp DataLab curriculum.*
