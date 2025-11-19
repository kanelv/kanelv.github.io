---
title: "Library Management System"
date: 2025-03-10T00:00:00+07:00
weight: 2
draft: false
tags: ["Java", "Spring Boot", "Clean Architecture", "DDD", "REST API", "PostgreSQL", "JWT"]
---

## Overview

A production-grade Library Management System built with Domain-Driven Design (DDD), Clean Architecture, and Hexagonal Architecture principles. This
RESTful API demonstrates enterprise-level Java development practices with a focus on maintainability, testability, and scalability. The system handles
  book catalog management, user/member management, borrowing operations, and includes comprehensive authentication and authorization features.

## Tech Stack

- **Java 17** with **Spring Boot 3.3.3**
- **PostgreSQL 15** with **Flyway** for database migrations
- **Spring Security 6** with **JWT** (JJWT 0.12.6) for authentication
- **Spring Data JPA** with Hibernate 6
- **Lombok** for boilerplate reduction
- **TestContainers** for integration testing
- **GitHub Actions** for CI/CD
- **JaCoCo** for code coverage (50% minimum threshold)

## Key Features

- **Book Management**: Full CRUD operations with ISBN validation (ISBN-10/13 formats), availability tracking, and copy management
- **User Management**: Role-based system with ADMIN, USER, and GUEST roles, each with different borrowing limits and durations
- **Borrowing System**: Complete borrowing workflow including book checkout, returns, due date extensions, overdue tracking, and automatic penalty
calculation ($1/day)
- **JWT Authentication**: Secure HTTP-only cookie-based authentication with role-based access control
- **Security Features**: CSRF protection, XSS filtering with Content Security Policy headers, BCrypt password encryption
- **Clean Architecture**: Clear separation between Domain, Application, Infrastructure, and Interface layers with 18 single-responsibility use cases

## Challenges & Solutions

**Challenge 1: Maintaining Clean Architecture Boundaries**
Implementing true Clean Architecture required strict discipline in keeping domain logic free from framework dependencies. Solution: Created separate
JPA entities in the infrastructure layer with mappers to convert between domain and persistence models, ensuring the domain layer remains pure.

**Challenge 2: Rich Domain Model vs Anemic Domain Model**
Avoiding the anemic domain model anti-pattern while working with JPA. Solution: Placed all business logic in domain entities (e.g.,
`Book.borrowCopy()`, `Borrowing.calculateCurrentPenalty()`) and used value objects like `ISBN` and `Email` for validation and immutability.

**Challenge 3: Secure Authentication Implementation**
Implementing JWT authentication with proper security practices. Solution: Used HTTP-only secure cookies for JWT storage, implemented comprehensive
security headers (CSP, X-XSS-Protection, nosniff), and created custom XSS filter for request sanitization.

## Links

- [GitHub Repository](https://github.com/kane/LibraryManagementAPI)

## Timeline

**Started:** March 2025
**Status:** Active
