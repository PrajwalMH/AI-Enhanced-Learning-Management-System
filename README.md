# AI-Enhanced Learning Management System 

## Project Summary

The **AI-Enhanced Learning Management System (LMS)** is a full-stack web application designed to support **Admin, Teacher, and Student** users.

The system includes features such as:

- Course and module management
- Assignments and submissions
- Grading
- Student progress tracking
- Learning analytics
- Notifications
- Discussion features
- Resource uploads
- Personalized learning recommendations
- AI-based quiz generation

## Technology Stack

### Backend

- **Java 17**
- **Spring Boot**
- **Spring Web**
- **Spring Data JPA**
- **Spring Security**
- **Maven**
- **JWT Authentication**
- **jjwt 0.12.6**
- **MySQL**
- **WebClient / Spring WebFlux**
- **AWS SDK for S3 2.25.60**

### Frontend

- **Next.js**
- **React**
- **TypeScript**
- **Tailwind CSS**
- **Axios**
- **Recharts / Chart.js** for student-performance visualizations

> Java 17 is the confirmed Java version used in the project. Other framework versions such as Spring Boot, Next.js, React, Maven, Node.js, and MySQL should be taken directly from `pom.xml`, `package.json`, and the local development environment rather than assumed.

## Running the Project

### 1. Create the MySQL Database

```sql
CREATE DATABASE ai_lms_db;
```

### 2. Configure the Backend

Update:

```text
backend/src/main/resources/application.properties
```

Configure the MySQL connection and SerpAPI credentials.

Example:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/ai_lms_db
spring.datasource.username=YOUR_USERNAME
spring.datasource.password=YOUR_PASSWORD

serpapi.api.key=YOUR_SERPAPI_KEY
serpapi.base.url=https://serpapi.com/search.json
```

### 3. Run the Backend

```bash
cd backend
mvn spring-boot:run
```

The backend runs at:

```text
http://localhost:8080
```

### 4. Run the Frontend

```bash
cd frontend
npm install
npm run dev
```

The frontend runs at:

```text
http://localhost:3000
```

### 5. Docker

Docker and Docker Compose can also be used to run the MySQL database, backend, and frontend together.

```bash
docker compose up --build
```

## SerpAPI Integration

**SerpAPI** is used for the **Personalized Learning Recommendation** feature.

When a student's performance falls below the required threshold, the backend sends a search request to SerpAPI to find relevant learning resources for the topic in which the student is struggling.

The recommendation system:

- Searches for educational resources related to weak topics
- Filters lower-quality or forum-based sources such as Reddit and Quora
- Prioritizes trusted and relevant educational resources
- Evaluates results based on topic relevance and source quality
- Returns up to **five recommended learning resources**

This allows the LMS to provide personalized external learning materials based on each student's academic performance instead of displaying the same resources to every student.
