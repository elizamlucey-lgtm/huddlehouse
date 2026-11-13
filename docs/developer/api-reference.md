# API Reference

The Huddlehouse REST API provides endpoints for managing workspaces, projects, and documents.

All endpoints use the following base URL:

`https://api.huddlehouse.example/v1`

## General Information

### Request Format

Requests that include a body must use JSON.

Include the following header:

```http
Content-Type: application/json
```

### Response Format

Successful API responses return JSON.

### Authentication

All endpoints require bearer token authentication.

See the [Authentication Guide](authentication.md) for details.

---

# Workspaces

Workspaces provide a shared environment for teams to organize projects, documents, and collaboration.

## List Workspaces

Retrieve the workspaces available to the authenticated account.

<badge color="success">GET</badge> `/workspaces`

### Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/workspaces" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Accept: application/json"
```

### Successful Response

**HTTP 200 OK**

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

## Retrieve a Workspace

Retrieve details for a specific workspace.

<badge color="success">GET</badge> `/workspaces/{workspaceId}`

### Path Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `workspaceId` | UUID | Yes | Unique identifier of the workspace |

### Example Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/workspaces/7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043" \
  --header "Authorization: Bearer YOUR_API_TOKEN"
```

### Successful Response

**HTTP 200 OK**

```json
{
  "id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
  "name": "Product Development",
  "description": "Workspace for product and engineering teams",
  "created_at": "2026-10-15T14:30:00Z"
}
```

---

# Projects

Projects allow teams to organize work, track progress, and coordinate deliverables.

## List Projects

Retrieve projects accessible to the authenticated account.

<badge color="success">GET</badge> `/projects`

### Query Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `workspace_id` | UUID | No | Filter projects by workspace |
| `limit` | Integer | No | Number of results to return; default 20, maximum 100 |
| `cursor` | String | No | Pagination cursor from a previous response |

### Example Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/projects?limit=20" \
  --header "Authorization: Bearer YOUR_API_TOKEN"
```

### Successful Response

**HTTP 200 OK**

```json
{
  "data": [
    {
      "id": "2a8f4c91-6d3e-42b1-9f50-8c7d2e1a6034",
      "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
      "name": "Website Redesign",
      "status": "active",
      "created_at": "2026-10-20T09:15:00Z"
    }
  ],
  "pagination": {
    "has_more": false,
    "next_cursor": null
  }
}
```

## Create a Project

Create a new project in a workspace.

<badge color="info">POST</badge> `/projects`

### Request Body

| Field | Type | Required | Description |
|---|---|---|---|
| `workspace_id` | UUID | Yes | Workspace where the project will be created |
| `name` | String | Yes | Project name |
| `description` | String | No | Optional project description |

### Example Request

```bash
curl --request POST \
  --url "https://api.huddlehouse.example/v1/projects" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
    "name": "Website Redesign",
    "description": "Refresh the Huddlehouse marketing website"
  }'
```

### Successful Response

**HTTP 201 Created**

```json
{
  "id": "2a8f4c91-6d3e-42b1-9f50-8c7d2e1a6034",
  "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
  "name": "Website Redesign",
  "description": "Refresh the Huddlehouse marketing website",
  "status": "active",
  "created_at": "2026-10-20T09:15:00Z"
}
```

## Retrieve a Project

Retrieve details for a specific project.

<badge color="success">GET</badge> `/projects/{projectId}`

### Path Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `projectId` | UUID | Yes | Unique identifier of the project |

### Example Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/projects/2a8f4c91-6d3e-42b1-9f50-8c7d2e1a6034" \
  --header "Authorization: Bearer YOUR_API_TOKEN"
```

### Successful Response

**HTTP 200 OK**

```json
{
  "id": "2a8f4c91-6d3e-42b1-9f50-8c7d2e1a6034",
  "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
  "name": "Website Redesign",
  "description": "Refresh the Huddlehouse marketing website",
  "status": "active",
  "created_at": "2026-10-20T09:15:00Z"
}
```

---

# Documents

Documents provide shared knowledge and reference materials within a workspace.

## List Documents

Retrieve documents available to the authenticated account.

<badge color="success">GET</badge> `/documents`

### Query Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `workspace_id` | UUID | No | Filter documents by workspace |
| `limit` | Integer | No | Number of results to return; default 20, maximum 100 |
| `cursor` | String | No | Pagination cursor from a previous response |

### Example Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/documents?limit=20" \
  --header "Authorization: Bearer YOUR_API_TOKEN"
```

### Successful Response

**HTTP 200 OK**

```json
{
  "data": [
    {
      "id": "9b4e7c12-5d3a-48f1-a620-3c8d9e7f2045",
      "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
      "title": "Engineering Onboarding",
      "created_at": "2026-10-22T11:00:00Z"
    }
  ],
  "pagination": {
    "has_more": false,
    "next_cursor": null
  }
}
```

## Create a Document

Create a new document in a workspace.

<badge color="info">POST</badge> `/documents`

### Request Body

| Field | Type | Required | Description |
|---|---|---|---|
| `workspace_id` | UUID | Yes | Workspace where the document will be created |
| `title` | String | Yes | Document title |
| `content` | String | Yes | Document body content |

### Example Request

```bash
curl --request POST \
  --url "https://api.huddlehouse.example/v1/documents" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Content-Type: application/json" \
  --data '{
    "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
    "title": "Engineering Onboarding",
    "content": "Welcome to the engineering team."
  }'
```

### Successful Response

**HTTP 201 Created**

```json
{
  "id": "9b4e7c12-5d3a-48f1-a620-3c8d9e7f2045",
  "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
  "title": "Engineering Onboarding",
  "content": "Welcome to the engineering team.",
  "created_at": "2026-10-22T11:00:00Z"
}
```

## Retrieve a Document

Retrieve a specific document.

<badge color="success">GET</badge> `/documents/{documentId}`

### Path Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| `documentId` | UUID | Yes | Unique identifier of the document |

### Example Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/documents/9b4e7c12-5d3a-48f1-a620-3c8d9e7f2045" \
  --header "Authorization: Bearer YOUR_API_TOKEN"
```

### Successful Response

**HTTP 200 OK**

```json
{
  "id": "9b4e7c12-5d3a-48f1-a620-3c8d9e7f2045",
  "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
  "title": "Engineering Onboarding",
  "content": "Welcome to the engineering team.",
  "created_at": "2026-10-22T11:00:00Z"
}
```

---

## Common Response Codes

| HTTP Status | Description |
|---|---|
| 200 | Request completed successfully |
| 201 | Resource created successfully |
| 400 | Request contains invalid parameters or data |
| 401 | Authentication is required or invalid |
| 403 | Client does not have permission to access the resource |
| 404 | Requested resource was not found |
| 429 | Rate limit exceeded |
| 500 | Unexpected server error |

For more information, see the [Error Codes and Troubleshooting Guide](errors.md).