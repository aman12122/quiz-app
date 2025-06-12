**Quiz App Backend**

A REST API for creating and managing quizzes, built with Spring Boot. After working with frontend JavaScript, I wanted to understand how the backend actually works and how data flows through a real application.
What it does

Store quiz questions with multiple choice answers in a database
Create custom quizzes by category (pulls random questions)
Serve questions without revealing correct answers (prevents cheating)
RESTful endpoints for managing questions and quizzes
Proper data relationships using JPA

**Built with:**

Spring Boot - My first dive into enterprise Java development
Spring Data JPA - For database operations (way easier than writing SQL manually)
PostgreSQL/H2 - Database storage
Lombok - Cuts down on boilerplate code significantly
Maven - Dependency management

**API Endpoints
Questions:**

GET /question/allQuestions - Get all questions (admin use)
GET /question/category/{category} - Filter by category
POST /question/add - Add new questions

**Quizzes:**

POST /quiz/create - Create quiz with random questions from a category
GET /quiz/get/{id} - Get quiz questions (answers hidden from users)

**What I learned building this**

Spring Framework: Coming from vanilla JavaScript, Spring felt overwhelming at first. All the annotations, dependency injection, and "magic" happening behind the scenes. But once I understood the concepts, it made building APIs so much faster than doing everything manually.
Database relationships: The @ManyToMany relationship between Quiz and Question was tricky to wrap my head around. Had to learn about JPA, entity mapping, and how Spring translates objects to database tables automatically.
API design: Realized there's a big difference between internal data (with answers) and what you expose to users. That's why I created the QuestionWrapper class - learned about DTOs and not exposing sensitive data through APIs.
Proper error handling: My first version crashed whenever something went wrong. Added try-catch blocks and proper HTTP status codes. Still learning about comprehensive error handling though.
Security through obscurity: The quiz endpoint only returns questions and options, never the correct answers. Users would submit their answers to a separate endpoint (not implemented yet) for scoring.

**What's missing (and what I learned)**

Answer submission endpoint - Need to handle user responses and calculate scores
Input validation - Currently trusting all incoming data (learned this is a bad idea)
Authentication - Anyone can create/access quizzes right now
Better error messages - Generic error handling isn't user-friendly
