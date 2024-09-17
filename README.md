# The Analysis 

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills i should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here:
[2_Skill_Demand.ipynb](03_Project/02_Skill_Demand.ipynb)

### Visualize Data

```python
fig, ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style="ticks")

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc["job_title_short"] == job_title].head(5)
    sns.barplot(data=df_plot, x="skill_percent", y="job_skills", ax=ax[i], hue="skill_count", palette="dark:b_r")
    ax[i].set_title(job_title)
    ax[i].set_xlabel("")
    ax[i].set_ylabel("")
    ax[i].legend().remove()
    ax[i].set_xlim(0, 80)

    for n, v in enumerate(df_plot["skill_percent"]):
        ax[i].text(v + 2, n, f"{v:.0f}%", va="center")
    if i != len(job_titles) - 1:
        ax[i].set_xticks([])

fig.suptitle("Likelihood of Skills Requested in US Job Posings", fontsize=15)
fig.tight_layout(h_pad=0.5)  # fix the overlap
plt.show()
```

### Results
![Visualization of Top Skills for Data Jobs](03_Project/Images/skill_demand_all_data_roles.png)
*Horizontal bar chart visualizing What are the most demanded skills for the top 3 most popular data roles*

### Insights

`SQL` and `Python` are key skills for all three roles. Each role requires a solid understanding of `SQL`, with `Python` being especially important for `Data Scientists` and `Data Engineers`.

Specialized technologies such as `AWS`, `Azure`, and `Spark` are more relevant for `Data Engineers`, while `Excel` and `Tableau` are more commonly used by `Data Analysts`.

`R` is particularly important for `Data Scientists` who are engaged in more advanced data analysis and statistics.

**Summary:**

Depending on the role, `SQL` and `Python` are of absolute priority. For more advanced roles, such as `Data Engineer` and `Data Scientist`, there is an increasing demand for knowledge of cloud technologies and big data processing tools, such as `AWS`, `Azure`, and `Spark`.


## 2. How are in-demand skills trending for Data Analysts?

This section focused on analyzing Data Analyst job listings across the United States. I filtered and identified the five key skills most frequently required by employers.

To gain deeper insights, I tracked how the demand for these skills fluctuated over the course of the year. This involved examining monthly trends to determine how the prominence of each skill varied from month to month. By doing so, I were able to visualize and understand the seasonal patterns and shifts in demand for specific Data Analyst skills throughout the year.

This analysis not only highlighted which skills are currently in high demand but also provided a temporal perspective on how these demands change, offering valuable insights for job seekers and industry professionals looking to align their skills with market trends.

View my notebook with detailed steps here:
[3_Skill_Trend.ipynb](03_Project/03_Skill_Trend.ipynb)

### Visualize Data

```python
sns.lineplot(data=df_plot, dashes=False, palette="tab10")
sns.set_theme(style="ticks")
sns.despine()

plt.title("Trending Top Skills for Data Analysts in the US")
plt.ylabel("Likelihood in Job Posting")
plt.xlabel("2023")
plt.legend().remove()

ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

for i in range(5):
    plt.text(11.25, df_plot.iloc[-1, i], df_plot.columns[i])
```

### Results
![Trending Top Skills for Data Analysts in the US](03_Project/Images/skills_trend.png)
*Line chart visualizing the trending top skills for data analysts in the US in 2023*

### Insights
tbc.