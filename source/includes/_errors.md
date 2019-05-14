# Errors

<aside class="notice">
Solmate uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the 2xx range indicate success. Codes in the 4xx range indicate an error that failed given the information provided (e.g., a required parameter was omitted, a charge failed, etc.). Codes in the 5xx range indicate an error with Solmate's servers (these are rare).
</aside>

The Solmate API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- The request was unacceptable, often due to missing a required parameter.
401 | Unauthorized -- No valid API key provided.
402 | Request Faile -- The parameters were valid but the request failed.
404 | Not Found -- The requested resource doesn't exist.
409 | Conflict -- The request conflicts with another request (perhaps due to using the same idempotent key).
429 | Too Many Requests -- Too many requests hit the API too quickly. We recommend an exponential backoff of your requests.
500 | Internal Server Error -- Something went wrong on Solmate's end. (These are rare.)
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
