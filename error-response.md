# REST API Best Practices

Standardized rest api error response.

## Error Responses

### 1. Input Validation Error

HTTP Status Code: 400 Bad Request

This status code indicates that the server could not understand the client's request due to invalid syntax or missing parameters. Input validation errors fall into this category as they are typically caused by client mistakes.

```json
{
  "error": {
    "code": "E002",
    "message": "Invalid input data",
    "details": [
        {
            "field": "email",
            "value": "user@example.com",
            "description": "The provided email address is not valid",
        }
    ]
  }
}
```

### 2. Business Logic Error

HTTP Status Code: 422 Unprocessable Entity

This status code indicates that the server understands the request, but it cannot process it because the provided data violates business rules or requirements. This status code is often used for business logic errors where the request is semantically incorrect.

```json
{
  "error": {
    "code": "E101",
    "message": "Insufficient funds",
    "details": {
      "account": "123456789",
      "required_amount": 100.00,
      "available_balance": 75.50
    }
  }
}

```
### 3. Unexpected Error

HTTP Status Code: 500 Internal Server Error

This status code indicates that an unexpected condition was encountered on the server, and no more specific message is suitable. Unexpected errors are typically considered server-side issues.

```json
{
  "error": {
    "code": "E500",
    "message": "Internal Server Error",
    "timestamp": "2024-01-29T12:34:56Z",
    "contact_support": "https://example.com/support"
  }
}
```

### 4. Error Code Table

This error code table outlines various types of errors that may occur in the system, providing detailed information to aid in troubleshooting and resolution.

| Error Type              | HTTP Status Code           | Error Code | Message                 | Description                                                                                               |
|-------------------------|----------------------------|------------|-------------------------|-----------------------------------------------------------------------------------------------------------|
| Input Validation Error  | 400 Bad Request            | E002       | Invalid input data      | The provided email address is not valid.                                                                  |
| Business Logic Error    | 422 Unprocessable Entity   | E101       | Insufficient funds      | Account 123456789 has an available balance of $75.50, but $100.00 is required.                           |
| Unexpected Error        | 500 Internal Server Error  | E500       | Internal Server Error   | An unexpected condition was encountered on the server. Check the timestamp for the occurrence. [Contact Support](https://example.com/support) |
