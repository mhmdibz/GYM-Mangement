# 🏋️ Gym Management System

A scalable RESTful API built with ASP.NET Core and Entity Framework Core for managing gym operations including members, trainers, sessions, bookings, and membership plans — following Clean Architecture, SOLID Principles, Repository Pattern, and Unit of Work.

---

## 📋 Table of Contents

- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Design Patterns](#design-patterns)
- [Getting Started](#getting-started)
- [API Endpoints](#api-endpoints)
- [Future Improvements](#future-improvements)
- [Learning Goals](#learning-goals)
- [Author](#author)

---

## Features

- ✅ Member management with membership status tracking (Active / Expired)
- ✅ Trainer management
- ✅ Membership plan management
- ✅ Session scheduling with capacity control (Open / Full)
- ✅ Booking system with conflict prevention
- ✅ Pagination support
- ✅ DTO-based responses
- ✅ Repository Pattern & Unit of Work
- ✅ Global exception handling middleware
- ✅ Swagger / OpenAPI documentation
- ✅ SQL Server integration
- ✅ AutoMapper & FluentValidation

---

## Architecture

The project follows **Clean Architecture** principles, divided into four layers:

```
┌─────────────────────────────────────┐
│           Gym.API (Presentation)    │  ← Controllers, Middleware
├─────────────────────────────────────┤
│        Gym.Application (Business)   │  ← Services, DTOs, Interfaces
├─────────────────────────────────────┤
│          Gym.Domain (Core)          │  ← Entities, Enums, Base classes
├─────────────────────────────────────┤
│      Gym.Infrastructure (Data)      │  ← EF Core, Repositories, Migrations
└─────────────────────────────────────┘
```

### Gym.API
- HTTP request handling
- Controllers
- Swagger configuration
- Global Exception Middleware
- Dependency Injection setup

### Gym.Application
- Business logic & Services
- DTOs (Request / Response)
- Interfaces (Services & Repositories)
- Custom Exceptions (NotFoundException, ConflictException, BusinessRuleException)

### Gym.Domain
- Core Entities (Member, Trainer, Session, Booking, MembershipPlan)
- Enums (MembershipStatus, SessionStatus)
- BaseEntity

### Gym.Infrastructure
- Entity Framework Core & GymDbContext
- Generic Repository implementation
- Unit of Work implementation
- EF Configurations & Migrations

---

## Tech Stack

| Technology | Version |
|---|---|
| .NET | 10.0 |
| ASP.NET Core Web API | 10.0 |
| Entity Framework Core | 10.0 |
| SQL Server | - |
| AutoMapper | 16.0 |
| FluentValidation | 11.3 |
| Swashbuckle (Swagger) | 10.1 |

---

## Project Structure

```
GymManagement/
│
├── Gym.API/
│   ├── Controllers/
│   │   ├── MembersController.cs
│   │   ├── TrainersController.cs
│   │   ├── SessionsController.cs
│   │   ├── BookingsController.cs
│   │   └── MembershipPlansController.cs
│   ├── Middleware/
│   │   └── GlobalExceptionMiddleware.cs
│   ├── appsettings.json
│   └── Program.cs
│
├── Gym.Application/
│   ├── DTOs/
│   │   ├── Members/
│   │   ├── Trainers/
│   │   ├── Sessions/
│   │   ├── Bookings/
│   │   ├── MembershipPlans/
│   │   └── Common/
│   ├── Interfaces/
│   │   ├── Services/
│   │   └── Repositories/
│   ├── Services/
│   └── Exceptions/
│
├── Gym.Domain/
│   ├── Entities/
│   ├── Enums/
│   └── Common/
│
└── Gym.Infrastructure/
    ├── Data/
    │   ├── GymDbContext.cs
    │   └── Configurations/
    ├── Repositories/
    ├── UnitOfWork/
    └── Migrations/
```

---

## Design Patterns

### Repository Pattern
Used to abstract data access logic and decouple the business layer from the database layer via a Generic Repository (`IGenericRepository`).

### Unit of Work Pattern
Used to manage transactions and coordinate multiple repositories, ensuring data consistency.

### Dependency Injection
Used throughout all layers for loose coupling and better testability.

---

## Getting Started

### Prerequisites

- [.NET 10 SDK](https://dotnet.microsoft.com/download)
- SQL Server
- Visual Studio 2022 or VS Code

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/mhmdibz/GYM-Mangement.git
cd GYM-Mangement
```

**2. Configure the connection string**

Open `Gym.API/appsettings.json` and update:
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=.;Database=GymManagementDb;Trusted_Connection=True;TrustServerCertificate=True"
  }
}
```

**3. Apply database migrations**
```bash
dotnet ef database update --project Gym.Infrastructure --startup-project Gym.API
```

**4. Run the application**
```bash
dotnet run --project Gym.API
```

**5. Open Swagger UI**
```
https://localhost:<port>/swagger
```

---

## API Endpoints

### Members
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/members` | Get all members |
| GET | `/api/members/paged` | Get members with pagination |
| GET | `/api/members/{id}` | Get member by ID |
| POST | `/api/members` | Create a new member |

### Trainers
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/trainers` | Get all trainers |
| GET | `/api/trainers/{id}` | Get trainer by ID |
| POST | `/api/trainers` | Create a new trainer |

### Sessions
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/sessions` | Get all sessions |
| GET | `/api/sessions/{id}` | Get session by ID |
| POST | `/api/sessions` | Create a new session |

### Bookings
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/bookings` | Get all bookings |
| GET | `/api/bookings/{id}` | Get booking by ID |
| POST | `/api/bookings` | Book a session for a member |

### Membership Plans
| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/membershipplans` | Get all plans |
| GET | `/api/membershipplans/{id}` | Get plan by ID |
| POST | `/api/membershipplans` | Create a membership plan |

---

## Future Improvements

- [ ] JWT Authentication & Authorization
- [ ] Role-based access control (Admin / Trainer / Member)
- [ ] Refresh Tokens
- [ ] Logging system
- [ ] Unit & Integration testing
- [ ] Docker support
- [ ] CI/CD pipeline
- [ ] Payment integration
- [ ] Notifications system
- [ ] Dashboard & analytics

---

## Learning Goals

This project was built to practice:

- Clean Architecture principles
- Scalable backend design
- ASP.NET Core Web API
- Entity Framework Core
- SOLID principles
- Repository & Unit of Work patterns
- Layered application structure

---

## Author

**Elsefi**
Computer Science Student & Backend Developer

---

## License

This project is for educational and portfolio purposes.
