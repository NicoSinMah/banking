# Banking Backend API

> A banking backend built with **Java 21**, **Spring Boot** and **PostgreSQL**, grown one small, tested increment at a time.

---

## The Vision

This project is a **living laboratory**. The goal is not just to ship a banking API, but to build one the way a professional engineer would: understanding *why* each piece exists, what alternatives were available, and what trade-offs were accepted.

Banking is a deliberately demanding domain. Money cannot be created or lost by accident, two operations can collide at the same instant, and a wrong answer is never "close enough". That makes it an ideal setting to practice:

- clear **business rules**
- reliable **data handling**
- sound **transaction boundaries**
- meaningful **testing**
- layered **security**

> **Honesty note:** this README describes the *intended* application. Every feature listed below is a goal until it is backed by code and passing tests. The [Project Status](#-project-status) section tracks what is actually done.

---

## What I'm Building

### Core Banking Operations

| Capability | Description |
|---|---|
| **Account management** | Create and retrieve bank accounts through a REST API |
| **Deposits & withdrawals** | Balance operations that enforce business rules (e.g. no overdrafts) |
| **Transfers** | Move funds between accounts with consistency and proper transaction boundaries |
| **Persistence** | Reliable storage of all data in PostgreSQL |

### Engineering Quality

| Capability | Description |
|---|---|
| **Validation & error handling** | Validated requests and consistent, meaningful HTTP error responses |
| **Testing** | Unit and integration tests covering API behavior, business rules and persistence |
| **Security** | Authentication and authorization, with JWT-based auth introduced once the fundamentals are solid |
| **Concurrency safety** | Protection against race conditions and lost updates on balances |

---

## Technology Stack

| Layer | Technology |
|---|---|
| Language | Java 21 |
| Framework | Spring Boot, Spring MVC |
| Database | PostgreSQL |
| Persistence | JPA / Hibernate (where applicable) |
| Testing | JUnit, Mockito (MockMvc and Testcontainers planned for integration tests) |
| Security | Spring Security, JWT |

*The stack reflects the intended direction. Exact dependencies and versions should be confirmed in the build configuration.*

---

## Architecture

A classic **layered backend**, keeping responsibilities separate so the code stays understandable and testable:

```
   HTTP Request
        │
        ▼
 ┌─────────────┐   DTOs in / out
 │ Controller  │──────────────────┐
 └─────────────┘                  │
        │                         │
        ▼                         │
 ┌─────────────┐   Business rules │
 │   Service   │   & transactions │
 └─────────────┘                  │
        │                         │
        ▼                         │
 ┌─────────────┐                  │
 │ Repository  │                  │
 └─────────────┘                  │
        │                         │
        ▼                         ▼
 ┌─────────────┐          ┌─────────────┐
 │ PostgreSQL  │◄─Entity──│     DTO     │
 └─────────────┘          └─────────────┘
```

- **Controller** – handles HTTP requests and responses
- **DTO** – defines the data exchanged through the API
- **Service** – application workflows and business rules
- **Repository** – data access
- **Entity** – persisted domain data
- **Configuration** – application and framework settings, including security

*The structure follows the implementation as it evolves. Not every layer exists yet.*

---

## 🔐 Security Direction

Security is introduced **incrementally**, starting from one key distinction:

- **Authentication** → *who* is making the request?
- **Authorization** → *what* is that identity allowed to do?

The plan: protect endpoints first, then build token-based authentication with **JWT** (claims, signing, expiration). Listing Spring Security or JWT as planned technologies does **not** mean the application is secured. Security behavior must be implemented *and* tested before it counts.

---

## 🛣️ Development Roadmap

The project grows alongside a structured, eight-phase backend engineering path. Early phases build the foundations this API depends on; later phases push it toward more advanced designs.

| Phase | Focus | Relevance to this project |
|---|---|---|
| **1. Backend fundamentals** | Java, SQL, JDBC, Spring Boot, REST, JPA, error handling, transactions, testing, security | Builds the first working version of the API |
| **2. Deep Java** | Memory, OOP, `equals`/`hashCode`, invariants, contracts | Stronger domain model and safer entities |
| **3. Data structures & algorithms** | Collections, complexity, algorithms | Informed choices of structures and implementations |
| **4. Software design** | SOLID, design patterns, clean code, refactoring | Cleaner, more extensible service layer |
| **5. Advanced Java & JVM** | Generics, streams, concurrency, JVM internals | Correct, safe handling of concurrent balance updates |
| **6. Professional backend** | Advanced Spring, SQL, indexes, N+1, migrations, OpenAPI | A production-minded persistence and API layer |
| **7. Architecture & distributed systems** | Modular monolith, hexagonal, DDD, messaging, resilience, Docker, Kubernetes, CI/CD | Possible evolution of the design, only when justified |
| **8. Professional engineering** | Code review, debugging, performance, defending technical decisions | Final consolidation and polish |

### Guiding principles

- **Understanding over copying.** Every decision should be explainable and justified.
- **Fundamentals over frameworks.** Frameworks are tools, not the goal.
- **Simplest design that works.** No microservices or Kubernetes where a simpler design is enough.
- **Evidence over claims.** A feature is "done" when it is implemented, tested and understood.

---

## 📍 Project Status

**🚧 In constant development.** This is an evolving application built and tested in small increments.

Planned capabilities are treated as goals until backed by code and test evidence. A living checklist, to be updated as work lands:

- [x] Project setup (Java 21, Spring Boot, build tool, PostgreSQL connection)
- [x] Account creation and retrieval
- [x] Deposits and withdrawals with business rules
- [x] Transfers with transactional consistency
- [x] Request validation and consistent error responses
- [ ] Unit tests (JUnit, Mockito)
- [ ] Integration tests (MockMvc, persistence, Testcontainers)
- [ ] Concurrency handling (optimistic / pessimistic locking)
- [ ] Authentication and authorization (Spring Security)
- [ ] JWT-based authentication
- [ ] API documentation (OpenAPI)
- [ ] Dockerized setup and CI pipeline

---

## Running the Application

Run instructions are intentionally omitted until the repository's actual build tool, configuration, database setup and implementation have been verified.

Once confirmed, this section will document:

- required Java version
- PostgreSQL setup and configuration
- environment variables
- exact commands to start the app and run the tests

---

## Scope

This repository is the **banking-themed monolithic application** used for hands-on backend learning. It is separate from the *BanKing* microservices portfolio project unless the two are explicitly connected.

---

## 📓 Development Log

*Progress notes will be added here as the project evolves: what was built, what was learned, and what comes next.*

| Date | Milestone | Notes |
|---|---|---|
| — | Project started | README and roadmap defined |

---

Built step by step. Tested as it grows. Understood before it ships.
