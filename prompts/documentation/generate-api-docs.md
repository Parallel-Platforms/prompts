# Generate API Documentation

Generate comprehensive API documentation for the provided code.

## Documentation Structure

### Overview
- **API Purpose**: What the API does
- **Base URL**: API endpoint base URL
- **Version**: API version
- **Authentication**: How to authenticate requests

### Authentication
```http
# Authentication example
Authorization: Bearer {token}
```
- Authentication methods
- How to obtain credentials
- Token refresh process
- Security considerations

### Endpoints

For each endpoint, include:

#### Endpoint Name
**Description**: What this endpoint does

**HTTP Method**: `GET` | `POST` | `PUT` | `PATCH` | `DELETE`

**URL**: `/api/v1/resource/{id}`

**URL Parameters**:
- `id` (required): Description of the parameter
- `filter` (optional): Description of the parameter

**Query Parameters**:
- `page` (integer, optional): Page number for pagination. Default: 1
- `limit` (integer, optional): Items per page. Default: 20, Max: 100

**Request Headers**:
```http
Content-Type: application/json
Authorization: Bearer {token}
```

**Request Body**:
```json
{
  "field1": "string",
  "field2": 123,
  "field3": {
    "nested": "value"
  }
}
```

**Success Response**:
- **Code**: 200 OK
- **Content**:
```json
{
  "id": "123",
  "field1": "value",
  "field2": 456,
  "createdAt": "2024-01-01T00:00:00Z"
}
```

**Error Responses**:
- **Code**: 400 Bad Request
  - **Content**: `{ "error": "Invalid input", "details": [...] }`
- **Code**: 401 Unauthorized
  - **Content**: `{ "error": "Invalid token" }`
- **Code**: 404 Not Found
  - **Content**: `{ "error": "Resource not found" }`
- **Code**: 500 Internal Server Error
  - **Content**: `{ "error": "Server error" }`

**Example Request**:
```bash
curl -X POST https://api.example.com/v1/resource \
  -H "Authorization: Bearer {token}" \
  -H "Content-Type: application/json" \
  -d '{
    "field1": "value",
    "field2": 123
  }'
```

**Example Response**:
```json
{
  "id": "123",
  "status": "success"
}
```

### Data Models

#### Model Name
```json
{
  "field1": "string (required) - Description",
  "field2": "integer (optional) - Description",
  "field3": {
    "nested": "string - Description"
  },
  "createdAt": "ISO 8601 datetime",
  "updatedAt": "ISO 8601 datetime"
}
```

### Rate Limiting
- Request limits
- Rate limit headers
- Handling rate limit errors

### Pagination
- Pagination parameters
- Response format
- Navigation links

### Error Handling
- Error response format
- Common error codes
- Error messages

### Webhooks (if applicable)
- Available webhook events
- Payload structure
- Verification process

### SDKs and Libraries
- Official SDKs
- Community libraries
- Code examples in different languages

### Changelog
- API version history
- Breaking changes
- Deprecation notices

## Best Practices
- Use clear, descriptive names
- Provide realistic examples
- Document all parameters
- Include response codes
- Show error cases
- Keep it up-to-date
- Use consistent formatting

Please generate API documentation that is:
1. Complete and accurate
2. Easy to understand
3. Includes practical examples
4. Follows OpenAPI/Swagger standards (if applicable)
5. Developer-friendly
