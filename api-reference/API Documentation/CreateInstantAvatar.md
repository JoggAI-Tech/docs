---
title: 'Create Instant Avatar'
description: 'How to create instant avatar by upload video.'
---

```markdown
# Jogg AI API Documentation

## Base URL

`https://api-services.jogg.ai`

## Create Custom Avatar

Create a new custom avatar from a video.

### Endpoint

```
POST /open/avatar/create
```

### Headers

| Key         | Value            |
|-------------|------------------|
| X-API-Key   | <your_api_key>   |
| Content-Type| application/json |

### Request Body

```json
{
    "origin_url": "string",  // Required. URL of the source video
    "name": "string"         // Required. Name for the avatar
}
```

### Response

```json
{
    "code": 0,
    "msg": "success",
    "data": {
        "id": 123  // The ID of the created avatar
    }
}
```

### Error Codes

- 401: Unauthorized - Invalid API key
- 400: Bad Request - Missing required fields
- 500: Internal Server Error

## Delete Custom Avatar

Delete an existing custom avatar.

### Endpoint

```
DELETE /open/avatar/delete
```

### Headers

| Key         | Value            |
|-------------|------------------|
| X-API-Key   | <your_api_key>   |
| Content-Type| application/json |

### Request Body

```json
{
    "id": 123  // Required. The ID of the avatar to delete
}
```

### Response

Success:
```json
{
    "code": 0,
    "msg": "success"
}
```

### Error Codes

- 401: Unauthorized - Invalid API key
- 400: Bad Request - Invalid avatar ID
- 404: Not Found - Avatar not found
- 500: Internal Server Error
