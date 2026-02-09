# Recipe Matcher

> A web application for managing recipes with intelligent ingredient matching and seasonal filtering.

## 🎯 Project Status

**Current Phase:** Initial Setup & Architecture  
**Portfolio Project** - Focus on clean architecture and professional code structure

---

## 🛠️ Tech Stack

- **Backend:** Java 21, Spring Boot 3.2
- **Database:** PostgreSQL 16
- **Security:** Spring Security (Form Login)
- **Persistence:** Spring Data JPA, Hibernate
- **Migrations:** Flyway
- **Frontend:** Thymeleaf (Server-side rendering)
- **Build Tool:** Maven

---

## 🚀 Features (Planned)

### MVP
- ✅ User authentication (form login)
- ⏳ Recipe CRUD (manual entry)
- ⏳ Recipe import from Chefkoch.de
- ⏳ Ingredient matching with scoring algorithm
- ⏳ Seasonal recipe filtering
- ⏳ Mobile-responsive UI

### Future Enhancements
- Multiple import sources (REWE, HelloFresh)
- Advanced search filters
- Recipe categories & tags
- Shopping list generation

---

## 📐 Architecture

### Layer Structure
```
Presentation Layer (Controllers + Thymeleaf)
         ↓
Service Layer (Business Logic)
         ↓
Repository Layer (Spring Data JPA)
         ↓
Database (PostgreSQL)
```

### Core Concepts
- **Clean separation of concerns** - Controller → Service → Repository
- **DTOs** for data transfer (Entities stay in service layer)
- **Strategy Pattern** for recipe importers (extensible)
- **Domain-driven design** for matching & season logic

---

## 🏃 Running Locally

### Prerequisites
- Java 21 (or Java 17)
- Docker & Docker Compose
- Maven (or use included wrapper)

### Setup

1. **Start PostgreSQL**
```bash
   docker-compose up -d
```

2. **Run Application**
```bash
   ./mvnw spring-boot:run
```

3. **Access Application**
```
   http://localhost:8080
```

### Database Access
```
Host:     localhost:5432
Database: recipedb
User:     recipeuser
Password: recipepass
```

---

## 📦 Project Structure
```
src/main/java/com/simohoff/recipematcher/
├── config/              # Spring configuration
├── domain/              # Entities, repositories
├── service/             # Business logic
│   └── importer/        # Recipe import strategies
└── web/                 # Controllers, DTOs, validators
```

---

## 🗄️ Data Model
```
User (1) ──→ (N) Recipe (1) ──→ (N) RecipeIngredient (N) ──→ (1) Ingredient
```

- **Recipe** has source type (MANUAL, CHEFKOCH, ...)
- **Ingredient** has seasonal availability (start/end month)
- **RecipeIngredient** stores recipe-specific amounts

---

## 📝 Development Notes

- **Flyway** manages all schema changes (no manual SQL)
- **No logic in controllers** - everything in services
- **Testable design** - services can be unit tested
- **Repository pattern** - Spring Data JPA interfaces only

---

## 📄 License

This is a personal portfolio project. Feel free to learn from it, but please don't copy it wholesale.

---

## 🔗 Contact

Your Name - [@yourhandle](https://twitter.com/yourhandle)  
Project Link: [https://github.com/yourusername/recipe-matcher](https://github.com/yourusername/recipe-matcher)