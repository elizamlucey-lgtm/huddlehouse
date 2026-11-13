
# Errors and Troubleshooting

The Huddlehouse API uses standard HTTP status codes to indicate whether a request succeeded or failed.

When an API request fails, the response includes an error object with a machine-readable error code and a descriptive message.

## Error Response Format

All API errors use the following JSON structure:

```json
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "The requested resource could not be found."
  }
}
```

### Error Object Fields

| Field | Type | Description |
|---|---|---|
| `error` | Object | Contains information about the error |
| `code` | String | Machine-readable error identifier |
| `message` | String | Description of the error |

## HTTP Status Codes

| HTTP Status | Error Code | Description |
|---|---|---|
| 400 | `BAD_REQUEST` | Request contains invalid parameters or data |
| 401 | `UNAUTHORIZED` | Authentication is missing or invalid |
| 403 | `FORBIDDEN` | Client does not have permission to access the resource |
| 404 | `RESOURCE_NOT_FOUND` | Requested resource does not exist or is unavailable |
| 409 | `CONFLICT` | Request conflicts with the current resource state |
| 422 | `VALIDATION_ERROR` | Request data failed validation |
| 429 | `RATE_LIMIT_EXCEEDED` | Client exceeded the allowed request rate |
| 500 | `INTERNAL_SERVER_ERROR` | Unexpected server error |
| 503 | `SERVICE_UNAVAILABLE` | API service is temporarily unavailable |

## Common Errors

### 400 Bad Request

The request contains invalid parameters or malformed data.

**Example response:**

```json
{
  "error": {
    "code": "BAD_REQUEST",
    "message": "The request contains invalid parameters."
  }
}
```

**Troubleshooting:**

1. Check the request URL and HTTP method.
2. Verify that query parameters use the expected format.
3. Confirm that the request body contains valid JSON.
4. Remove unsupported or incorrectly formatted fields.

### 401 Unauthorized

The request does not include a valid authentication token.

**Example response:**

```json
{
  "error": {
    "code": "UNAUTHORIZED",
    "message": "A valid bearer token is required."
  }
}
```

**Troubleshooting:**

1. Confirm that the Authorization header is present.
2. Verify that the authentication scheme is `Bearer`.
3. Check that the token has not expired or been revoked.
4. Generate a replacement token if necessary.

See the [Authentication Guide](authentication.md).

### 403 Forbidden

The authenticated client does not have permission to access the requested resource.

**Example response:**

```json
{
  "error": {
    "code": "FORBIDDEN",
    "message": "You do not have permission to access this resource."
  }
}
```

**Troubleshooting:**

1. Confirm that the authenticated account has access to the workspace.
2. Verify the permissions assigned to the API client.
3. Confirm that the requested action is allowed for the resource.

### 404 Not Found

The requested resource does not exist or is unavailable to the authenticated client.

**Example response:**

```json
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "The requested resource could not be found."
  }
}
```

**Troubleshooting:**

1. Verify the resource identifier.
2. Confirm that the resource belongs to the expected workspace.
3. Check the endpoint path for spelling errors.
4. Confirm that the resource has not been deleted.

### 409 Conflict

The request conflicts with the current state of a resource.

**Example response:**

```json
{
  "error": {
    "code": "CONFLICT",
    "message": "The requested operation conflicts with the current resource state."
  }
}
```

**Troubleshooting:**

1. Retrieve the current resource state.
2. Review whether another operation changed the resource.
3. Retry the request after resolving the conflict.

### 422 Validation Error

The request was understood, but one or more fields failed validation.

**Example response:**

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "The name field is required."
  }
}
```

**Troubleshooting:**

1. Review the request body.
2. Confirm that all required fields are included.
3. Verify that each field uses the expected data type.
4. Check field values against documented constraints.

### 429 Too Many Requests

The client exceeded the API rate limit.

**Example response:**

```json
{
  "error": {
    "code": "RATE_LIMIT_EXCEEDED",
    "message": "Too many requests. Try again later."
  }
}
```

**Troubleshooting:**

1. Reduce the frequency of API requests.
2. Implement exponential backoff before retrying.
3. Avoid repeatedly retrying failed requests without a delay.
4. Review any rate-limit information returned in the response headers.

### 500 Internal Server Error

The API encountered an unexpected server-side error.

**Troubleshooting:**

1. Retry the request after a short delay.
2. Verify that the request is correctly formatted.
3. Record the endpoint, timestamp, and response details.
4. Escalate the issue through the documented support process if it persists.

### 503 Service Unavailable

The API is temporarily unavailable.

**Troubleshooting:**

1. Wait before retrying the request.
2. Use exponential backoff for repeated attempts.
3. Avoid sending large volumes of retry requests.
4. Retry when the service becomes available.

## Recommended Client Error Handling

When integrating with the Huddlehouse API, implement consistent error handling.

Recommended practices include:

- Check the HTTP status code before processing a response.
- Parse the error object when a request fails.
- Use machine-readable error codes to identify failure types.
- Log relevant diagnostic information without exposing credentials.
- Retry temporary failures using exponential backoff.
- Do not automatically retry requests that require user or data correction.

## Related Documentation

- [Quickstart Guide](quickstart.md)
- [Authentication Guide](authentication.md)
- [API Reference](api-reference.md)
