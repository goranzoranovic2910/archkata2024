[Back](/README.md)

---

# Administrator Endpoint Methods

## Update Candidate Hire Status

```
PUT /api/admin/updateCandidateHireStatus/{candidateId}
```

The `Update Candidate Hire Status` method allows an administrator to update the hire status of a candidate for a specific job.

## Update User

```
PUT /api/admin/updateUser/{userId}
```

The `Update User` method allows an administrator to update general user data, including for candidates and employers.

## Update Candidate

```
PUT /api/admin/updateCandidate/{candidate_id}
```

The `Update Candidate` method allows an administrator to update candidate details using the candidate's ID.


## Update Employer

```
PUT /api/admin/updateEmployer/{employer_id}
```

The `Update Employer` method allows an administrator to update employer-related data using the employer's ID.

## Update Matching Strategy Configuration

```
PUT /api/admin/updateMatchingStrategyConfig/{strategy}
```

The `Update Matching Strategy Configuration` method allows an administrator to update the matching strategy configuration for the skill-matching service (e.g., switch between Cosine Similarity and LLM).