# Quickstart Guide

This guide walks you through making your first request to the Huddlehouse API.

By the end of this guide, you'll know how to prepare an API request, authenticate with a bearer token, and retrieve workspace information.

## Prerequisites

Before you begin, make sure you have:

- Access to a Huddlehouse workspace
- An API access token
- cURL installed or another HTTP client
- Basic familiarity with REST APIs and JSON

## 1. Understand the API Base URL

All requests to the Huddlehouse API use the following base URL:

`https://api.huddlehouse.example/v1`

The API uses HTTPS and returns JSON responses.

## 2. Prepare Your Authentication Token

Huddlehouse uses bearer token authentication.

For this example, replace `YOUR_API_TOKEN` with a valid API access token.

Keep your token secure. Do not include it in public repositories, client-side code, or shared screenshots.

## 3. Make Your First API Request

Use the following cURL command to retrieve your available workspaces.

### Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/workspaces" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Accept: application/json"
```

### Response

A successful request returns HTTP `200 OK` and a JSON response containing the workspaces associated with the authenticated account.

```json
{
  "data": [
    {
      "id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
      "name": "Product Development",
      "description": "Workspace for product and engineering teams",
      "created_at": "2026-10-15T14:30:00Z"
    }
  ],
  "pagination": {
    "has_more": false,
    "next_cursor": null
  }
}
```

The response includes:

| Field | Description |
|---|---|
| `data` | Array of workspace objects |
| `id` | Unique workspace identifier |
| `name` | Workspace name |
| `description` | Workspace description |
| `created_at` | Workspace creation timestamp |
| `pagination` | Pagination metadata |

## 4. Understand the Response

The API returns a structured JSON response.

Each workspace has a unique identifier (`id`) that you can use when making requests to retrieve specific workspace information or access related resources.

The `pagination` object indicates whether additional results are available.

## 5. Troubleshooting

If your request does not succeed, check the following:

| HTTP Status | Meaning | Suggested Action |
|---|---|---|
| 401 | Unauthorized | Verify that your bearer token is valid |
| 403 | Forbidden | Confirm that your account has permission to access the resource |
| 404 | Not Found | Verify the endpoint and resource identifier |
| 429 | Too Many Requests | Wait before sending additional requests |
| 500 | Internal Server Error | Retry later or investigate the server response |

For additional information, see the [API Errors Guide](errors.md).

## Next Steps

Now that you've made your first API request, continue with:

- [Authentication Guide](authentication.md)
- [API Reference](api-reference.md)
- [Error Codes and Troubleshooting](errors.md)