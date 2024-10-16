[Back](/README.md)

---

# Job Matching

## Get Job Matches

```
GET /api/candidates/jobs/matches
```

The `Get Job Matches` method allows an authenticated candidate to retrieve a list of job matches based on their profile and preferences. The request must include an authorization header with the candidate's token. Query parameters such as `page` and `limit` can be used to paginate the results. Upon successful retrieval, the response includes the total number of matches, the current page, the limit per page, and a list of job matches. Each job match contains details such as job ID, title, company, location, match score, and posted date in ISO 8601 format. For more details, please visit [candidate API specs](/apis/candidate.md).

## Retrieve filtered matches

```
GET /api/candidates/jobs/matches/filter
```

The `Retrieve Filtered Matches` method allows an authenticated candidate to retrieve a list of job matches based on specific filters. The request must include an authorization header with the candidate's token. Query parameters can be used to filter the results, such as `title`, `company`, `location`, `minMatchScore`, `maxMatchScore`, `fromDate`, `toDate`, `page`, and `limit`. Upon successful retrieval, the response includes the total number of matches, the current page, the limit per page, and a list of job matches. Each job match contains details such as job ID, title, company, location, match score, and posted date in ISO 8601 format. For more details, please visit [candidate API specs](/apis/candidate.md).


## Get Job Details

```
GET /api/candidates/jobs/{jobId}
```

The `Get Job Details` method allows an authenticated candidate to retrieve detailed information about a specific job. The request must include an authorization header with the candidate's token and a path parameter specifying the job ID. Upon successful retrieval, the response includes detailed information about the job, such as job ID, title, company, location, description, requirements, posted date in ISO 8601 format, and match score. For more details, please visit [candidate API specs](/apis/candidate.md).