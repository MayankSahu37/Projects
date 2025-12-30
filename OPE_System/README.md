# Centralized Protected Exam Conductor System

A secure, web-based platform for conducting online coding examinations with comprehensive monitoring and anti-cheating measures.

## Features

- **Secure Authentication**: JWT-based authentication for students and teachers
- **Real-time Monitoring**: Live tracking of student activities during exams
- **Code Execution**: In-browser code editor with compilation and execution
- **Anti-cheating Measures**: Tab switching detection, navigation restrictions
- **Question Management**: CRUD operations for coding questions
- **Exam Management**: Create, configure, and manage coding exams
- **Grading System**: Review submissions and assign grades

## Technology Stack

- **Backend**: Spring Boot 3.5.6, Spring Security, Spring Data JPA, Spring WebSocket
- **Frontend**: HTML5, CSS3, JavaScript ES6+, Monaco Editor
- **Database**: MySQL 8.0+
- **Authentication**: JWT (JSON Web Tokens)
- **Real-time Communication**: WebSocket with STOMP protocol
- **Build Tool**: Maven 3.8+
- **Java Version**: OpenJDK 17

## Prerequisites

- Java 17 or higher
- MySQL 8.0 or higher
- Maven 3.8 or higher

## Setup Instructions

### 1. Database Setup

1. Install MySQL and create a database named `exam_db`
2. Update database credentials in `src/main/resources/application.properties`

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/exam_db
spring.datasource.username=your_username
spring.datasource.password=your_password
```

### 2. Code Execution API Setup

1. Sign up for a JDoodle account at https://www.jdoodle.com/
2. Get your client ID and secret
3. Update the configuration in `application.properties`

```properties
code.execution.api.client-id=your_client_id
code.execution.api.client-secret=your_client_secret
```

### 3. Build and Run

```bash
# Clone the repository
git clone <repository-url>
cd exam-conductor

# Build the project
mvn clean install

# Run the application
mvn spring-boot:run
```

The application will start on `http://localhost:8080`

## Default Credentials

### Teacher Login
- Username: `teacher1`
- Password: `teacher123`

### Student Login
- Roll Number: `STU001`, `STU002`, or `STU003`
- Password: `student123`

## API Endpoints

### Authentication
- `POST /api/auth/student/login` - Student login
- `POST /api/auth/teacher/login` - Teacher login
- `POST /api/auth/refresh` - Refresh JWT token
- `POST /api/auth/logout` - Logout

### Exam Management
- `POST /api/exam/create` - Create new exam
- `GET /api/exam/{id}` - Get exam details
- `PUT /api/exam/{id}` - Update exam
- `DELETE /api/exam/{id}` - Delete exam

### Question Management
- `GET /api/questions/list` - Get all questions
- `POST /api/questions/add` - Add new question
- `PUT /api/questions/{id}` - Update question
- `DELETE /api/questions/{id}` - Delete question

### Code Execution
- `POST /api/submissions/execute` - Execute code
- `POST /api/submissions/submit` - Submit solution

## WebSocket Endpoints

- `/ws` - WebSocket connection endpoint
- `/topic/monitoring` - Real-time monitoring updates
- `/queue/alerts` - Private alert messages

## Project Structure

```
src/
├── main/
│   ├── java/com/jpec/exam/
│   │   ├── config/          # Configuration classes
│   │   ├── controller/      # REST controllers
│   │   ├── dto/            # Data Transfer Objects
│   │   ├── entity/         # JPA entities
│   │   ├── exception/      # Custom exceptions
│   │   ├── repository/     # JPA repositories
│   │   ├── security/       # Security components
│   │   ├── service/        # Business logic
│   │   ├── util/           # Utility classes
│   │   ├── websocket/      # WebSocket handlers
│   │   └── ExamApplication.java
│   └── resources/
│       ├── static/         # Frontend assets
│       │   ├── css/        # Stylesheets
│       │   ├── js/         # JavaScript files
│       │   └── lib/        # External libraries
│       ├── application.properties
│       └── data.sql        # Initial data
└── test/                   # Test files
```

## Security Features

- JWT token-based authentication
- Role-based access control (STUDENT/TEACHER)
- CORS configuration
- CSRF protection
- Input validation
- Secure password encoding (BCrypt)

## Development

### Running in Development Mode

```bash
mvn spring-boot:run -Dspring-boot.run.profiles=dev
```

### Building for Production

```bash
mvn clean package -Pprod
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.