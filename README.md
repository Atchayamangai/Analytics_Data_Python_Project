# Overview

Welcome to my analysis of the data job market, focusing on data analyst roles. This project was created out of a desire to navigate and understand the job market more effectively. It delves into the top-paying and in-demand skills to help find optimal job opportunities for data analysts.

The data sourced from Luke Barousse's Python Course which provide a foundation for my analysis, containing detailed information on job titles, salaries, locations, and essential skills. Through a series of Python script. i explore key questions such as the most demanded skills, salary trends, and the intersection of demand and salary in data analytics.

# The Questions

Below are the questions I want to answer in my project:

    1.What are the skills most demand for the top3 most popular data roles?
    2.How are in-demand skills trending for Data Analyst?
    3.How well do jobs and skills pay for Data Analysts?
    4.What are the optimal skills for data analysts to learn? (High Demand and High Paying)

# Tools I Used

For my deep dive into the data analysts job market, I harnessed the power of several key tools:

- **Pthon:** The backbone of my analysis, allowing me to analyze the data and find critical insights. I also used the following Python libraries:
   - **Pandas Library:** This was used to analyze the data.
   - **Matplotlib Library:** I visualized the data.
   - **Seaborn Library"** Helped me create more advanced visuals.
- **Jupyter Notebooks:** The tool I used to run my Python scripts which let me easily include my notes and analysis.
- **Visual Studio code:** My go-to for executing my Python scripts.
- **Git & GitHub:** Essential for version control and sharing my Python code and analysis, ensuring collaboration and Analysis.
  
# Data Preparation and Cleanup

This section outlines the steps taken to prepare the data for analysis, ensuring accuracy and usability.

# Import & Clean Up Data

I start by importing necessary libraries and loading the dataset, followed by initial data cleaning tasks to ensure data Analalysis.

# The Analysis

Each Jupyter notebook for this project aimed at investigating specific aspects of the data job market. Here's how I approached each question:

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role i'm targeting.

View my notebook with detailed steps here : [2_Skill_Demand.ipynb](Project\2_Skill_Demand.ipynb)

### Visualize Data

```python
fig, ax = plt.subplots(len(job_titles), 1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_count[df_skills_count["job_title_short"] == job_title].head(5)
    df_plot.plot(kind="barh", x='job_skills', y='skill_count', ax=ax[i], title=job_title)
    ax[i].invert_yaxis()
    ax[i].set_ylabel('')
    ax[i].legend().set_visible(False)

fig.suptitle('Counts of Top Skills in Job Postings', fontsize=15)    
fig.tight_layout(h_pad=0.5)  # fix the overlap

plt.show()
```
### Results

![Visualization of Top Skills for Data Nerds](images/skill_demand_data_roles.png)


### Insights

- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientist (72%) and Data Engineers (65%).
- SQL is the most requested skill for Data Analysts and Data Scientist, with it in over half the job postings for both roles. For Data Engineers, Python is the most sought-after skill appearing in 68% of job postings.
- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).


 # The Analysis

 ## 2. How are in-demand skills trending for Data Analysts?

 ### Visualize Data

 ```python

 from matplotlib.ticker import PercentFormatter

df_plot = df_DA_US_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, legend='full', palette='tab10')

plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()

```
### Results

![Trending Top Skills for Data Analysts in the US](Project\images\DA_skill_trend.png)
  
  *Bar graph visualizing the trending top skills for data analysts in the US in 2023.*

### Insights

- SQL remains the most consistently demanded skill throughout the year, although it shows a gradual decrease in demand.
- Excel experienced a significant increase in demand starting around September, surpassing both python and tableaue by the end of the year.
- Both python and Tableaue show relatively stable demand throughout the year with some fluctuations but remain essential skills for data analysts.
- Power BI, while less demanded compared to the others, shows a slight upward trend towards the year's end.

# The Analysis

## 3. How well do jobs and skills pay for Data Analysts?

### Salary Analysis for Data Nerds?

### Visualize Data
```python
sns.boxplot(data=df_US_top6, x="salary_year_avg", y="job_title_short", order=job_order)

sns.set_theme(style='ticks')

plt.title('Salary Distributions in the United States')
plt.xlabel('Yearly Salary (USD)')
plt.ylabel('')
plt.xlim(0, 600000)

ticks_x = plt.FuncFormatter(lambda y, pos: f'${int(y/1000)}k')

plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()

```

#### Results 

![Salary Distributions of Data Jobs in the US](Project\images\salary_analysis_for_data_roles.png)
*Box plot visualizing the salary distributions for the top 6 data job titles.*

#### Insights

Senior Data Scientist:

- Highest median salary of all roles, near $150k.
Wide distribution of salaries, with outliers extending beyond $500k.
Concentration of salaries between $100k and $250k.

Senior Data Engineer:

- Similar salary distribution to Senior Data Scientist but slightly lower.
Median salary around $140k.
Many outliers, some above $400k, indicating high variability.

Data Scientist:

- Median salary around $120k.
Narrower range compared to senior roles, but outliers still reaching beyond $300k.
Many salaries between $100k and $200k.

Data Engineer:

- Similar salary to Data Scientist, with a median close to $120k.
Smaller number of outliers compared to Senior roles, but still noticeable above $300k.

Senior Data Analyst:

- Lower median salary compared to senior engineering/scientist roles, around $110k.
Salaries generally distributed between $90k and $150k.
Fewer outliers compared to other roles.

Data Analyst:

- Lowest median salary, around $80k.
Narrower salary range with most values falling between $60k and $100k.
Outliers present but not as high as in other roles, with few above $150k.

### Highest Paid & Most Demanded Skills for Data

### Visualize Data

```python

fig, ax =  plt.subplots(2, 1)

# Top 10 Highest Paid Skills for Data Analyst
sns.barplot(data=df_DA_top_pay, x='median', y=df_DA_top_pay.index, hue='median', ax=ax[0], palette='dark:b_r')

# Top 10 Most In-Demand Skills for Data Analyst
sns.barplot(data=df_DA_skills, x='median', y=df_DA_skills.index, hue='median', ax=ax[1], palette='light:b')

plt.show()

```

### Results

Here's the breakdown highest-paid  & Most in-demand skills for data analysts in the US:

![The Highest Paid & Most In-Demand Skills for Data Analysts in the us](Project\images\skill_analysis_highest_paid.png)
*Two separate bar graph visualizing the highest paid skills and most in-demand skills for data analysts in the US.*

### Insights

**Top 10 Highest Paid Skills for Data Analysts:**

- The highest-paid skill is `dplyr`, a tool commonly used in data manipulation in `R`, followed by `bitbucket` and `gitlab`, which are version control and collaboration platforms.
- Skills related to blockchain and machine learning, such as solidity (used in Ethereum development) and hugging face (a library for natural language processing), also command high salaries.
- Technologies for containerization (ansible) and distributed databases (couchbase, cassandra) are well compensated.
- These skills often correspond to more specialized or technical domains, which may explain the higher median salaries.

**Top 10 Most In-Demand Skills for Data Analysts:**

- `Python` tops the list as the most sought-after skill, reflecting its widespread use in data analysis, machine learning, and automation.
- `Tableau` and `Power BI` indicate a strong demand for data visualization tools, essential for communicating insights effectively.
- Traditional database management skills like `SQL Server`, `SQL`, and `SAS` are still highly demanded, as they form the backbone of data storage and processing.
- Tools like `PowerPoint` and `Excel` appear as lower-paying, yet still essential, especially for data presentation.

# The Analysis

## 4. What is the most optimal skill to learn for Data Analyst?

### Visualize Data

```python

from adjustText import adjust_text
import matplotlib.pyplot

plt.scatter(df_DA_skills_high_demand["skill_percent"], df_DA_skills_high_demand["median_salary"])
plt.show()

```
### Results

![Most Optimal Skills for Data Analysts in the US](Project\pictures\optimal_skills.png)
*A scatter plot visualizing the most optimal skills (high paying & high demand) for data analysts in the US.*

### Insights

**Programming (Blue Dots):**

- These include skills like `Python`, `Go`, and `SAS`.
- `Python` is highly prevalent (around 40% of jobs) with a median salary just below $90k, indicating its wide demand and relatively strong pay.
- `Go` is less common, appearing in only about 10% of jobs, but offers a competitive salary near $90k.
- `SAS` and R offer slightly lower salaries but are still valued in a decent portion of the market.
   
**Analyst Tools (Orange Dots):**

- These include `Power BI`, `Tableau`, `Looker`, `PowerPoint`, and `Excel`.
- `Tableau` and `Power BI` appear in about 30% of job listings, offering salaries around $85k-$90k.
Looker and PowerPoint offer lower prevalence and salaries.
- `Excel` is present in nearly 40% of jobs but has a lower salary compared to more specialized tools.
Word and PowerPoint are widely used but less compensated, reflecting their more general business application.

**Cloud (Green Dots):**

- `Azure` and `AWS` are both cloud technologies used in data infrastructure.
- Both skills offer competitive salaries above $90k, with AWS being slightly more prevalent than Azure.
  
**Databases (Purple Dots):**
  
- `SQL`, `SQL Server`, and `Oracle`.
- `SQL` is the most in-demand skill, appearing in over 50% of job listings. Despite its high prevalence, its salary is competitive but not the highest.
- `SQL Server` and Oracle appear in around 20% of listings, offering salaries just below $90k.

- # What I Learned

Throughout this project, I deepened my understanding of the data analyst job market and enhanced my technical skills in Python, especially in data manipulation and visualization. Here are a few specific things I learned:
  - **Advanced Python Usage:** Utilizing libraries such as Pandas for data manipulation, Seaborn and Matplotlib for data visualization, and other libraries helped me perform complex data analysis tasks more efficiently.
  - **Data Cleaning Importance:** I learned that thorough data cleaning and preparation are crucial before any analysis can be conducted, ensuring the accuracy of insights derived from the data.
  - **Strategic Skill Analysis:** The project emphasized the importance of aligning one's skills with market demand. Understanding the relationship between skill demand, salary, and job availability allows for more strategic career planning in the tech industry.

# Insights

This project provided several general insights into the data job market for analysts:

  - **Skill Demand and Salary Correlation:** There is a clear correlation between the demand for specific skills and the salaries these skills command. Anvanced and specialized skills like Python and Oracle often lead to higher salaries.
  - **Market Trends:** There are changing trends in skill demand, highlighting the dynamic nature of the data job market. Keeing up with these trends is essential for career growth in data analytics.
  - **Economic Value of Skilss:** Understandingwhich skills are both in-demand and well-compensated can guide data analysts in prioritizing learning to maximize their economic returns.
  
# Challenges I Faced

This project was not without its challenges, but it provided good learning opportunities.

  - **Data Inconsistencies:** Handling missing or inconsistend data entries requires careful consideration and thorough techniques to ensure the integrity of the analysis.
  - **Complex Data Visualization:** Designing effective visual representations of complex datasets was challenging conveying insights clearly and compellingly.
  - **Balancing Breadth and Depth:** Deciding how deeply to dive into each analysis while maintaining a broad over ilanscape required constant balancing to ensure comprehensive coverage without getting lost in details.
  
# Conclusion

This exploration into the data analyst job market has been incredibly informative, highlighting the critical skills and trends that shape this evolving field. The insights I got enhance my understanding and provide actionable guidance for anyone looking to advance their career in data analysics. As the market continues to change, ongoing analysis will be essential to stay ahead in data analytics. This project is a good foundation for future explorations and underscores the importance of continuous learning and adaptation in the data field.



