## Account Management
Register Candidate
- POST /api/candidates/register

Request Body:
``` json
  {
    "email": "string",
    "password": "string",
    "firstName": "string",
    "lastName": "string",
    "phoneNumber": "string"
  }
```
```
Response: (201 Created)
```
``` json
  {
    "id": "string",
    "email": "string",
    "firstName": "string",
    "lastName": "string",
    "createdAt": "string (ISO 8601 date)"
  }
```

Login Candidate
- POST /api/candidates/login
Request Body:
``` json
  {
    "email": "string",
    "password": "string"
  }
```
```
Response: (200 OK)
```
``` json
  {
    "token": "string",
    "expiresIn": "number"
  }
```

Get Candidate Profile
- GET /api/candidates/profile
```
Headers:
Authorization: Bearer {token}
Response: (200 OK)
```
``` json
  {
    "id": "string",
    "email": "string",
    "firstName": "string",
    "lastName": "string",
    "phoneNumber": "string"
  }
````

Update Candidate Profile
- PUT /api/candidates/profile
```
Headers:
Authorization: Bearer {token}
Request Body:
```
``` json
  {
    "firstName": "string",
    "lastName": "string",
    "phoneNumber": "string"
  }
```

Response: (200 OK)

``` json
  {
    "id": "string",
    "email": "string",
    "firstName": "string",
    "lastName": "string",
    "phoneNumber": "string",
    "updatedAt": "string (ISO 8601 date)"
  }
```

## Resume Management
Upload Resume
- POST /api/candidates/resume
```
Headers:
Authorization: Bearer {token}
Content-Type: multipart/form-data
Request Body:
- file: (binary)
Response: (201 Created)
```
``` json
  {
    "id": "string",
    "fileName": "string",
    "uploadDate": "string (ISO 8601 date)",
    "fileSize": "number"
  }
```

Get Resume
- GET /api/candidates/resume
```
Headers:
Authorization: Bearer {token}
Response: (200 OK)
```
``` json
  {
    "id": "string",
    "fileName": "string",
    "uploadDate": "string (ISO 8601 date)",
    "fileSize": "number",
    "downloadUrl": "string"
  }
```

Delete Resume
- DELETE /api/candidates/resume
```
Headers:
Authorization: Bearer {token}
Response: (200 OK)
```
``` json
  {
    "message": "Resume deleted successfully"
  }
```

## Anonymized Resume Management
Upload Anonimized Resume
- POST /api/candidates/anonymized
```
Headers:
Authorization: Bearer {token}
Content-Type: multipart/form-data
Request Body:
- file: (binary)
Response: (201 Created)
```
``` json
  {
    "id": "string",
    "fileName": "string",
    "uploadDate": "string (ISO 8601 date)",
    "fileSize": "number"
  }
```

Get Anonimized Resume
- GET /api/candidates/anonimized
```
Headers:
Authorization: Bearer {token}
Response: (200 OK)
```
``` json
  {
    "id": "string",
    "fileName": "string",
    "uploadDate": "string (ISO 8601 date)",
    "fileSize": "number",
    "downloadUrl": "string"
  }
```

Delete Anonimized Resume
- DELETE /api/candidates/anonymized
```
Headers:
Authorization: Bearer {token}
Response: (200 OK)
```
``` json
  {
    "message": "Resume deleted successfully"
  }
```

## AI Tips
Get Resume Tips
- GET /api/candidates/resume/tips
```
Headers:
Authorization: Bearer {token}
Response: (200 OK)
```
``` json
  {
    "resumeId": "string",
    "tips": [
      {
        "category": "string",
        "suggestion": "string",
        "priority": "number"
      }
    ],
    "overallScore": "number"
  }
```

## Job Matching
Get Job Matches
- GET /api/candidates/jobs/matches
```
Headers:
Authorization: Bearer {token}
Query Parameters:
page: number
limit: number
Response: (200 OK)
```
``` json
  {
    "totalMatches": "number",
    "page": "number",
    "limit": "number",
    "matches": [
      {
        "jobId": "string",
        "title": "string",
        "company": "string",
        "location": "string",
        "matchScore": "number",
        "postedDate": "string (ISO 8601 date)"
      }
    ]
  }
```

Retrieve filtered matches
- GET /api/candidates/jobs/matches/filter
```
Headers:
Authorization: Bearer {token}
Query Parameters:
title: string (optional)
company: string (optional)
location: string (optional)
minMatchScore: number (optional)
maxMatchScore: number (optional)
fromDate: string (ISO 8601 date, optional)
toDate: string (ISO 8601 date, optional)
page: number (default: 1)
limit: number (default: 20)
Response: (200 OK)
```
``` json
  {
    "totalMatches": "number",
    "page": "number",
    "limit": "number",
    "matches": [
      {
        "jobId": "string",
        "title": "string",
        "company": "string",
        "location": "string",
        "matchScore": "number",
        "postedDate": "string (ISO 8601 date)"
      }
    ],
    "appliedFilters": {
      "title": "string",
      "company": "string",
      "location": "string",
      "minMatchScore": "number",
      "maxMatchScore": "number",
      "fromDate": "string (ISO 8601 date)",
      "toDate": "string (ISO 8601 date)"
    }
  }
```

Get Job Details
- GET /api/candidates/jobs/{jobId}
```
Headers:
Authorization: Bearer {token}
Path Parameters:
jobId: string
Response: (200 OK)
```
``` json
  {
    "id": "string",
    "title": "string",
    "company": "string",
    "location": "string",
    "description": "string",
    "requirements": ["string"],
    "postedDate": "string (ISO 8601 date)",
    "matchScore": "number"
  }
```

## Job Applications
Apply for Job
- POST /api/candidates/jobs/{jobId}/apply
``` 
Headers:
Authorization: Bearer {token}
Path Parameters:
jobId: string
Response: (201 Created)
```

``` json
  {
    "applicationId": "string",
    "jobId": "string",
    "applicationDate": "string (ISO 8601 date)",
    "status": "string"
  }
```
