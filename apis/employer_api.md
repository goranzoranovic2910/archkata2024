[Back](/README.md)

---

# Employer

## Register employer

```
POST /api/employer
```

The `Register Employer` method allows a new employer to create an account and autofill company details. Upon successful registration, the employer's information is stored, and a unique employer ID is generated. The response includes the employer's ID and details.

## Retrieve Employer Details

```
GET /api/employer/{employer_id}
```

The `Retrieve Employer Details` method allows an employer to view their account information, including job ads and payment history.

## Update Employer Information

```
PUT /api/employer/{employer_id}
```

The `Update Employer Information` method allows an employer to update their profile. The request body should contain the fields to be updated.

## Deactivate Employer Profile

```
DELETE /employer/{employer_id}
```

The `Deactivate Employer Profile` method allows an employer to deactivate their account. Upon successful deactivation, the response includes a confirmation message.

## Download Anonymized Candidate Resume

```
GET /api/employer/{employer_id}/{candidate_id}/anonymized
```

The `Download Anonymized Candidate Resume` method allows an employer to retrieve an anonymized resume for a specific candidate.

## Download Unlocked Candidate Resume

```
GET /api/employer/{employer_id}/candidates/{candidate_id}/resume