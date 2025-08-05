# UserService Microservice – MVP Setup (2025-08-05)
**Author:** Jeet Solanki

## Overview
This document outlines the initial setup and architecture of the UserService microservice for the Brainz project.  
It explains what has been implemented, how the service is organized, current capabilities, and outstanding tasks.

---


## What I Did

### 1. **Project Structure**
- Created a modular Java Spring Boot project with the following packages:
    - `config/` – Security and app configuration
    - `controller/` – REST API endpoints
    - `dto/` – Data Transfer Objects for requests/responses
    - `entity/` – 
    - `exception/` – (Reserved for future custom exceptions)
    - `repository/` – 
    - `security/` – (Reserved for future, e.g., filters)
    - `service/` – Business logic (UserService)
    - `util/` – Utility classes

### 2. **Environment Configuration**
- Split configuration into:
    - `application.properties` (shared, non-sensitive)
    - `application-dev.properties` (PostgresSql, dev settings)
    - `application-test.properties` (H2, test settings)
- JWT secret is now referenced as an environment variable (`JWT_SECRET`), not hardcoded.


### 5. **CI/CD**
- GitHub Actions workflow runs tests and builds Docker images.
- CI uses the `test` profile, ensuring safe, isolated builds.

---


## What We Can Do Now

- Accept Registration, Validate, and User-specific requests via REST API.
- Create user in db and passing roles, and use passwordEncoder
- Run automated tests and builds in CI/CD with safe, environment-specific config.
- Easily extend the service for new features (e.g., friend-system, group-system, etc.).

---

## What’s Needed for Production

- Set the `JWT_SECRET` environment variable securely in production.
- Implement the UserService microservice for user profile management, and context based LLM usage(core-stuff).
- Add more tests (unit, integration, security).
- Add exception handling and error responses.
- Add monitoring/health checks (Spring Boot Actuator).
- (Optional) Add rate limiting, logging, and audit features.

---

## What Remains / Next Steps

- Write test cases
- Implement context-storage in user-side, LLm-core to provide that context, communicate them via webclient(asynchronous) and connect it to a real database.
- Add context-storage, password reset, and user profile endpoints.
- Write more documentation for each new feature or milestone.
- Regularly update the `docs/` folder with new design decisions and features.

---

## How to Use This Documentation

- Keep this file in `docs/` as a permanent record of the MVP setup.
- For each new feature or milestone, add a new markdown file in `docs/` (e.g., `2025-07-27-User-feature.md`).
- Copy/paste or link these docs to your knowledge base repo as needed.

---