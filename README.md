# MP2 Part1 Data retrieval

### Overall research objective: Study commit patterns over time for   10 scientific software projects.

### Work schedule
- Task 1: (Due Oct 9) Retrieve all commits and associated data for
each of the 10 projects
- Task 2: (Due Oct 16) Plot (and describe) commit trends over time for each project
- Task 3: (Due Oct 23)  Investigate trends for large gaps, discontinued
contributions, and other anomalies and report topics of commits
before and after the gap
- Task 4: (Due  Oct 30) Based on all available evidence make a
judgment about the reasons for the gap or discontinued contribution
and reasons for restarted contributions (if any)

### Task 1 details

$${\color{red} If you retrieve data on more than 50 commits at a time, the server
  may block you and you will need to wait a few minutes befort you
  can send requests$$

- If you run requests in a loop, make sure the chunks are under 50
  commit and include some waits between the subsequent requests 
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

### Steps

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

### Task 2-4 details: TBD
