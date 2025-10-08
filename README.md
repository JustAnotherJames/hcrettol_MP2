# MP2 OSS Activity Analysis

### Overall research objective: Study commit patterns over time for   10 scientific software projects.

$${\color{red} WoC \space Server \space  fixed!\space  Notebook\space  updated }$$

### Work schedule
- Part 1: (Due Oct 9) Retrieve all commits and associated data for
each of the 10 projects
- Part 2: (Due Oct 16) Plot (and describe) commit trends over time for each project
- Part 3: (Due Oct 23)  Investigate trends for large gaps, discontinued
contributions, and other anomalies and report topics of commits
before and after the gap
- Part 4: (Due  Oct 30) Based on all available evidence make a
judgment about the reasons for the gap or discontinued contribution
and reasons for restarted contributions (if any)



- If you run requests in a loop, make sure the chunks are under 50
  commits and include some waits between the subsequent requests 
- You'll find the list of 10 projects in [net2prj.csv](https://github.com/fdac25/MP2/blob/main/net2prj.csv): your assigned projects
  are marked with your netid. Each row has a netid, WOCProjectID, and GitHubURL (project repository link)
- Example [Notebook](https://github.com/fdac25/MP2/blob/main/getinfo.ipynb) is provided for you modify in order to retrieve data for your projects.
- More info on obtaining the data from WoC: [API Docs](https://worldofcode.org/docs/#/guide_remote?id=task-4-batching)
  

### Notes

Recall the lecture about data retrieval:

a) what kind of source is worldofcode.org?

b) pay attention to how many commits you are getting, check for
errors

c) you may need to get an API key if the throughput is not
sufficient

d) you may need to retrieve commit sha1's first, then get commit
content in batches

e) validation: does the number of commits or authors match that on GH?

f) WoC data is up to Jan 2025, so there may be some projects with
later commits on GH 

### Part 1 Steps

1. Fork fdac25/MP2
2. Create retrieval notbook copy (rename to yournetid.ipynb)
3. Edit/run your copy using google collab notebooks and save the
output in your fork
4. For each of the 10 projects go to their github repo and get
   the number of stars, number of forks, and the last commit date
5. Report (in your notebook) the number of commits, the number of authors, and max and
min time for each project based on WoC commits and also add the info
you obtained from github
6. Create a CSV file in your fork named netid_project_summary.csv
that is semicolon separated and containing the following columns:
```
project_wocid
commit_sha1
author
time
commit message
```

### Extra credit: obtain the same data (in addition to WoC data) on each commit from github and store in netid_project_summary_gh.csv

### Part 2 steps: data visualization

Visualize the commit timestamps you obtain in Task 1. Steps:

1. Group activity by month. Each row should represent one month, with the number of commits made during that month.
2. Even if a month had zero commits, still include it with a 0
count.
3. Begin with the first month in which the project had any commit.
4. End with the last month in which the project had a commit.
5. Save this as:  Filename: netid_commits_timeseries_<WOCProjectID>.csv
```
Columns/Format: Month;Commits
Example rows:
2021-01;5
2021-02;0
2021-03;2
```
6. Create a line plot of the time series in Python. The plot should use the monthly data you just generated.
```
Plot Format:
X-axis = months (YYYY-MM)
Y-axis = number of commits
Title = WOCProjectID
Add axis labels and grid lines
Save the plot as: netid_timeseries_<WOCProjectID>.png
Export resolution: ≥300 DPI
```
Example code:
```
import pandas as pd
import matplotlib.pyplot as plt

# Load CSV
df = pd.read_csv("netid_commits_timeseries_<WOCProjectID>.csv", sep=";")

# Plot
plt.figure(figsize=(10,5))
plt.plot(df["Month"], df["Commits"], marker="o", linestyle="-")
plt.xlabel("Time (YYYY-MM)")
plt.ylabel("Number of Commits")
plt.title("Commit Activity: <WOCProjectID>")
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()

# Save; Resolution 300 DPI
plt.savefig("netid_timeseries_<WOCProjectID>.png", dpi=300)
plt.close()
```


##### Identify the Longest Inactivity Gap
Using your monthly time series, determine the longest continuous period of zero commits.
To calculate:
1. Start in the first month with zero commits.
2. Count consecutive zero-commit months.
3. Track the maximum length.
4. Create netid_project_stats.csv with columns project, the number of commits, the number of authors, and max and
min time for each project based on WoC commits and also add the info
you obtained from github. In addition, add
```
LongestGapStart (YYYY-MM), 
LongestGapEnd (YYYY-MM),
LongestGapLength (months).
```
5. Count total commits to date after the LongestGapEnd. Add another
column to netid_project_stats.csv: NumCommitsAfterLastGap
6. Provide a concise classification of the project’s overall
   activity trajectory based on the charts you have produced your overall perception. Record this
   in netid_project_stats.csv: ActivityPattern (choose from:
   steady, rising, declining, U-shaped, stopped, cyclical, irregular). 
7. In the notebook, in the cell "Interpretation", add explanation for the trnds you
   noted. See the definitions below. Also specify the number of gaps
   (of at least three months of inactivity) are there for each project.

Trends: steady, declining, rising, U-shaped: Long-term, general
movements in activity levels. An upward trend might indicate that a
person is becoming more active over several months, while a downward
trend could signal a decrease in mobility.

Seasonal/Cyclical patterns: Predictable and repeated patterns of activity
that occur at fixed intervals, such as quarterly or
annually. 

Irregular or random variations: Unpredictable changes in activity
that cannot be explained by trends or seasonal patterns.

[Example Notebook](https://github.com/fdac25/MP2/blob/main/Vis.ipynb)
## Part 3-4 details: TBD

