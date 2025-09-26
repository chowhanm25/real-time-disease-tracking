# API Documentation

## Overview

The Real-Time Disease Tracking System provides a comprehensive RESTful API for accessing disease outbreak data, submitting reports, and managing system resources. This API enables integration with external systems, mobile applications, and research tools.

**Base URL**: `http://your-domain.com/api/`  
**API Version**: v1  
**Authentication**: Token-based authentication required for write operations

## Authentication

### Token Authentication

Most endpoints require authentication. Include the token in the request header:

```http
Authorization: Token your_auth_token_here
```

### Obtaining a Token

**POST** `/api/auth/token/`

```json
{
    "username": "your_username",
    "password": "your_password"
}
```

**Response:**
```json
{
    "token": "your_auth_token_here",
    "user_id": 1,
    "username": "your_username"
}
```

## Disease Management

### List All Diseases

**GET** `/api/diseases/`

Returns a list of all diseases in the system.

**Response:**
```json
{
    "count": 45,
    "next": "http://api.example.com/api/diseases/?page=2",
    "previous": null,
    "results": [
        {
            "id": 1,
            "name": "COVID-19",
            "description": "Coronavirus Disease 2019",
            "severity_level": "high",
            "created_at": "2025-01-15T10:30:00Z"
        }
    ]
}
```

### Get Disease Details

**GET** `/api/diseases/{id}/`

**Response:**
```json
{
    "id": 1,
    "name": "COVID-19",
    "description": "Coronavirus Disease 2019",
    "severity_level": "high",
    "symptoms": [
        {
            "id": 1,
            "name": "Fever",
            "description": "High body temperature"
        }
    ],
    "total_reports": 1250,
    "recent_reports": 45,
    "created_at": "2025-01-15T10:30:00Z"
}
```

## Disease Reports

### Submit Disease Report

**POST** `/api/reports/`

**Authentication Required**

**Request Body:**
```json
{
    "disease_id": 1,
    "symptoms": [1, 2, 3],
    "conditions": [1],
    "country": "Canada",
    "city": "Windsor",
    "latitude": 42.3149,
    "longitude": -83.0364,
    "additional_info": "Optional additional information"
}
```

**Response:**
```json
{
    "id": 123,
    "disease": {
        "id": 1,
        "name": "COVID-19"
    },
    "symptoms": [
        {"id": 1, "name": "Fever"},
        {"id": 2, "name": "Cough"}
    ],
    "country": "Canada",
    "city": "Windsor",
    "status": "pending",
    "created_at": "2025-03-15T14:30:00Z"
}
```

### List Disease Reports

**GET** `/api/reports/`

Query parameters:
- `disease_id`: Filter by disease ID
- `country`: Filter by country name
- `city`: Filter by city name
- `start_date`: Filter reports after this date (YYYY-MM-DD)
- `end_date`: Filter reports before this date (YYYY-MM-DD)
- `page`: Page number for pagination

**Response:**
```json
{
    "count": 1250,
    "next": "http://api.example.com/api/reports/?page=2",
    "previous": null,
    "results": [
        {
            "id": 123,
            "disease": "COVID-19",
            "country": "Canada",
            "city": "Windsor",
            "report_date": "2025-03-15T14:30:00Z",
            "status": "verified"
        }
    ]
}
```

## Analytics and Statistics

### Disease Statistics by Country

**GET** `/api/analytics/countries/`

Query parameters:
- `disease_id`: Specific disease ID (optional)
- `start_date`: Start date for statistics (YYYY-MM-DD)
- `end_date`: End date for statistics (YYYY-MM-DD)

**Response:**
```json
{
    "total_countries": 45,
    "data": [
        {
            "country": "Canada",
            "total_reports": 234,
            "diseases": [
                {
                    "disease_name": "COVID-19",
                    "count": 189,
                    "percentage": 80.8
                }
            ],
            "trend": "decreasing",
            "last_report": "2025-03-15T14:30:00Z"
        }
    ]
}
```

### Global Dashboard Data

**GET** `/api/analytics/dashboard/`

**Response:**
```json
{
    "total_reports": 12450,
    "total_diseases": 45,
    "active_countries": 67,
    "recent_reports": 156,
    "top_diseases": [
        {
            "name": "COVID-19",
            "count": 5430,
            "percentage": 43.6
        }
    ],
    "geographic_distribution": [
        {
            "country": "Canada",
            "count": 234,
            "percentage": 1.9
        }
    ],
    "last_updated": "2025-03-15T15:30:00Z"
}
```

## User Management

### User Profile

**GET** `/api/users/profile/`

**Authentication Required**

**Response:**
```json
{
    "id": 1,
    "username": "john_doe",
    "email": "john@example.com",
    "first_name": "John",
    "last_name": "Doe",
    "country": "Canada",
    "city": "Windsor",
    "total_reports": 5,
    "last_report": "2025-03-10T10:30:00Z",
    "account_created": "2025-01-15T09:00:00Z"
}
```

## Error Handling

### Error Response Format

All API errors follow this format:

```json
{
    "error": {
        "code": "VALIDATION_ERROR",
        "message": "The submitted data is invalid",
        "details": {
            "field_name": ["This field is required."]
        }
    }
}
```

### Common Error Codes

| Code | HTTP Status | Description |
|------|-------------|-------------|
| `AUTHENTICATION_REQUIRED` | 401 | Authentication token required |
| `PERMISSION_DENIED` | 403 | Insufficient permissions |
| `NOT_FOUND` | 404 | Resource not found |
| `VALIDATION_ERROR` | 400 | Request data validation failed |
| `RATE_LIMITED` | 429 | Too many requests |
| `SERVER_ERROR` | 500 | Internal server error |

## Rate Limiting

- **Authenticated users**: 100 requests per minute
- **Anonymous users**: 20 requests per minute
- **Report submissions**: 1 per user per month

Rate limit headers are included in responses:
```
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 95
X-RateLimit-Reset: 1647345600
```

## Data Formats

### Date Format
All dates are in ISO 8601 format: `YYYY-MM-DDTHH:MM:SSZ`

### Coordinates
- Latitude: -90 to 90 (decimal degrees)
- Longitude: -180 to 180 (decimal degrees)

### Pagination
Paginated responses include:
- `count`: Total number of results
- `next`: URL for next page
- `previous`: URL for previous page
- `results`: Array of results

## Testing the API

### Using cURL

```bash
# Get disease list
curl -X GET "http://localhost:8000/api/diseases/"

# Submit a report (with authentication)
curl -X POST "http://localhost:8000/api/reports/" \
  -H "Authorization: Token your_token_here" \
  -H "Content-Type: application/json" \
  -d '{
    "disease_id": 1,
    "symptoms": [1, 2],
    "country": "Canada",
    "city": "Windsor"
  }'
```

## Support

For API support:
1. Check this documentation
2. Review the Django logs for detailed error messages
3. Create an issue in the GitHub repository
4. Contact the development team