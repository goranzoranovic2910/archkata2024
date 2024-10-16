[Back](/README.md)

---

# Resume Management

## Upload Resume

``` 
POST /api/candidates/resume
```

The `Upload Resume` method allows an authenticated candidate to upload their resume. The request must include an authorization header with the candidate's token and use `multipart/form-data` for the request body. The request body should contain the resume file as a binary attachment. Upon successful upload, the response includes the resume's ID, file name, upload date in ISO 8601 format, and file size. For more details, please visit [candidate API specs](/apis/candidate.md).

## Get Resume

``` 
GET /api/candidates/resume/{resume_id}
```

The `Get Resume` method allows an authenticated candidate to retrieve their uploaded resume. The request must include an authorization header with the candidate's token. Upon successful retrieval, the response includes the resume's ID, file name, upload date in ISO 8601 format, file size, and a download URL for the resume file. For more details, please visit [candidate API specs](/apis/candidate.md).

## Delete Resume

```
DELETE /api/candidates/resume/{resume_id}
```

The `Delete Resume` method allows an authenticated candidate to delete their uploaded resume. The request must include an authorization header with the candidate's token. Upon successful deletion, the response includes a message confirming that the resume was deleted successfully. For more details, please visit [candidate API specs](/apis/candidate.md).