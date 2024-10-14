## Employer
```
POST /employer: Register a new employer and autofill company details.
GET /employer/{id}: Retrieve employer details, including job ads and payment history.
PUT /employer/{id}: Update employer information.
DELETE /employer/{id}: Deactivate employer profile.
GET /employer/{employerId}/{candidateId}/anonimized : Download anonymized candidate resume.
GET /employer/{employerId}/candidates/{candidateId}/resume: Download unlocked candidate resume.
```

## Job Ads
```
POST /employer/{id}/job: Create a new job ad.
GET /employer/{id}/jobs: Retrieve all job ads for an employer.
PUT /employer/{id}/job/{jobId}: Update a job ad.
DELETE /employer/{id}/job/{jobId}: Remove a job ad.
```

## Payments
```
POST /employer/{id}/payment: Make a payment to unlock candidate profiles or services.
GET /employer/{id}/payments: Retrieve payment history for an employer.
```

## HR System Integration
```
POST /employer/{id}/hrIntegration: Integrate ClearView with an HR system.
GET /employer/{id}/hrSync: Synchronize job ads with HR system.
```
