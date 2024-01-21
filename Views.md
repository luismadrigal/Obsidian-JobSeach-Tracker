
### View for One File with many entries

```dataview
TABLE rows.Lists.text AS Details
FROM #job-search AND !"JobSearch"
WHERE icontains(Platform, "LinkedIn")
FLATTEN file.lists AS Lists
FLATTEN meta(Lists.section).subpath AS Job-Post
GROUP BY Job-Post
WHERE icontains(rows.Lists.text, "Hybrid") or icontains(rows.Lists.text, "Remote")
LIMIT 2
```



### View for files

```dataview
TABLE Title AS "Job Title",
      Employer AS "Company",
      Location AS City,
      Platform AS Website,
      Applied, Posted, Delta, Type,
      Pay AS Compensation,
      Locale AS "Work-site",
      Says AS Wicket,
      Notes
FROM #job-search AND "JobSearch"
WHERE icontains(Platform, "LinkedIn")
```
