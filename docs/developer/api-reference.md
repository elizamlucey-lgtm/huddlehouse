# API Reference

The Huddlehouse REST API provides endpoints for managing workspaces, projects, and documents. Developers can use these endpoints to integrate workspace management, project organization, and document collaboration into their applications.

> **Portfolio demonstration:** Huddlehouse is a fictional product. This API reference describes a proposed API contract. The endpoints and examples are illustrative and are not connected to a live service.

---

## On this page

**Getting Started**
- [Base URL](#base-url)
- [General Information](#general-information)
- [Authentication](#authentication)
- [Resource Identifiers](#resource-identifiers)
- [Date and Time Format](#date-and-time-format)

**Workspaces**
- [List Workspaces](#list-workspaces)
- [Retrieve a Workspace](#retrieve-a-workspace)
- [Create a Workspace](#create-a-workspace)

**Projects**
- [List Projects](#list-projects)
- [Create a Project](#create-a-project)
- [Retrieve a Project](#retrieve-a-project)

**Documents**
- [List Documents](#list-documents)
- [Create a Document](#create-a-document)
- [Retrieve a Document](#retrieve-a-document)

**Additional Reference**
- [Pagination](#pagination)
- [Common Response Codes](#common-response-codes)
- [Error Response Format](#error-response-format)
- [API Usage Notes](#api-usage-notes)

---

<a id="base-url"></a>
## Base URL

All API endpoints use the following base URL:

```text
https://api.huddlehouse.example/v1
```

<a id="general-information"></a>
## General Information

### Request Format

Requests that include a body must use JSON.

Include the following headers:

```http
Content-Type: application/json
Accept: application/json
```

### Response Format

Successful API responses return JSON.

Responses use standard HTTP status codes to indicate whether a request succeeded or encountered an error.

<a id="authentication"></a>
### Authentication

All endpoints require bearer token authentication.

Include your API token in the `Authorization` header:

```http
Authorization: Bearer YOUR_API_TOKEN
```

See the [Authentication Guide](authentication.md) for details.

<a id="resource-identifiers"></a>
### Resource Identifiers

Huddlehouse uses UUIDs to uniquely identify workspaces, projects, and documents.

<a id="date-and-time-format"></a>
### Date and Time Format

Timestamps use ISO 8601 format in UTC.

Example:

```text
2026-10-15T14:30:00Z
```

---

# Workspaces

Workspaces provide a shared environment for teams to organize projects, documents, and collaboration.

<a id="list-workspaces"></a>
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

**200 OK**

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

### Response Fields

| Field | Type | Description |
|---|---|---|
| data | Array | Collection of workspace objects |
| data.id | UUID | Unique workspace identifier |
| data.name | String | Workspace name |
| data.description | String | Workspace description |
| data.created_at | String | Workspace creation timestamp |
| pagination.has_more | Boolean | Indicates whether additional results are available |
| pagination.next_cursor | String or null | Cursor used to retrieve the next page of results |

<a id="retrieve-a-workspace"></a>
## Retrieve a Workspace

Retrieve details for a specific workspace.

<badge color="success">GET</badge> `/workspaces/{workspaceId}`

### Path Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| workspaceId | UUID | Yes | Unique identifier of the workspace |

### Example Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/workspaces/7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Accept: application/json"
```

### Successful Response

**200 OK**

```json
{
  "id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
  "name": "Product Development",
  "description": "Workspace for product and engineering teams",
  "created_at": "2026-10-15T14:30:00Z"
}
```

### Response Fields

| Field | Type | Description |
|---|---|---|
| id | UUID | Unique workspace identifier |
| name | String | Workspace name |
| description | String | Workspace description |
| created_at | String | Workspace creation timestamp |

<a id="create-a-workspace"></a>
## Create a Workspace

Create a new workspace for organizing projects, documents, and team collaboration.

<badge color="info">POST</badge> `/workspaces`

### Request Body

| Field | Type | Required | Description |
|---|---|---|---|
| name | String | Yes | Name of the workspace |
| description | String | No | Optional workspace description |

### Example Request

```bash
curl --request POST \
  --url "https://api.huddlehouse.example/v1/workspaces" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Content-Type: application/json" \
  --header "Accept: application/json" \
  --data '{
    "name": "Product Development",
    "description": "Workspace for product and engineering teams"
  }'
```

### Successful Response

**201 Created**

```json
{
  "id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
  "name": "Product Development",
  "description": "Workspace for product and engineering teams",
  "created_at": "2026-11-13T14:30:00Z"
}
```

### Response Fields

| Field | Type | Description |
|---|---|---|
| id | UUID | Unique identifier assigned to the workspace |
| name | String | Workspace name |
| description | String | Workspace description |
| created_at | String | Workspace creation timestamp |

---

# Projects

Projects allow teams to organize work, track progress, and coordinate deliverables within a workspace.

<a id="list-projects"></a>
## List Projects

Retrieve projects accessible to the authenticated account.

<badge color="success">GET</badge> `/projects`

### Query Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| workspace_id | UUID | No | Filter projects by workspace |
| limit | Integer | No | Number of results to return; default 20, maximum 100 |
| cursor | String | No | Pagination cursor from a previous response |

### Example Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/projects?limit=20" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Accept: application/json"
```

### Successful Response

**200 OK**

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

### Response Fields

| Field | Type | Description |
|---|---|---|
| data | Array | Collection of project objects |
| data.id | UUID | Unique project identifier |
| data.workspace_id | UUID | Identifier of the parent workspace |
| data.name | String | Project name |
| data.status | String | Current project status |
| data.created_at | String | Project creation timestamp |
| pagination.has_more | Boolean | Indicates whether additional results are available |
| pagination.next_cursor | String or null | Cursor used to retrieve the next page |

<a id="create-a-project"></a>
## Create a Project

Create a new project in a workspace.

<badge color="info">POST</badge> `/projects`

### Request Body

| Field | Type | Required | Description |
|---|---|---|---|
| workspace_id | UUID | Yes | Workspace where the project will be created |
| name | String | Yes | Project name |
| description | String | No | Optional project description |

### Example Request

```bash
curl --request POST \
  --url "https://api.huddlehouse.example/v1/projects" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Content-Type: application/json" \
  --header "Accept: application/json" \
  --data '{
    "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
    "name": "Website Redesign",
    "description": "Refresh the Huddlehouse marketing website"
  }'
```

### Successful Response

**201 Created**

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

### Response Fields

| Field | Type | Description |
|---|---|---|
| id | UUID | Unique project identifier |
| workspace_id | UUID | Identifier of the parent workspace |
| name | String | Project name |
| description | String | Project description |
| status | String | Current project status |
| created_at | String | Project creation timestamp |

<a id="retrieve-a-project"></a>
## Retrieve a Project

Retrieve details for a specific project.

<badge color="success">GET</badge> `/projects/{projectId}`

### Path Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| projectId | UUID | Yes | Unique identifier of the project |

### Example Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/projects/2a8f4c91-6d3e-42b1-9f50-8c7d2e1a6034" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Accept: application/json"
```

### Successful Response

**200 OK**

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

### Response Fields

| Field | Type | Description |
|---|---|---|
| id | UUID | Unique project identifier |
| workspace_id | UUID | Identifier of the parent workspace |
| name | String | Project name |
| description | String | Project description |
| status | String | Current project status |
| created_at | String | Project creation timestamp |

---

# Documents

Documents provide shared knowledge and reference materials within a workspace.

<a id="list-documents"></a>
## List Documents

Retrieve documents available to the authenticated account.

<badge color="success">GET</badge> `/documents`

### Query Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| workspace_id | UUID | No | Filter documents by workspace |
| limit | Integer | No | Number of results to return; default 20, maximum 100 |
| cursor | String | No | Pagination cursor from a previous response |

### Example Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/documents?limit=20" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Accept: application/json"
```

### Successful Response

**200 OK**

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

### Response Fields

| Field | Type | Description |
|---|---|---|
| data | Array | Collection of document objects |
| data.id | UUID | Unique document identifier |
| data.workspace_id | UUID | Identifier of the parent workspace |
| data.title | String | Document title |
| data.created_at | String | Document creation timestamp |
| pagination.has_more | Boolean | Indicates whether additional results are available |
| pagination.next_cursor | String or null | Cursor used to retrieve the next page |

<a id="create-a-document"></a>
## Create a Document

Create a new document in a workspace.

<badge color="info">POST</badge> `/documents`

### Request Body

| Field | Type | Required | Description |
|---|---|---|---|
| workspace_id | UUID | Yes | Workspace where the document will be created |
| title | String | Yes | Document title |
| content | String | Yes | Document body content |

### Example Request

```bash
curl --request POST \
  --url "https://api.huddlehouse.example/v1/documents" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Content-Type: application/json" \
  --header "Accept: application/json" \
  --data '{
    "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
    "title": "Engineering Onboarding",
    "content": "Welcome to the engineering team."
  }'
```

### Successful Response

**201 Created**

```json
{
  "id": "9b4e7c12-5d3a-48f1-a620-3c8d9e7f2045",
  "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
  "title": "Engineering Onboarding",
  "content": "Welcome to the engineering team.",
  "created_at": "2026-10-22T11:00:00Z"
}
```

### Response Fields

| Field | Type | Description |
|---|---|---|
| id | UUID | Unique document identifier |
| workspace_id | UUID | Identifier of the parent workspace |
| title | String | Document title |
| content | String | Document body content |
| created_at | String | Document creation timestamp |

<a id="retrieve-a-document"></a>
## Retrieve a Document

Retrieve a specific document.

<badge color="success">GET</badge> `/documents/{documentId}`

### Path Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| documentId | UUID | Yes | Unique identifier of the document |

### Example Request

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/documents/9b4e7c12-5d3a-48f1-a620-3c8d9e7f2045" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Accept: application/json"
```

### Successful Response

**200 OK**

```json
{
  "id": "9b4e7c12-5d3a-48f1-a620-3c8d9e7f2045",
  "workspace_id": "7f3a2c91-8d4e-4b6f-a921-2c5d8e7f1043",
  "title": "Engineering Onboarding",
  "content": "Welcome to the engineering team.",
  "created_at": "2026-10-22T11:00:00Z"
}
```

### Response Fields

| Field | Type | Description |
|---|---|---|
| id | UUID | Unique document identifier |
| workspace_id | UUID | Identifier of the parent workspace |
| title | String | Document title |
| content | String | Document body content |
| created_at | String | Document creation timestamp |

---

<a id="pagination"></a>
# Pagination

List endpoints support cursor-based pagination to help clients retrieve large collections of resources.

### Query Parameters

| Parameter | Type | Required | Description |
|---|---|---|---|
| limit | Integer | No | Number of results to return; default 20, maximum 100 |
| cursor | String | No | Cursor returned by the previous response |

### Example Request

Use the `next_cursor` value returned in a previous response to retrieve the next page.

```bash
curl --request GET \
  --url "https://api.huddlehouse.example/v1/projects?limit=20&cursor=eyJvZmZzZXQiOjIwfQ" \
  --header "Authorization: Bearer YOUR_API_TOKEN" \
  --header "Accept: application/json"
```

### Pagination Response

```json
{
  "data": [
    {
      "id": "2a8f4c91-6d3e-42b1-9f50-8c7d2e1a6034",
      "name": "Website Redesign",
      "status": "active"
    }
  ],
  "pagination": {
    "has_more": true,
    "next_cursor": "eyJvZmZzZXQiOjQwfQ"
  }
}
```

### Pagination Fields

| Field | Type | Description |
|---|---|---|
| has_more | Boolean | Indicates whether additional results are available |
| next_cursor | String or null | Cursor to include in the next request; null when no additional results are available |

When `has_more` is `false`, no additional results are available.

---

<a id="common-response-codes"></a>
# Common Response Codes

The API uses standard HTTP status codes to communicate request outcomes.

| HTTP Status | Description | Recommended Action |
|---|---|---|
| 200 | Request completed successfully | Process the returned resource or collection |
| 201 | Resource created successfully | Store the new resource identifier |
| 400 | Request contains invalid parameters or data | Review request parameters and formatting |
| 401 | Authentication is required or invalid | Verify the bearer token |
| 403 | Client does not have permission to access the resource | Verify user permissions |
| 404 | Requested resource was not found | Verify the resource identifier |
| 409 | Request conflicts with the current resource state | Review the resource state before retrying |
| 422 | Request validation failed | Review the fields identified in the error response |
| 429 | Rate limit exceeded | Wait before retrying the request |
| 500 | Unexpected server error | Retry later or contact support with the request ID |

<a id="error-response-format"></a>
## Error Response Format

Error responses use a consistent JSON structure.

### Example: Unauthorized Request

**401 Unauthorized**

```json
{
  "error": {
    "code": "unauthorized",
    "message": "A valid API token is required.",
    "request_id": "req_abc123"
  }
}
```

### Example: Validation Error

**422 Unprocessable Entity**

```json
{
  "error": {
    "code": "validation_error",
    "message": "The request contains invalid fields.",
    "details": [
      {
        "field": "name",
        "issue": "This field is required."
      }
    ],
    "request_id": "req_def456"
  }
}
```

### Error Response Fields

| Field | Type | Description |
|---|---|---|
| error.code | String | Machine-readable error identifier |
| error.message | String | Human-readable explanation of the error |
| error.details | Array | Optional collection of field-level validation errors |
| error.details.field | String | Name of the field associated with the error |
| error.details.issue | String | Description of the validation issue |
| error.request_id | String | Unique identifier for troubleshooting the request |

For additional troubleshooting information, see the [Error Codes and Troubleshooting Guide](errors.md).

---

<a id="api-usage-notes"></a>
# API Usage Notes

- All endpoints use HTTPS.
- All endpoints require bearer token authentication.
- JSON request bodies must use the `application/json` content type.
- Successful responses return JSON.
- Resource identifiers use UUID format.
- Timestamps use ISO 8601 format in UTC.
- List endpoints support cursor-based pagination.
- Error responses include a machine-readable error code and request identifier.
- The API examples are illustrative and do not connect to a live service.
