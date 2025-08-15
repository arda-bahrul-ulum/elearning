# E-Learning Platform

A comprehensive e-learning platform built with Golang backend and React frontend, featuring course management, video streaming, quizzes, payments, and admin panel.

## 🚀 Features

### Core Features

- **Authentication & Authorization**: JWT-based auth with refresh tokens, role-based access (Admin, Instructor, Student)
- **Course Management**: Create, edit, and manage courses with sections and lessons
- **Media Handling**: Video upload, transcoding, and S3-compatible storage with CDN
- **Learning Flow**: Progress tracking, lesson completion, video position saving
- **Quiz System**: Multiple choice, essay, and code submission quizzes with auto-grading
- **Payment Integration**: Midtrans/Stripe/PayPal integration for course purchases
- **Notifications**: Email and in-app notification system
- **Admin Panel**: Comprehensive dashboard for user, course, and analytics management

### User Roles

- **Students**: Enroll in courses, track progress, take quizzes, view certificates
- **Instructors**: Create courses, manage content, view student progress, grade assignments
- **Admins**: Full system access, user management, analytics, content moderation

## 🛠️ Tech Stack

### Backend

- **Framework**: Golang with Gin HTTP framework
- **Database**: PostgreSQL with GORM ORM
- **Cache**: Redis for session storage and caching
- **Authentication**: JWT tokens with refresh token rotation
- **Storage**: S3-compatible storage (MinIO/AWS S3)
- **Background Jobs**: Worker goroutines with persistent queues
- **Migrations**: golang-migrate for database versioning

### Frontend

- **Framework**: React 18 with Vite
- **Styling**: Tailwind CSS with Headless UI components
- **State Management**: Redux Toolkit with React Query
- **Routing**: React Router DOM v6
- **Forms**: React Hook Form with validation
- **Charts**: Recharts for analytics dashboards

### DevOps

- **Containerization**: Docker & Docker Compose
- **Development**: Hot reload for both backend and frontend
- **Database**: PostgreSQL 15 with automated migrations
- **Object Storage**: MinIO for local S3-compatible storage

## 📦 Project Structure

```
elearning/
├── backend/                    # Golang backend
│   ├── cmd/server/            # Application entry point
│   ├── internal/              # Internal packages
│   │   ├── config/           # Configuration management
│   │   ├── database/         # Database connection & migrations
│   │   ├── models/           # Database models
│   │   ├── repositories/     # Data access layer
│   │   ├── services/         # Business logic layer
│   │   ├── handlers/         # HTTP handlers
│   │   ├── middleware/       # HTTP middleware
│   │   ├── utils/            # Utility functions
│   │   └── workers/          # Background workers
│   ├── migrations/           # SQL migration files
│   ├── pkg/                  # Reusable packages
│   └── Dockerfile
├── frontend/                  # React frontend
│   ├── src/
│   │   ├── components/       # Reusable UI components
│   │   ├── pages/            # Page components
│   │   ├── hooks/            # Custom React hooks
│   │   ├── services/         # API services
│   │   ├── store/            # Redux store & slices
│   │   ├── utils/            # Utility functions
│   │   └── styles/           # CSS styles
│   └── Dockerfile
├── docker-compose.yml        # Multi-container setup
└── README.md

backend/
├── cmd/
│   └── server/
│       └── main.go                 # Application entry point
├── internal/
│   ├── config/
│   │   └── config.go              # Configuration management
│   ├── database/
│   │   ├── connection.go          # Database connection
│   │   └── migrations/            # SQL migration files
│   ├── models/
│   │   ├── user.go               # User model
│   │   ├── course.go             # Course model
│   │   ├── lesson.go             # Lesson model
│   │   ├── enrollment.go         # Enrollment model
│   │   ├── quiz.go               # Quiz model
│   │   ├── payment.go            # Payment model
│   │   └── notification.go       # Notification model
│   ├── repositories/
│   │   ├── interfaces/
│   │   │   ├── user_repository.go
│   │   │   ├── course_repository.go
│   │   │   ├── lesson_repository.go
│   │   │   ├── enrollment_repository.go
│   │   │   ├── quiz_repository.go
│   │   │   ├── payment_repository.go
│   │   │   └── notification_repository.go
│   │   └── implementations/
│   │       ├── user_repository.go
│   │       ├── course_repository.go
│   │       ├── lesson_repository.go
│   │       ├── enrollment_repository.go
│   │       ├── quiz_repository.go
│   │       ├── payment_repository.go
│   │       └── notification_repository.go
│   ├── services/
│   │   ├── interfaces/
│   │   │   ├── auth_service.go
│   │   │   ├── user_service.go
│   │   │   ├── course_service.go
│   │   │   ├── lesson_service.go
│   │   │   ├── enrollment_service.go
│   │   │   ├── quiz_service.go
│   │   │   ├── payment_service.go
│   │   │   ├── media_service.go
│   │   │   └── notification_service.go
│   │   └── implementations/
│   │       ├── auth_service.go
│   │       ├── user_service.go
│   │       ├── course_service.go
│   │       ├── lesson_service.go
│   │       ├── enrollment_service.go
│   │       ├── quiz_service.go
│   │       ├── payment_service.go
│   │       ├── media_service.go
│   │       └── notification_service.go
│   ├── handlers/
│   │   ├── auth_handler.go
│   │   ├── user_handler.go
│   │   ├── course_handler.go
│   │   ├── lesson_handler.go
│   │   ├── enrollment_handler.go
│   │   ├── quiz_handler.go
│   │   ├── payment_handler.go
│   │   ├── media_handler.go
│   │   └── admin_handler.go
│   ├── middleware/
│   │   ├── auth.go               # JWT authentication
│   │   ├── cors.go               # CORS handling
│   │   ├── logger.go             # Request logging
│   │   └── rate_limiter.go       # Rate limiting
│   ├── utils/
│   │   ├── jwt.go                # JWT utilities
│   │   ├── hash.go               # Password hashing
│   │   ├── email.go              # Email utilities
│   │   ├── s3.go                 # S3 utilities
│   │   └── validator.go          # Input validation
│   └── workers/
│       ├── media_processor.go    # Media processing worker
│       ├── email_worker.go       # Email sending worker
│       └── notification_worker.go # Notification worker
├── migrations/
│   ├── 000001_create_users.up.sql
│   ├── 000001_create_users.down.sql
│   ├── 000002_create_courses.up.sql
│   ├── 000002_create_courses.down.sql
│   └── ...
├── pkg/
│   ├── logger/
│   │   └── logger.go             # Structured logging
│   └── cache/
│       └── redis.go              # Redis cache client
├── scripts/
│   ├── migrate.sh                # Migration script
│   └── seed.sql                  # Database seeding
├── tmp/                          # Temporary file uploads
├── Dockerfile
├── go.mod
├── go.sum
├── .env.example
└── README.md
```

## 🚦 Getting Started

### Prerequisites

- Docker & Docker Compose
- Go 1.21+ (for local development)
- Node.js 18+ (for local development)

### Quick Start with Docker

1. **Clone the repository**

```bash
git clone <repository-url>
cd elearning-platform
```

2. **Set up environment variables**

```bash
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env
```

3. **Start all services**

```bash
docker-compose up -d
```

4. **Run database migrations**

```bash
docker-compose exec backend migrate -path ./migrations -database "postgres://postgres:password@postgres:5432/elearning?sslmode=disable" up
```

5. **Access the application**

- Frontend: http://localhost:3000
- Backend API: http://localhost:8080
- MinIO Console: http://localhost:9001 (minioadmin/minioadmin123)

### Local Development Setup

#### Backend Setup

```bash
cd backend

# Install dependencies
go mod download

# Set up environment
cp .env.example .env

# Run database migrations
migrate -path ./migrations -database "your-db-url" up

# Start the server
go run cmd/server/main.go
```

#### Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev
```

## 📋 Environment Configuration

### Backend (.env)

```env
# Server
ENVIRONMENT=development
PORT=8080

# Database
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=password
DB_NAME=elearning

# Redis
REDIS_HOST=localhost
REDIS_PORT=6379

# JWT
JWT_SECRET=your-super-secret-jwt-key
JWT_EXPIRATION_HOURS=1
REFRESH_TOKEN_EXP_DAYS=30

# S3 Storage
S3_ENDPOINT=http://localhost:9000
S3_ACCESS_KEY=minioadmin
S3_SECRET_KEY=minioadmin123
S3_BUCKET=elearning-media

# SMTP
SMTP_HOST=smtp.mailtrap.io
SMTP_PORT=587
SMTP_USER=your-mailtrap-user
SMTP_PASS=your-mailtrap-pass

# URLs
APP_URL=http://localhost:8080
FRONTEND_URL=http://localhost:3000
```

### Frontend (.env)

```env
VITE_API_URL=http://localhost:8080
VITE_APP_NAME=EduPlatform
```

## 🔧 API Documentation

### Authentication Endpoints

- `POST /api/v1/auth/register` - User registration
- `POST /api/v1/auth/login` - User login
- `POST /api/v1/auth/refresh` - Refresh access token
- `POST /api/v1/auth/logout` - User logout
- `POST /api/v1/auth/verify-email` - Verify email address
- `POST /api/v1/auth/forgot-password` - Request password reset
- `POST /api/v1/auth/reset-password` - Reset password

### Course Endpoints

- `GET /api/v1/courses` - List all courses
- `GET /api/v1/courses/:id` - Get course details
- `POST /api/v1/courses` - Create new course (Instructor/Admin)
- `PUT /api/v1/courses/:id` - Update course (Instructor/Admin)
- `DELETE /api/v1/courses/:id` - Delete course (Instructor/Admin)

### User Endpoints

- `GET /api/v1/users/profile` - Get user profile
- `PUT /api/v1/users/profile` - Update user profile
- `POST /api/v1/users/avatar` - Upload avatar
- `GET /api/v1/users/dashboard` - Get user dashboard
- `GET /api/v1/users/enrollments` - Get user enrollments

## 🧪 Testing

### Backend Tests

```bash
cd backend
go test ./...
```

### Frontend Tests

```bash
cd frontend
npm run test
```

## 🚢 Deployment

### Production Docker Build

```bash
# Build production images
docker-compose -f docker-compose.prod.yml build

# Deploy
docker-compose -f docker-compose.prod.yml up -d
```

### Manual Deployment

#### Backend Deployment

```bash
cd backend

# Build binary
go build -o elearning-server cmd/server/main.go

# Run migrations
migrate -path ./migrations -database "production-db-url" up

# Start server
./elearning-server
```

#### Frontend Deployment

```bash
cd frontend

# Build for production
npm run build

# Serve static files (nginx/apache)
# Copy dist/ folder to web server
```

## 🔒 Security Features

- **Authentication**: JWT with refresh token rotation
- **Authorization**: Role-based access control (RBAC)
- **Rate Limiting**: API rate limiting with Redis
- **Input Validation**: Request validation and sanitization
- **Security Headers**: CORS, XSS protection, CSP headers
- **Password Security**: Bcrypt hashing with salt
- **SQL Injection Protection**: GORM ORM with prepared statements

## 🎯 Performance Optimizations

- **Caching**: Redis caching for frequently accessed data
- **Database**: Connection pooling and query optimization
- **CDN**: S3-compatible storage with CDN integration
- **Code Splitting**: Frontend code splitting for faster loading
- **Image Optimization**: Automated image compression and format conversion
- **Background Jobs**: Async processing for heavy operations

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

For support and questions:

- Create an issue on GitHub
- Check the documentation
- Contact the development team

## 🗺️ Roadmap

- [ ] Mobile app (React Native)
- [ ] Advanced analytics dashboard
- [ ] Live streaming classes
- [ ] AI-powered course recommendations
- [ ] Multi-language support
- [ ] Advanced quiz types (drag-drop, matching)
- [ ] Certificate generation system
- [ ] Discussion forums
- [ ] Assignment submission system
- [ ] Gamification features
