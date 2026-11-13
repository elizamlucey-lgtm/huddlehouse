# Authentication

The Huddlehouse API uses bearer token authentication to authorize requests.

Every authenticated API request must include a valid access token in the HTTP Authorization header.

## Authentication Overview

Bearer tokens identify and authorize API clients when accessing Huddlehouse resources.

The API expects tokens to be included in the following header format:

```http
Authorization: Bearer YOUR_API_TOKEN
```

Replace `YOUR_API_TOKEN` with your assigned API access token.

## Obtaining an API Token

In the fictional Huddlehouse platform, API tokens are managed through workspace developer settings.

To obtain a token:

1. Sign in to your Huddlehouse workspace.
2. Open **Workspace Settings**.
3. Navigate to **Developer Settings**.
4. Select **API Access Tokens**.
5. Generate a new token.
6. Copy the token and store it securely.

**Important:** API token generation and management are conceptual features in this portfolio project. They are not currently implemented in a live Huddlehouse application.

## Include the Token in API Requests

Include the bearer token in the Authorization header of every authenticated request.

### Example: cURL

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/workspaces" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Accept: application/json"
```

### Example: HTTP Request

```http
GET /v1/workspaces HTTP/1.1
Host: api.huddlehouse.example
Authorization: Bearer YOUR_API_TOKEN
Accept: application/json
```

## Token Security Best Practices

Protect API tokens as you would other sensitive credentials.

Follow these recommendations:

- Never commit API tokens to source control.
- Store tokens in environment variables or an approved secrets manager.
- Do not expose tokens in browser-based client code.
- Avoid including tokens in logs, screenshots, or support requests.
- Use separate credentials for development and production environments.
- Rotate or revoke tokens when they may have been exposed.

## Authentication Errors

The API may return the following responses when authentication fails.

| HTTP Status | Error | Description |
|---|---|---|
| 401 | Unauthorized | The token is missing, invalid, or expired |
| 403 | Forbidden | The authenticated client does not have permission to access the resource |

### Example: 401 Unauthorized

```json
{
  "error": {
    "code": "UNAUTHORIZED",
    "message": "A valid bearer token is required."
  }
}
```

### Example: 403 Forbidden

```json
{
  "error": {
    "code": "FORBIDDEN",
    "message": "You do not have permission to access this resource."
  }
}
```

## Troubleshooting Authentication

If an API request returns an authentication error:

1. Verify that the Authorization header is present.
2. Confirm that the header uses the `Bearer` authentication scheme.
3. Check that the token value has not been truncated or modified.
4. Confirm that the token has not expired or been revoked.
5. Verify that the authenticated account has permission to access the requested resource.

If the problem persists, review the [API Errors Guide](errors.md).

## Related Documentation

- [Quickstart Guide](quickstart.md)
- [API Reference](api-reference.md)
- [Error Codes and Troubleshooting](errors.md)