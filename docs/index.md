# Welcome to Supportify

**Supportify** is a tech company dedicated to simplifying customer support for businesses of all sizes. Our **Supportify APIs** provides developers with the tools they need to integrate powerful support ticket management, user interaction tracking, and automated workflows into their applications. Whether you're a SaaS company, e-commerce platform, or help desk, Supportify helps you deliver exceptional support experiences.

## Getting Started

Welcome to **Supportify API** version 1.0.0! Currently, the API includes one resource: the **users** resource. No authentication is required to make calls to the endpoints in this resource. Let’s walk you through creating a sample support ticket as a user.

### Creating a Support Ticket
* `baseUrl` - [https://jogmg-backend.onrender.com](baseUrl)

To create a support ticket, send a `POST` request to the `/users` endpoint with the following JSON data in your request body:

```json
{
    "name":"Gabriel",
    "email":"gabriel@yahoo.com",
    "subject":"Client Rent",
    "message":"Client has refused to pay her rent for the past 365 days"
}
```

### Example Request
```JavaScript
async function sendRequest() {
  const url = "https://jogmg-backend.onrender.com/users";
  const data = {
    name: "Gabriel",
    email: "gabriel@yahoo.com",
    subject: "Client Rent",
    message: "Client has refused to pay her rent for the past 365 days"
  };

  try {
    const response = await fetch(url, {
      method: "POST",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify(data)
    });

    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    const responseData = await response.json();
    console.log("Request successful:", responseData);
  } catch (error) {
    console.error("Error:", error);
  }
}

// Call the function
sendRequest();
```

### Example Response
```json
{
    "error": false,
    "statusCode": 201,
    "message": "User created successfully",
    "data": {
        "name": "Gabriel",
        "email": "gabriel@yahoo.com",
        "subject": "Client Rent",
        "message": "Client has refused to pay her rent for the past 365 days",
        "_id": "67df14b8838694a04c0f3771",
        "createdAt": "2025-03-22T19:51:20.559Z",
        "updatedAt": "2025-03-22T19:51:20.559Z",
        "__v": 0
    }
}
```

**Voila!** You’ve just made your first request to the Supportify API. This example demonstrates how users can send feedback by creating support tickets.

Now that you’ve seen how it works, feel free to explore the [API Reference](api-reference.md) to discover more endpoints available in the users resource. Whether you’re managing tickets, updating user information, or fetching support history, the [API Reference](api-reference.md) has everything you need to get started.

## Errors

The error codes follow the standard HTTP conventions. Below is a table of common status codes you might encounter when using the Supportify API. While some of these codes indicate success (like 200 and 201), others represent errors that you should handle in your application.

| First Header | Second Header | Third Header |
| ------------ | ------------- | ------------ |
| 200 | OK | The request was successful, and the response contains the requested data. |
| 201| Created | The request was successful, and a new resource was created|
| 404| Not Found | The requested resource (e.g., a user or ticket) does not exist.|
| 500| Internal Server Error | Something went wrong on the server. Please try again later.|