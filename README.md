# SkillSight: Mapping the Data Analyst Job Market

## 📊 Overview
**SkillSight** is an analytical exploration of the data job market, focusing primarily on **Data Analyst** roles.  
This project was built to better understand how demand and salary correlate across different technical skills, helping aspiring data professionals make informed career choices.

Using data from **Luke Barousse’s Python Course Dataset**, the project examines:
- The most in-demand skills for top data roles  
- Trends in skill popularity over time  
- Salary patterns across different job titles  
- The overlap between high-paying and high-demand skills  

---

## ❓ Key Questions
1. What are the most demanded skills for the top 3 data roles?  
2. How are in-demand skills trending for Data Analysts throughout the year?  
3. Which roles and skills pay the most for Data Analysts?  
4. Which skills are both **high-paying** and **high-demand** (most optimal to learn)?

---

## 🛠️ Tools and Technologies
**Programming Language:** Python  
**Libraries Used:**  
- `pandas` → data manipulation and cleaning  
- `matplotlib` → creating basic visualizations  
- `seaborn` → producing advanced visual insights  
- `ast` → parsing and handling string-based list data  
- `datasets` (Hugging Face) → importing the dataset  

**Environment:**  
- Jupyter Notebooks → iterative analysis and visualization  
- Visual Studio Code → additional script execution  
- Git & GitHub → version control and sharing  

---

## 🧹 Data Preparation
1. **Import & Clean Data**  
   - Loaded dataset using Hugging Face `datasets` API.  
   - Converted dates and parsed list-type columns into usable formats.  
   - Filtered data to focus exclusively on **U.S. job postings**.

2. **Data Cleaning Example**
   ```python
   import ast, pandas as pd
   from datasets import load_dataset

   dataset = load_dataset('lukebarousse/data_jobs')
   df = dataset['train'].to_pandas()
   df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
   df['job_skills'] = df['job_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)
   df_US = df[df['job_country'] == 'United States']
   ```

---

## 📈 Analysis Overview

### 1️⃣ Top Skills by Role
**Goal:** Identify the most in-demand skills for top data roles (Analyst, Engineer, Scientist).  
**Insight:**  
- SQL dominates across Data Analyst and Data Scientist roles.  
- Python is the most required skill for Data Engineers.  
- Cloud tools like AWS and Azure are key differentiators.

---

### 2️⃣ Skill Trends Over Time
**Goal:** Track how demand for key skills changes month-to-month.  
**Insight:**  
- SQL remains consistent but slightly declines by year-end.  
- Excel surges from September onwards.  
- Power BI gains gradual popularity.

---

### 3️⃣ Salary Distribution and Top-Paying Skills
**Goal:** Explore salary differences by job title and skill.  
**Insight:**  
- Senior roles (Data Scientist/Engineer) command the highest pay.  
- Specialized technical skills (Gitlab, dplyr, Bitbucket) yield top salaries.  
- Foundational tools (Excel, SQL) remain most in-demand but offer lower median pay.

---

### 4️⃣ Optimal Skill Identification
**Goal:** Find skills that are both high-demand and high-paying.  
**Insight:**  
- **Oracle**, **Python**, and **Tableau** rank high in both metrics.  
- Programming and database skills cluster toward higher salary regions.  
- Visualization tools balance accessibility and earning potential.

---

## 🧩 Visualization Example
```python
sns.scatterplot(
    data=df_DA_skills_tech_high_demand,
    x='skill_percent',
    y='median_salary',
    hue='technology',
    palette='bright'
)
```

**Output:** A scatter plot showing optimal skills, color-coded by technology type.

---

## 💡 Key Takeaways
- **SQL** remains the backbone of the data analytics profession.  
- **Python** and **Tableau** offer the best mix of demand and salary.  
- Specialized tools like **Oracle** signal high-value niche expertise.  
- Continuous upskilling is essential to stay aligned with evolving trends.

---

## 🧠 What I Learned
- Enhanced data cleaning and transformation techniques using Pandas.  
- Improved visualization clarity with Seaborn and Matplotlib.  
- Understood the practical impact of skill-market alignment in analytics.  

---

## ⚡ Challenges
- Handling incomplete data entries and inconsistent skill formatting.  
- Crafting visuals that balance depth with clarity.  
- Managing notebook complexity while keeping analysis modular.

---

## 🏁 Conclusion
**SkillSight** serves as a comprehensive insight engine into the Data Analyst job market.  
It bridges data-driven understanding with career planning, providing clear, actionable takeaways on what skills truly matter.  
As the industry evolves, this foundation can be extended for real-time trend tracking and broader global analysis.

---

## 📂 Repository Structure
```
SkillSight/
│
├── data/                # Dataset (via Hugging Face)
├── notebooks/
│   ├── 1_Data_Cleanup.ipynb
│   ├── 2_Skill_Demand.ipynb
│   ├── 3_Skills_Trend.ipynb
│   ├── 4_Salary_Analysis.ipynb
│   └── 5_Optimal_Skills.ipynb
├── visuals/             # Graphs and plots
└── README.md
```
