---
title: "URL Shortener API"
date: 2025-01-01T00:00:00+07:00
weight: 1
draft: false
tags: ["nestjs", "typescript", "dynamodb", "postgresql", "clean-architecture", "serverless"]
---

## Overview

A full-featured URL Shortener API built with enterprise-grade architecture. The service generates short, unique aliases for long URLs and handles
redirections with minimal latency. Designed to handle high read-to-write ratios (100:1) with support for multiple user types (Guest, User, Admin),
click analytics, and automatic link expiration.

## Tech Stack

- **TypeScript & Node.js 20+** - Type-safe backend development
- **NestJS** - Progressive Node.js framework with dependency injection
- **PostgreSQL** - Relational data storage for users and authentication
- **AWS DynamoDB** - Distributed, scalable storage for short links with single-table design
- **TypeORM** - Database migrations and entity management
- **JWT (RS256)** - Secure authentication with cookie-based tokens
- **Docker & Docker Compose** - Containerized development environment
- **CircleCI** - CI/CD pipeline with parallel test execution
- **Serverless Framework** - AWS Lambda deployment support
- **nanoid** - Collision-resistant unique ID generation

## Key Features

- **URL Shortening** - Generate 10-character short codes with collision handling
- **URL Redirection** - HTTP 302 redirect with click tracking
- **Link Lifecycle Management** - Activate, deactivate, and extend expiry
- **Automatic Expiration** - DynamoDB TTL for automatic cleanup
- **Role-Based Access Control** - Hierarchical permissions (Admin > User > Guest)
- **API Versioning** - URI-based versioning for backward compatibility
- **Swagger Documentation** - Auto-generated OpenAPI docs
- **Cursor Pagination** - Efficient Base64-encoded pagination

## Challenges & Solutions

**Dual Database Strategy**: Needed different characteristics for different data types. Used PostgreSQL for relational user data requiring strong
consistency, and DynamoDB for URL storage needing high scalability. This hybrid approach optimizes performance for different access patterns.

**Collision-Safe Short Codes**: Implemented retry mechanism with DynamoDB conditional writes to handle potential nanoid collisions gracefully,
ensuring unique short codes without race conditions.

**DynamoDB Single-Table Design**: Designed partition and sort keys to support both user-based queries (all links for a user) and code-based lookups
(redirect by short code) using Global Secondary Indexes.

**Clean Architecture**: Structured the codebase with clear separation between domain, application, interface adapters, and infrastructure layers,
making the code testable and maintainable.

## Links

- <a href="https://github.com/kanelv/url-shortener" target="_blank">GitHub Repository</a>

## Timeline

**Started:** July 2024
**Status:** Active Development
