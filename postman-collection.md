# API Documentation

## Base URL
`http://localhost:8000/api`

## Authentication Endpoints

### Register
- **URL**: `/register`
- **Method**: `POST`
- **Headers**: 
  - Content-Type: application/json
- **Body**:
```json
{
    "name": "Test User",
    "email": "test@example.com",
    "password": "password123",
    "password_confirmation": "password123"
}
```
- **Success Response**: 
  - Status Code: 201
  - Response:
```json
{
    "message": "Registration successful",
    "user": {
        "id": 1,
        "name": "Test User",
        "email": "test@example.com"
    },
    "token": "1|abcdef..."
}
```

### Login
- **URL**: `/login`
- **Method**: `POST`
- **Headers**: 
  - Content-Type: application/json
- **Body**:
```json
{
    "email": "test@example.com",
    "password": "password123"
}
```
- **Success Response**: 
  - Status Code: 200
  - Response:
```json
{
    "message": "Login successful",
    "user": {
        "id": 1,
        "name": "Test User",
        "email": "test@example.com"
    },
    "token": "1|abcdef..."
}
```

### Get User Info
- **URL**: `/user`
- **Method**: `GET`
- **Headers**: 
  - Authorization: Bearer {token}
- **Success Response**: 
  - Status Code: 200
  - Response:
```json
{
    "id": 1,
    "name": "Test User",
    "email": "test@example.com"
}
```

### Logout
- **URL**: `/logout`
- **Method**: `POST`
- **Headers**: 
  - Authorization: Bearer {token}
- **Success Response**: 
  - Status Code: 200
  - Response:
```json
{
    "message": "Logged out successfully"
}
```

## Rate Limiting
- API her kullanıcı için dakikada maksimum 10 istek ile sınırlandırılmıştır
- Limit aşıldığında 429 Too Many Requests hatası döner
