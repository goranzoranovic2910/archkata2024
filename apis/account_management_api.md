[Back](/README.md)

---

# Account Management

## Register Candidate

```
POST /api/candidates/register
```

The `Register Candidate` method allows a new candidate to create an account by providing their email, password, first name, last name, and phone number. Upon successful registration, the candidate's details are stored, and a unique candidate ID is generated. The response includes the candidate's ID, email, first name, last name, and the account creation timestamp in ISO 8601 format. For more details please visit [candidate API specs](candidate.md).

## Login Candidate

```
POST /api/candidates/login
```

The `Login Candidate` method allows a registered candidate to log in by providing their credentials. Upon successful authentication, the candidate can access subsequent APIs. The specific method of authentication and session management may vary depending on the implementation decision, and other types of authentication can be used as an implementation detail. For more details please visit [candidate API specs](candidate.md).

## Get Candidate Profile

```
GET /api/candidates/profile
```

The Get Candidate Profile method allows an authenticated candidate to retrieve their profile information. The request must include an authorization header with the candidate's token. Upon successful retrieval, the response includes the candidate's ID, email, first name, last name, and phone number. For more details, please visit [candidate API specs](candidate.md).

## Update Candidate Profile

```
PUT /api/candidates/profile
```

The `Update Candidate Profile` method allows an authenticated candidate to update their profile information. The request must include an authorization header with the candidate's token. The request body should contain the fields to be updated, such as `firstName`, `lastName`, and `phoneNumber`. Upon successful update, the response includes the candidate's ID, email, first name, last name, phone number, and the timestamp of the last update in ISO 8601 format. For more details, please visit [candidate API specs](candidate.md).