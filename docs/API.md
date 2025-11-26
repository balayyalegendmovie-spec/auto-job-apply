# Auto Job Apply - API Documentation

## Base URL
```
https://api.yourproject.com/v1
```

## Authentication
All requests require a JWT bearer token in the Authorization header:
```
Authorization: Bearer <your_jwt_token>
```

## Endpoints

### User Profile

#### GET /profile
Retrieve current user's profile

**Response:**
```json
{
  "id": "uuid",
  "email": "user@example.com",
  "fullname": "John Doe",
  "skills": ["Python", "React", "Node.js"],
  "desiredRoles": ["Software Engineer", "Full Stack"],
  "location": "Remote"
}
```

#### PUT /profile
Update user profile

**Request Body:**
```json
{
  "fullname": "John Doe",
  "skills": ["Python", "React"],
  "desiredRoles": ["Software Engineer"]
}
```

### Jobs

#### GET /jobs
List all jobs with filters

**Query Parameters:**
- `role`: Filter by job role
- `location`: Filter by location
- `skills`: Filter by required skills
- `page`: Pagination

**Response:**
```json
{
  "jobs": [
    {
      "id": "uuid",
      "title": "Software Engineer",
      "company": "Tech Corp",
      "location": "Remote",
      "skills": ["Python", "React"]
    }
  ],
  "total": 100
}
```

### Applications

#### GET /applications
List user's applications

#### POST /applications/submit
Submit a job application

**Request Body:**
```json
{
  "jobId": "uuid",
  "resumeId": "uuid"
}
```

## Error Handling
All errors return appropriate HTTP status codes:
- `400`: Bad Request
- `401`: Unauthorized
- `403`: Forbidden
- `404`: Not Found
- `500`: Internal Server Error

## Rate Limiting
- 100 requests per 15 minutes per user
- Returns `429 Too Many Requests` when exceeded
