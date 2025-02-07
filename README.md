# Fullstack Music Streaming App

## Description
Development of a fullstack music streaming application combining:
- A secure **Spring Boot** REST API for managing the music catalog and users.
- An **Angular** user interface for music playback and organization.
- **MongoDB** as the database for storing albums, songs, and audio files.
- **GridFS** for storing audio files and streaming data.

The application uses **stateless JWT authentication** and **role-based access control**.

## Technologies Used
### Backend:
- **Spring Boot** (Spring Security, Spring Data MongoDB, Bean Validation)
- **JWT Authentication**
- **MongoDB + GridFS**
- **REST API**
- **Docker & Jenkins**
- **Testing: JUnit, Mockito**

### Frontend:
- **Angular 17**
- **NgRx (state management)**
- **RxJS**
- **Bootstrap / Tailwind**
- **HTTP Interceptors & Guards**
- **Lazy loading & Resolvers**

## Features
### Backend (Spring Boot):
- **Album management**: CRUD with pagination, sorting, and filters
- **Song management**: CRUD with audio file handling
- **User management**: Registration, authentication, roles (Admin/User)
- **Audio file storage and streaming**

### Frontend (Angular):
- **Album and song management** with full CRUD (NgRx)
- **Integrated audio player** (Play, Pause, Next, Previous, Volume, Progress)
- **Dynamic user interface** with filters and search
- **Authentication pages and music library**

## Installation & Execution
### Prerequisites
- **Docker** & **Docker Compose**
- **Node.js** & **Angular CLI**
- **JDK 17** & **Maven**

### Installation with Docker
```bash
# Start all services
docker-compose up -d
```
The application will be available at:
- **Frontend**: `http://localhost:4200`
- **Backend**: `http://localhost:8080`
- **MongoDB**: `mongodb://localhost:27017/musicdb`

### Manual Installation
#### Backend
```bash
cd backend
mvn clean install
mvn spring-boot:run
```
The API will be available at `http://localhost:8080`

#### Frontend
```bash
cd frontend
npm install
ng serve
```
The user interface will be available at `http://localhost:4200`

## Docker Configuration
A **docker-compose.yml** file manages the backend, frontend, and MongoDB.

```yaml
version: '3.8'
services:
  backend:
    build: ./backend
    ports:
      - "8080:8080"
    environment:
      SPRING_PROFILES_ACTIVE: prod
    depends_on:
      - mongodb
  
  frontend:
    build: ./frontend
    ports:
      - "4200:4200"
    depends_on:
      - backend

  mongodb:
    image: mongo:latest
    container_name: music-db
    ports:
      - "27017:27017"
    volumes:
      - mongodb_data:/data/db

volumes:
  mongodb_data:
```

## Contribution
Contributions are welcome. For any improvements, open an issue or a pull request.

## Author
- **Mohammed El Bachiri**

## License
This project is licensed under the MIT License.


