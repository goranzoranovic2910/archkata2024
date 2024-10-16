[Back](/README.md)

---

# Service Review API Methods


## Get Errors Overview

```
GET /api/reporting/service/errorsOverview
```

The `Get Errors Overview` method provides a breakdown of errors across pages, endpoints, or services to help identify and address system issues. The parameter `filterBy` specifies whether to filter by page, endpoint, or service. The response includes the total number of errors and a detailed breakdown.

## Get Crashes Overview

```
GET /api/reporting/service/crashesOverview
```

The `Get Crashes Overview` method retrieves data on system crashes, providing an overview of system stability. The response includes the total number of crashes and detailed crash information.

## Get Service Downtime

```
GET /api/reporting/service/serviceDowntime
```

The `Get Service Downtime` method provides details on service downtime, broken down by different services. The response includes the total downtime and a breakdown by service.

## Get LLM Latency

```
GET /api/reporting/service/llmLatency
```

The `Get LLM Latency` method reports on the latency of LLM services, helping monitor and optimize LLM performance. The response includes the average latency and a breakdown by service.

## Get LLM Cost

```
GET /api/reporting/service/llmCost
```

The `Get LLM Cost` method provides cost data related to running LLM services, offering insights into the financial impact of these operations. The response includes the total cost and a breakdown by usage.

## Get LLM Capacity Usage

```
GET /api/reporting/service/llmCapacity
```

The `Get LLM Capacity Usage` method reports on the capacity usage of the LLM service to ensure the system is operating within its performance limits. The response includes the total capacity used and detailed usage information.

## Triggering data aggregation

```
POST /api/reporting/service/runDataAggregation/{dateFrom}/{dateTo}
```

The `runDataAggregation` method triggers the backend process to gather monthly data. The parameters `dateFrom` and `dateTo` specify the time range for data aggregation.
This method will run backend process to gather data. Since we are operating on single database, all the aggregation we need at this point can be covered by a Database job. 
This job could potentially be triggered by schedule in Database, however, based on requirements we want to allow Admin to trigger it as well.