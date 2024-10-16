[Back](/README.md)

---

# Anonymized Resume Management

## Upload Anonymized Resume

```
POST /api/candidates/anonymized
```

The `Upload Anonymized Resume` method allows an authenticated candidate to upload an anonymized version of their resume. The request must include an authorization header with the candidate's token and use `multipart/form-data` for the request body. The request body should contain the anonymized resume file as a binary attachment. Upon successful upload, the response includes the anonymized resume's ID, file name, upload date in ISO 8601 format, and file size. For more details, please visit [candidate API specs](/apis/candidate.md).


## Get Anonymized Resume

```
GET /api/candidates/anonymized
```

The `Get Anonymized Resume` method allows an authenticated candidate to retrieve their uploaded anonymized resume. The request must include an authorization header with the candidate's token. Upon successful retrieval, the response includes the anonymized resume's ID, file name, upload date in ISO 8601 format, file size, and a download URL for the resume file. For more details, please visit [candidate API specs](/apis/candidate.md).


## Delete Anonymized Resume

```
DELETE /api/candidates/anonymized
```

The `Delete Anonymized Resume` method allows an authenticated candidate to delete their uploaded anonymized resume. The request must include an authorization header with the candidate's token. Upon successful deletion, the response includes a message confirming that the anonymized resume was deleted successfully. For more details, please visit [candidate API specs](/apis/candidate.md).