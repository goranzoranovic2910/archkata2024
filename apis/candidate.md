## Account Management
```
POST /api/candidates/register: Register Candidate
POST /api/candidates/login: Login Candidate
GET /api/candidates/profile: Get Candidate Profile
PUT /api/candidates/profile: Update Candidate Profile
```

## Resume Management
```
POST /api/candidates/resume: Upload Resume 
GET /api/candidates/resume: Get Resume
DELETE /api/candidates/resume: Delete Resume
```

## Anonymized Resume Management
```
POST /api/candidates/anonymized: Upload Anonimized Resume
GET /api/candidates/anonimized: Get Anonimized Resume
DELETE /api/candidates/anonymized: Delete Anonimized Resume
```

## AI Tips
```
GET /api/candidates/resume/tips: Get Resume Tips
```

## Job Matching
```
GET /api/candidates/jobs/matches: Get Job Matches
GET /api/candidates/jobs/matches/filter: Retrieve filtered matches
GET /api/candidates/jobs/{jobId}: Get Job Details
```

## Job Applications
```
POST /api/candidates/jobs/{jobId}/apply: Apply for Job
```
