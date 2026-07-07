# Case Study: Manufacturing Defect & Quality Analytics

### 👤 Author
* **Ryan D. Vo** – Cal Poly Pomona Industrial Engineering
* **Project Methodology:** DMAIC (Define, Measure, Analyze, Improve, Control)
* **Dataset Source:** [Kaggle Manufacturing Defects Dataset](https://kaggle.com)

<br>

---

<br>

## 🏢 1. Define & Measure (DMAIC Framework)
In high-volume manufacturing environments like Caterpillar, minimizing defect rates and predicting repair overhead is essential to sustaining lean production lines. 

### 🎯 Project Objectives & Scope:
* **Analyzed 5,000+ defect logs using SQL/Python to map severity and frequency patterns.**
* **Isolated top 2 defects causing 80% of variation using Excel Pareto and Pivot Tables.**
* **Utilized Python (Matplotlib/Seaborn) to track repair costs and prioritize line fixes.**

---

## 🗄️ 2. Data Engineering & Relational SQL Aggregations
To aggregate the data across categorical groups, a relational structure is utilized to evaluate total defect frequencies and extract financial averages. 

```sql
-- Query to map defect distribution and calculate mean repair costs
SELECT 
    defect_type, 
    severity, 
    COUNT(*) AS total_occurrences,
    ROUND(AVG(repair_cost), 2) AS average_repair_cost
FROM quality_logs
GROUP BY defect_type, severity
ORDER BY total_occurrences DESC;
```

---

## 📊 3. Pareto Principle Modeling (Excel Analysis)
*(Placeholder: Paste your Excel Pareto Chart Image Here)*

By building out frequency-based Pivot Tables, an industrial 80/20 Pareto distribution is established. This data configuration isolates the exact defect categories that represent the "vital few" root causes behind 80% of line disruptions.

---

## 🐍 4. Exploratory Data Visualization (Python / Seaborn)
The implementation code below leverages Python's analysis and graphics engines to parse categorical distribution trends and map variation structures:

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# 1. Load data from target environment
df = pd.read_csv("manufacturing_defects.csv")

# 2. Configure global visualization aesthetics
sns.set_theme(style="whitegrid")
plt.figure(figsize=(10, 5))

# 3. Plot Defect Frequencies (Seaborn Countplot)
sns.countplot(
    data=df, 
    x='defect_type', 
    order=df['defect_type'].value_counts().index, 
    palette="viridis"
)
plt.title('Defect Distribution Over Quality Logs')
plt.xlabel('Defect Category Type')
plt.ylabel('Total Incident Count')
plt.xticks(rotation=45)
plt.tight_layout()
plt.savefig('defect_frequency_chart.png')
plt.show()
```
