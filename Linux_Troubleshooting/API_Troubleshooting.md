# API Troubleshooting

## Problem

An API request is failing, returning an unexpected response, timing out, or not processing the expected data.

## Step 1: Identify the API Issue

Collect the basic details related to the API failure:

* API endpoint
* HTTP method
* Timestamp of the issue
* Request ID or transaction ID
* HTTP status code
* Error message
* Request and response details

## Step 2: Check the HTTP Method

Verify that the correct HTTP method is being used.

Common HTTP methods:

```text
GET
POST
PUT
PATCH
DELETE
```

## Step 3: Check HTTP Status Code

Review the HTTP response status code to understand the type of issue.

Common status codes:

| Status Code | Meaning                       |
| ----------- | ----------------------------- |
| 200         | Successful request            |
| 201         | Resource created successfully |
| 400         | Bad Request                   |
| 401         | Unauthorized                  |
| 403         | Forbidden                     |
| 404         | Resource Not Found            |
| 408         | Request Timeout               |
| 429         | Too Many Requests             |
| 500         | Internal Server Error         |
| 502         | Bad Gateway                   |
| 503         | Service Unavailable           |
| 504         | Gateway Timeout               |

## Step 4: Test the API Using Postman

Use Postman to test the API endpoint.

Verify:

* API URL
* HTTP method
* Headers
* Authentication
* Request parameters
* Request body
* Response body
* Response status code
* Response time

## Step 5: Check Request Headers

Verify that required headers are present.

Common headers include:

```text
Content-Type: application/json
Authorization: Bearer <token>
Accept: application/json
```

Do not expose real authentication tokens, passwords, API keys, or other credentials in GitHub.

## Step 6: Check Request Body

For POST, PUT, and PATCH requests, validate the request payload.

Example:

```json
{
  "orderId": "12345",
  "status": "confirmed"
}
```

Check that:

* Required fields are present.
* Field names are correct.
* Data types are correct.
* Values are valid.
* JSON format is correct.

## Step 7: Check API Response

Review the response returned by the API.

Example:

```json
{
  "status": "success",
  "message": "Order processed successfully"
}
```

If the response contains an error, check the error message and related request or transaction ID.

## Step 8: Check Application Logs

If the API is integrated with an application, review application logs around the time of the failure.

```bash
grep -i "error" application.log
```

Search for a specific transaction ID:

```bash
grep -i "12345" application.log
```

Monitor new log entries:

```bash
tail -f application.log
```

## Step 9: Check Connectivity

If the API is unreachable, check network connectivity and DNS resolution.

```bash
ping <hostname>
```

```bash
nslookup <hostname>
```

You can also test an API endpoint using curl:

```bash
curl -I https://example.com
```

Use approved endpoints and environments when testing.

## Step 10: Troubleshooting Approach

1. Understand the reported API issue.
2. Collect the endpoint and transaction details.
3. Verify the HTTP method.
4. Check the HTTP status code.
5. Validate headers and authentication.
6. Validate request parameters and payload.
7. Test the API using Postman.
8. Review the API response.
9. Check application logs.
10. Check connectivity if required.
11. Identify the probable root cause.
12. Take the appropriate corrective action.
13. Retest the API.
14. Monitor the application after resolution.
15. Document the incident and resolution.

## Resolution

After taking corrective action, retest the API using Postman or an approved API testing tool.

Verify:

* Expected HTTP status code
* Correct response
* Successful transaction processing
* Application functionality
* No related errors in the logs

## Production Support Best Practices

* Always capture the transaction ID or request ID when available.
* Check the HTTP status code before troubleshooting further.
* Never expose passwords, tokens, API keys, or sensitive customer data.
* Do not test directly against production unless authorized.
* Use Postman collections and environments appropriately.
* Document the root cause and resolution.
* Escalate issues to the API, application, database, or infrastructure team when required.

## Key Tools

* Postman
* curl
* Linux commands
* Application logs
* API documentation
* Monitoring tools
