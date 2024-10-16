[Back](/README.md)

---

# Business Reporting API Methods

## Get Active Candidates

```
GET /api/reporting/business/activeCandidates
```

The `Get Active Candidates` method retrieves the number of active candidates over a given period. The parameters `dateFrom` and `dateTo` specify the time range for the data. The response includes a timeline of active candidate counts.

## Get Active Employers

```
GET /api/reporting/business/activeEmployers
```

The `Get Active Employers` method retrieves the number of active employers over a given period. The parameters `dateFrom` and `dateTo` specify the time range for the data. The response includes a timeline of active employer counts.

## Get Active Jobs

```
GET /api/reporting/business/activeJobs
```

The `Get Active Jobs` method retrieves the number of active job postings over a given period. The parameters `dateFrom` and `dateTo` specify the time range for the data. The response includes a timeline of active job counts.

## Get Score Vs Offer Comparison

```
GET /api/reporting/business/scoreOfferComparison
```

The `Get Score Vs Offer Comparison` method provides a histogram showing the distribution of scores and the number of candidates receiving job offers within each score range. This helps determine the accuracy of the matching algorithm by correlating high scores with high job offer counts.

## Get Score Vs Reject Comparison

```
GET /api/reporting/business/scoreRejectComparison
```

The `Get Score Vs Reject Comparison` method provides a histogram showing the distribution of scores and the number of candidates rejected within each score range. This helps identify score ranges where candidates are more likely to be rejected.

## Get Demographic Offer Reject Breakdown

```
GET /api/reporting/business/demographicOfferRejectBreakdown
```

The `Get Demographic Offer Reject Breakdown` method provides data on offers and rejections categorized by demographic groups

## Get Employer Survey Data

```
GET /api/reporting/business/employerSurvey
```

The `Get Employer Survey Data` method retrieves feedback from employers, offering insights into their experience with the platform. The response includes survey results.

## Get Candidate Survey Data

```
GET /api/reporting/business/candidateSurvey
```

The `Get Candidate Survey Data` method retrieves feedback from candidates, evaluating their experience on the platform. The response includes survey results.
