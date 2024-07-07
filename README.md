# Java Backend Project

## Overview

This project is a Spring Boot application that uses PostgreSQL as the database. The project is containerized using Docker and leverages Flyway for database migrations. Postman is used for API testing.

## Prerequisites

- Java 11 or later
- Maven 3.6.3 or later
- Docker
- Postman

## Getting Started

### Clone the Repository

```sh
git clone https://github.com/yourusername/yourproject.git
cd yourproject
```

### Build the Project
Ensure that Maven is installed and JAVA_HOME is set correctly.
```sh
mvn clean install
```

## Run the Application with Docker

### 1. Create a Docker Network
```sh
docker-composer -up
```

### 2. Start the PostgreSQL Container
```sh
docker-compose up --build
```

This will start a PostgreSQL container with the following settings:

- **Username**: `abraham`
- **Password**: `admin`
- **Database**: `project`
- **Port**: `5432`

### 3. Apply Flyway Migrations

Flyway will automatically apply the migrations when the application starts.

### 4. Run the Spring Boot Application

Make sure Docker is running and execute:
```sh
mvn spring-boot:run
```

## Database Setup

### 1. Access PostgreSQL

To interact with the PostgreSQL database, you can use the following command:
```sh
docker exec -it <container_id> psql -U abraham -d project
```
Replace <container_id> with the actual container ID from docker ps.

### 2. Create the Initial Database and User
```sql
CREATE DATABASE project;
CREATE USER abraham WITH ENCRYPTED PASSWORD 'admin';
GRANT ALL PRIVILEGES ON DATABASE project TO abraham;
```
