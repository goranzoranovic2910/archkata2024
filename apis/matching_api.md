[Back](/README.md)

---

# Matching API

## Get Job for Candidate

Retrieve the list of jobs that the candidate applied to. The job data includes the job requirements and expected skills.

```
GET api/matching/candidates/{candidate_id}/jobs
```

## Get Job Skills

Extract the required skills for the job from the `job_id`. Output is a map of skills. Example: `{Java: Expert, SQL: Intermediate}`

```
GET api/matching/jobs/{job_id}/skills
```

## Score Candidate Job Match

Compare the candidate’s skills with the job’s required skills. Use Cosine Similarity to compute a score (1-100%) that represents the candidate’s fit for the job.

```
GET api/matching/candidates/{candidate_id}/jobs/{job_id}/score
```

## Store Matching Score

Save the calculated score in the database, linking the CandidateId, JobAdId, and the score. Example: `{candidate_id: 123, job_id: 456, score: 85}`

```
PUT api/matching/candidates/{candidate_id}/jobs/{job_id}/score
```