# Developer Workflows: Let's Connect Things!

Welcome to Developer Workflows!

In this course, Nova and Pip are going to learn how applications communicate with each other.

We'll explore APIs, endpoints, authentication, requests, responses, and troubleshooting.

Don't worry if these words sound complicated. We'll break everything down into small pieces.

By the end of this course, you'll understand the basics of how developers connect applications using the Huddlehouse API.

---

## Meet Your Developer Guides

<div style="display:flex; flex-wrap:wrap; gap:20px; align-items:center; margin:24px 0;">
  <div style="flex:1; min-width:180px; text-align:center; background:#f2f6f1; border-radius:16px; padding:18px;">
    <img src="assets/mascot-1.png" alt="Nova, your developer guide" style="width:150px; max-width:100%; height:150px; object-fit:contain;">
    <h3>Nova</h3>
    <p><strong>Your developer guide</strong></p>
    <p>Nova knows how APIs work and enjoys explaining technical concepts.</p>
  </div>
  <div style="flex:1; min-width:180px; text-align:center; background:#f3f0fa; border-radius:16px; padding:18px;">
    <img src="assets/mascot-3.png" alt="Pip, learning about APIs" style="width:150px; max-width:100%; height:150px; object-fit:contain;">
    <h3>Pip</h3>
    <p><strong>Your curious learner</strong></p>
    <p>Pip has lots of questions and isn't afraid to ask them.</p>
  </div>
</div>

---

## 1. First, What's an API?

<details class="academy-collapsible-section">
<summary>🔌 What is an API?</summary>
<div class="academy-collapsible-content">

**Pip:** "Nova, I keep hearing people talk about APIs. What is an API?"

**Nova:** "Great question! Let's imagine you're ordering food at a restaurant."

Imagine this:

1. You look at the menu.
2. You tell the waiter what you want.
3. The waiter takes your order to the kitchen.
4. The kitchen prepares your food.
5. The waiter brings your food back.

An API works in a similar way!

An API is a way for two software applications to communicate and exchange information.

Think of it like this:

<div style="background:#f7f8f5; border:1px solid #e4e9e1; border-radius:16px; padding:22px; margin:24px 0;">
  <h3 style="text-align:center;">The Restaurant API</h3>
  <div style="display:grid; grid-template-columns:1fr 1fr 1fr; gap:8px; align-items:center; text-align:center;">
    <div style="background:#eaf2ec; padding:14px 8px; border-radius:12px;">
      <div style="font-size:30px;">👤</div>
      <strong>You</strong>
      <p style="font-size:13px;">Make a request</p>
    </div>
    <div style="background:#f0ecfa; padding:14px 8px; border-radius:12px;">
      <div style="font-size:30px;">🧑‍🍳</div>
      <strong>Waiter</strong>
      <p style="font-size:13px;">Carries the request</p>
    </div>
    <div style="background:#fff4df; padding:14px 8px; border-radius:12px;">
      <div style="font-size:30px;">🍽️</div>
      <strong>Kitchen</strong>
      <p style="font-size:13px;">Provides the result</p>
    </div>
  </div>
  <p style="text-align:center; margin-top:16px;"><strong>The waiter is like the API.</strong> It helps carry information between you and the kitchen.</p>
</div>

**Pip:** "So an API is like a messenger between two applications?"

**Nova:** "Exactly!"

For example, another application might use the Huddlehouse API to retrieve a list of projects.

The other application asks for information. Huddlehouse processes the request and sends back a response.

### Remember

An API allows applications to communicate with each other using an agreed set of rules.

</div>
</details>

## 2. What Is an Endpoint?

<details class="academy-collapsible-section">
<summary>📍 Understanding endpoints and URLs</summary>
<div class="academy-collapsible-content">

**Pip:** "Okay, I understand APIs. But what is an endpoint?"

**Nova:** "Think of an endpoint as a specific destination where an application can request something."

Imagine a building with different rooms:

- The kitchen is one destination.
- The conference room is another.
- The library is somewhere else.

Each room has a different purpose.

APIs work similarly. Different endpoints provide access to different resources or actions.

### Example: Huddlehouse API

Our fictional Huddlehouse API has several endpoints:

| Endpoint | What it does |
|---|---|
| `/workspaces` | Access workspaces |
| `/projects` | Access projects |
| `/documents` | Access documents |

These endpoints belong to the same API, but each one works with a different type of information.

### What does a complete API URL look like?

Let's look at an example:

<div style="background:#f7f8f5; border:1px solid #e4e9e1; border-radius:12px; padding:18px; margin:20px 0; overflow-wrap:anywhere;">
  <p style="font-size:12px; color:#68746b; margin-bottom:8px;">EXAMPLE API URL</p>
  <code style="font-size:14px;">https://api.huddlehouse.example/v1/projects</code>
  <hr style="border:0; border-top:1px solid #dce3da; margin:14px 0;">
  <p><strong>https://</strong> — The secure connection method</p>
  <p><strong>api.huddlehouse.example</strong> — The API server address</p>
  <p><strong>/v1</strong> — The API version</p>
  <p><strong>/projects</strong> — The endpoint</p>
</div>

**Pip:** "So if I want project information, I go to the projects endpoint?"

**Nova:** "You got it!"

### Remember

An endpoint is a specific URL path used to access a resource or perform an operation through an API.

</div>
</details>

## 3. How Do Requests and Responses Work?

<details class="academy-collapsible-section">
<summary>📨 Sending a request and receiving a response</summary>
<div class="academy-collapsible-content">

**Pip:** "How does another application actually ask Huddlehouse for information?"

**Nova:** "It sends something called a request."

A request is a message sent to an API asking it to do something.

The API processes that request and sends back a response.

Think of it like asking someone a question:

- You ask a question.
- They understand what you're asking.
- They give you an answer.

### The basic API workflow

<div style="background:#f7f8f5; border:1px solid #e4e9e1; border-radius:16px; padding:20px; margin:24px 0;">
  <h3 style="text-align:center;">How an API Request Works</h3>
  <div style="background:#eaf2ec; border-radius:12px; padding:16px; text-align:center;">
    <div style="font-size:28px;">💻</div>
    <strong>1. Application</strong>
    <p>Asks Huddlehouse for information.</p>
  </div>
  <div style="text-align:center; font-size:24px; padding:8px;">↓ Request</div>
  <div style="background:#f0ecfa; border-radius:12px; padding:16px; text-align:center;">
    <div style="font-size:28px;">🔌</div>
    <strong>2. Huddlehouse API</strong>
    <p>Receives and processes the request.</p>
  </div>
  <div style="text-align:center; font-size:24px; padding:8px;">↓ Response</div>
  <div style="background:#fff4df; border-radius:12px; padding:16px; text-align:center;">
    <div style="font-size:28px;">📦</div>
    <strong>3. Application</strong>
    <p>Receives the requested information.</p>
  </div>
</div>

### Meet the HTTP methods

HTTP methods tell an API what kind of action you want to perform.

| Method | Simple meaning | Example |
|---|---|---|
| GET | Retrieve information | View projects |
| POST | Create something | Create a project |
| PUT | Replace something | Replace a document |
| PATCH | Update part of something | Change a project name |
| DELETE | Remove something | Delete a project |

You don't need to memorize everything immediately.

For now, remember:

- GET = Get information
- POST = Create information
- PATCH = Change information
- DELETE = Remove information

### Let's look at a real example

Suppose Pip wants to retrieve a list of Huddlehouse projects.

The application sends:

```http
GET /v1/projects
```

Huddlehouse might respond with:

```json
{
  "data": [
    {
      "id": "project-123",
      "name": "Team Calendar",
      "status": "in_progress"
    },
    {
      "id": "project-456",
      "name": "Website Refresh",
      "status": "planned"
    }
  ]
}
```

This response contains two projects.

The information is formatted as JSON, which is a common way for applications to exchange structured data.

**Pip:** "So the request asks for projects, and the response gives us the projects?"

**Nova:** "Exactly!"

### Remember

A request asks an API to do something. A response tells the application what happened or returns the requested information.

</div>
</details>

## 4. What Is Authentication?

<details class="academy-collapsible-section">
<summary>🔐 Keeping API access secure</summary>
<div class="academy-collapsible-content">

**Pip:** "Wait! Can anyone ask Huddlehouse for project information?"

**Nova:** "Not necessarily. That's where authentication comes in."

Authentication is the process of checking who or what is trying to access a system.

Think about entering an office building.

You might need an access badge before you're allowed inside.

An API can use a similar approach.

### Meet the API key

An API key is a credential that helps identify an application or authorize its access.

Imagine Pip has an application that needs to retrieve Huddlehouse projects.

The application must provide valid authentication credentials when it sends its request.

For our fictional Huddlehouse API, we'll use a bearer token.

Example:

```http
GET /v1/projects
Authorization: Bearer YOUR_ACCESS_TOKEN
```

The token is included in the request header.

The API checks whether the credentials are valid and whether the request is allowed.

### What happens when authentication fails?

If the application sends an invalid or missing token, the API may respond:

```json
{
  "error": {
    "code": "unauthorized",
    "message": "Authentication is required."
  }
}
```

The application cannot access the requested resource until valid credentials are provided.

### Important security habits

- Never share access tokens publicly.
- Don't put credentials in screenshots or documentation examples.
- Store secrets in secure locations.
- Replace exposed credentials immediately.
- Use only the permissions an application needs.

**Pip:** "So an API token is like a key to a building. We shouldn't hand it to everyone!"

**Nova:** "Exactly. Protecting credentials is part of protecting the information behind the API."

### Remember

Authentication helps verify identity and control access to API resources.

</div>
</details>

## 5. How Do Developers Read API Documentation?

<details class="academy-collapsible-section">
<summary>📖 Finding your way around API documentation</summary>
<div class="academy-collapsible-content">

**Pip:** "Nova, how do developers know which endpoint to use and what information to send?"

**Nova:** "They read the API documentation!"

API documentation explains how an API works and how developers can use it.

Think of it like an instruction manual.

If you buy a new piece of furniture, the instructions help you understand which pieces go where and how to assemble everything.

API documentation does the same thing for software integrations.

### What should you look for?

When reading API documentation, look for:

| Documentation section | What it tells you |
|---|---|
| Overview | What the API does |
| Authentication | How to access the API |
| Endpoints | What resources are available |
| Parameters | What information you can send |
| Request examples | How to format a request |
| Response examples | What the API sends back |
| Error codes | What went wrong and how to fix it |

### Let's explore the Huddlehouse Developer Hub

Our fictional Developer Hub contains:

- API Quickstart
- Authentication
- API Reference
- Error Reference
- OpenAPI Specification

Each resource answers a different question.

For example:

- Need to get started? Read the Quickstart.
- Need to understand credentials? Read Authentication.
- Need to find an endpoint? Open the API Reference.
- Getting an error? Check the Error Reference.

**Pip:** "So the Developer Hub is like the instruction manual for connecting applications to Huddlehouse?"

**Nova:** "Exactly!"

### Remember

Good API documentation helps developers understand what an API does, how to use it, and what to do when something goes wrong.

</div>
</details>

## 6. What Is OpenAPI?

<details class="academy-collapsible-section">
<summary>📄 Understanding the OpenAPI specification</summary>
<div class="academy-collapsible-content">

**Pip:** "I found something called an OpenAPI specification in the Developer Hub. Is that another API?"

**Nova:** "Not quite! OpenAPI is a standard way to describe an API."

Think of it like a detailed blueprint.

A building blueprint shows:

- Where the rooms are
- How everything connects
- What each area is used for

An OpenAPI specification describes:

- Available endpoints
- Supported HTTP methods
- Required parameters
- Authentication requirements
- Request formats
- Response formats

### What does it look like?

Our fictional Huddlehouse API specification is written in YAML.

Here's a small example:

```yaml
paths:
  /projects:
    get:
      summary: List projects
      responses:
        "200":
          description: A list of projects
```

Let's break that down:

| Part | Meaning |
|---|---|
| `paths` | Lists available API paths |
| `/projects` | Identifies the projects endpoint |
| `get` | Describes a GET request |
| `summary` | Explains what the operation does |
| `responses` | Describes possible responses |
| `200` | Indicates a successful request |

### Why is OpenAPI useful?

OpenAPI specifications can help teams:

- Understand an API's structure
- Generate interactive API documentation
- Create client libraries
- Validate API requests and responses
- Share a consistent API contract

Our Huddlehouse Developer Hub uses an OpenAPI specification to power its interactive API reference.

**Pip:** "So the specification is like a blueprint that helps everyone understand how the API is built?"

**Nova:** "That's a great way to think about it!"

### Remember

OpenAPI describes an API in a structured format that tools and people can use to understand its behavior.

</div>
</details>

## 7. What Happens When Something Goes Wrong?

<details class="academy-collapsible-section">
<summary>🛠️ Understanding API errors and troubleshooting</summary>
<div class="academy-collapsible-content">

**Pip:** "Nova! My application tried to retrieve projects, but something went wrong!"

**Nova:** "Don't panic. APIs send error responses to help us understand what happened."

An HTTP status code is a number that describes the result of a request.

### Common API status codes

| Status code | Simple meaning | What to check |
|---|---|---|
| 200 | Success | The request worked |
| 201 | Created | A resource was created |
| 400 | Bad Request | Check the request format |
| 401 | Unauthorized | Check authentication |
| 403 | Forbidden | Check permissions |
| 404 | Not Found | Check the endpoint or resource ID |
| 409 | Conflict | Check for conflicting information |
| 422 | Validation Error | Check the submitted values |
| 500 | Server Error | The server encountered a problem |

### Let's solve a problem

Pip tries to retrieve a project but receives:

```json
{
  "error": {
    "code": "unauthorized",
    "message": "Authentication is required."
  }
}
```

**Pip:** "What does unauthorized mean?"

**Nova:** "It means the API couldn't verify your application's access."

Together, they check:

1. Did the application include an access token?
2. Is the token valid?
3. Has the token expired?
4. Does the application have the required permissions?

After fixing the missing token, Pip tries again.

This time, the API returns a successful response!

### A simple troubleshooting routine

When an API request fails:

1. Read the HTTP status code.
2. Read the error message.
3. Check the endpoint and HTTP method.
4. Review authentication and permissions.
5. Check required parameters and submitted data.
6. Try the request again after fixing the problem.

**Pip:** "So instead of guessing, I should use the error message to figure out what went wrong?"

**Nova:** "Exactly! Error messages are clues."

### Remember

API errors aren't just failures. They provide information that helps developers troubleshoot problems.

</div>
</details>

## 8. Putting It All Together

<details class="academy-collapsible-section">
<summary>🚀 Your first Huddlehouse integration</summary>
<div class="academy-collapsible-content">

Now let's imagine Nova and Pip are helping another application connect to Huddlehouse.

Their goal is simple:

**Display a list of Huddlehouse projects inside another application.**

Here's what they need to do.

<div style="background:#f7f8f5; border:1px solid #e4e9e1; border-radius:16px; padding:22px; margin:24px 0;">
  <h3 style="text-align:center;">The Integration Journey</h3>
  <div style="background:#eaf2ec; border-radius:12px; padding:16px; text-align:center; margin:10px 0;">
    <div style="font-size:28px;">📖</div>
    <strong>1. Read the documentation</strong>
    <p>Find the projects endpoint and understand how it works.</p>
  </div>
  <div style="text-align:center; font-size:24px;">↓</div>
  <div style="background:#f0ecfa; border-radius:12px; padding:16px; text-align:center; margin:10px 0;">
    <div style="font-size:28px;">🔐</div>
    <strong>2. Set up authentication</strong>
    <p>Obtain valid credentials and protect the access token.</p>
  </div>
  <div style="text-align:center; font-size:24px;">↓</div>
  <div style="background:#fff4df; border-radius:12px; padding:16px; text-align:center; margin:10px 0;">
    <div style="font-size:28px;">📨</div>
    <strong>3. Send the request</strong>
    <p>Use GET to request the projects endpoint.</p>
  </div>
  <div style="text-align:center; font-size:24px;">↓</div>
  <div style="background:#e8f0fa; border-radius:12px; padding:16px; text-align:center; margin:10px 0;">
    <div style="font-size:28px;">📦</div>
    <strong>4. Process the response</strong>
    <p>Read the returned project information.</p>
  </div>
  <div style="text-align:center; font-size:24px;">↓</div>
  <div style="background:#eaf2ec; border-radius:12px; padding:16px; text-align:center; margin:10px 0;">
    <div style="font-size:28px;">🎉</div>
    <strong>5. Handle any errors</strong>
    <p>Use status codes and messages to troubleshoot problems.</p>
  </div>
</div>

**Pip:** "I think I understand now! We read the documentation, authenticate, send a request, and process the response."

**Nova:** "Exactly! That's the foundation of working with APIs."

### One last thing

The examples in this course describe our fictional Huddlehouse API. They help explain how API integrations work, but they don't connect to a live backend.

The important thing is understanding the workflow and knowing where to find the information developers need.

</div>
</details>

## 9. What You've Learned

<details class="academy-collapsible-section">
<summary>⭐ Review the important concepts</summary>
<div class="academy-collapsible-content">

Let's recap everything!

| Concept | Simple explanation |
|---|---|
| API | A way for applications to communicate |
| Endpoint | A specific destination in an API |
| Request | A message asking an API to do something |
| Response | The information returned by an API |
| HTTP method | Describes the action being requested |
| Authentication | Helps verify identity and control access |
| API documentation | Instructions for using an API |
| OpenAPI | A structured description of an API |
| Status code | A number describing the result of a request |

**Pip:** "That was a lot of new words!"

**Nova:** "It was! But now you know what they mean and how they fit together."

You don't need to become an expert overnight.

The best way to learn is to explore the documentation, follow examples, ask questions, and practice.

</div>
</details>

---

## Ready for Your Knowledge Check?

<div style="background:#f2f6f1; border:1px solid #dce8dc; border-radius:16px; padding:24px; margin:24px 0; text-align:center;">
  <div style="font-size:42px;">🎓 👽</div>
  <h3>You've completed the Developer Workflows learning material!</h3>
  <p>Now it's time to test what you've learned.</p>
  <p><strong>Nova and Pip are rooting for you!</strong></p>
  <p style="margin-top:20px;">
    <a href="developer-workflows-quiz.html" style="display:inline-block; background:#536f5b; color:white; padding:13px 22px; border-radius:10px; text-decoration:none; font-weight:700;">Take the Developer Workflows Knowledge Check →</a>
  </p>
</div>