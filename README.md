# The Analysis

## 1. what are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles, I filtered out those positions by which ones were most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here:
[2_Skills_Count.ipynb](3_Project/2_Skills_Count.ipynb)


### Visualize Data
'''

fig, ax = plt.subplots(len(job_titles),1)
sns.set_theme(style='ticks')
for i,job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    # df_plot.plot(kind = 'barh', x = 'job_skills', y = 'skills_percent',  ax = ax[i], title = job_title)
    sns.barplot(data= df_plot, x = 'skills_percent', y = 'job_skills', hue = 'skill_count', ax = ax[i], palette= 'dark:b_r')
    # ax[i].invert_yaxis()
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].set_title(job_title)
    ax[i].legend().set_visible(False)
    ax[i].set_xlim(0,78)
    
    for n,v in enumerate(df_plot['skills_percent']):
        ax[i].text(v + 1, n, f'{int(v)}%' , va = 'center')
    
    if i != len(job_titles) - 1:
         ax[i].set_xticks([])
    
fig.suptitle('Likelihood of skills requested in Job postings:', fontsize = 15)
fig.tight_layout()
plt.show()

'''

### Results
![Visualization of Top Skills for Data Job](3_Project/Images/Skill_count.png)

### Insights
- Python is a versatile skill, highly demanded across all three roles, but prominently for Data Scientists(72%) and Data Engineers(65%). 

- SQL is the most requested skill for Data Analysts and Data Scientists, with it in over half the job postings for both roles. For Data Engineers, Python is the most sought-after skill, appearing in 68% of the job postings.

- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).