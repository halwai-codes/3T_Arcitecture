# 3-Tier Architecture

## 📌 Objective

Build a .NET application using **3-Tier Architecture** to understand how a real-world application separates responsibilities between the Presentation, Business, and Data Access layers.

The goal is to practice architecture, separation of concerns, dependency injection, interfaces, business logic, and database interaction.

---

# 🏗️ Architecture

The application should contain three main layers:

### 1. Presentation Layer

Responsible for communication with the client.

Responsibilities:

* Receive client requests
* Define API endpoints
* Validate incoming request models
* Call the Business Layer
* Return appropriate HTTP responses
* Handle presentation-related concerns

Do not put business rules or database queries in this layer.

---

### 2. Business Layer

Responsible for application and business logic.

Responsibilities:

* Implement business rules
* Perform business validations
* Process application workflows
* Coordinate operations
* Communicate with the Data Access Layer
* Transform data when required
* Return results to the Presentation Layer

The Business Layer should not directly handle HTTP requests or database-specific implementation details.

---

### 3. Data Access Layer

Responsible for communicating with the database.

Responsibilities:

* Database connectivity
* CRUD operations
* Entity Framework Core operations
* Repository implementation
* Query execution
* Data persistence
* Database-related configuration

Business decisions should not be implemented in this layer.

---

# 🔄 Request Flow

Follow this flow for every application operation:

1. Client sends a request.
2. Presentation Layer receives the request.
3. Presentation Layer calls the appropriate Business Layer service.
4. Business Layer validates and processes the request.
5. Business Layer calls the Data Access Layer when database access is required.
6. Data Access Layer communicates with the database.
7. Data Access Layer returns the data.
8. Business Layer processes the returned data.
9. Presentation Layer returns the response to the client.

---

# 📁 Project Organization

Create separate projects for:

* Presentation
* Business
* Data Access

Keep each project's responsibility clearly separated.

Avoid placing classes in another layer simply because they are convenient to access there.

---

# 🔗 Layer Dependencies

Follow this dependency direction:

**Presentation → Business → Data Access → Database**

Avoid unnecessary reverse dependencies.

The Presentation Layer should not directly access the database.

The Business Layer should not directly contain database implementation.

---

# 🔌 Interfaces

Use interfaces between major application responsibilities.

Create interfaces for:

* Business services
* Repositories
* Other components where loose coupling is beneficial

The purpose is to allow implementations to be replaced or mocked without changing the calling layer.

---

# 💉 Dependency Injection

Use .NET Dependency Injection to provide required services and repositories.

Requirements:

* Register dependencies centrally.
* Inject dependencies through constructors.
* Avoid manually creating service or repository objects inside Controllers.
* Keep components loosely coupled.

---

# 🗄️ Database

Use a relational database such as SQL Server.

Create entities appropriate for the application.

For practice, include entities such as:

* Employee
* Department
* Customer
* Admin

Implement common database operations:

* Create
* Read
* Update
* Delete

---

# 🧠 Business Rules

Business rules must remain inside the Business Layer.

Examples:

* Employee must belong to a valid department.
* Customer email must be unique.
* Employee salary must satisfy defined business constraints.
* Deleted records should follow the application's business rules.
* Only authorized operations should be allowed.

Do not move these rules into Controllers or repositories.

---

# 🧪 Validation

Implement validation at the appropriate level.

### Presentation Validation

Validate request structure and required fields.

### Business Validation

Validate business rules and application-specific conditions.

### Database Validation

Use database constraints where appropriate to maintain data integrity.

---

# 📦 DTOs

Use DTOs when transferring data between the API and internal application layers.

Do not expose database entities unnecessarily through the API.

Consider separate models for:

* Create requests
* Update requests
* Response objects

---

# 🧪 Testing

Create tests for the Business Layer independently from the database.

Focus on:

* Business rules
* Validation
* Service behavior
* Success scenarios
* Failure scenarios
* Exception scenarios

Use mocks for dependencies when appropriate.

---

# ⚠️ Error Handling

Implement centralized error handling.

The application should:

* Handle unexpected exceptions
* Return meaningful HTTP responses
* Avoid exposing internal implementation details
* Log important application errors

---

# 📝 Logging

Add application logging for important events.

Log information such as:

* Application operations
* Errors
* Exceptions
* Important business events

Do not log passwords, tokens, connection strings, or other sensitive information.

---

# 🔐 Security

Add basic API security practices.

Consider:

* Authentication
* Authorization
* Input validation
* Secure configuration
* Protection of sensitive information
* Proper database access controls

---

# 📊 Documentation

Document:

* Architecture
* Project structure
* Layer responsibilities
* API endpoints
* Database design
* Setup instructions
* Configuration requirements

Use Swagger/OpenAPI for API documentation.

---

# 🚀 Implementation Tasks

Complete the project in the following order:

* [ ] Create the solution.
* [ ] Create the Presentation project.
* [ ] Create the Business project.
* [ ] Create the Data Access project.
* [ ] Configure project references.
* [ ] Create database entities.
* [ ] Configure the database context.
* [ ] Create repository interfaces.
* [ ] Implement repositories.
* [ ] Create business service interfaces.
* [ ] Implement business services.
* [ ] Configure Dependency Injection.
* [ ] Create API Controllers.
* [ ] Implement CRUD operations.
* [ ] Add DTOs.
* [ ] Add validation.
* [ ] Add exception handling.
* [ ] Add logging.
* [ ] Add unit tests.
* [ ] Add Swagger documentation.
* [ ] Test the complete request flow.
* [ ] Push the project to GitHub.

---

# 🎯 Learning Outcomes

After completing the project, you should be able to explain and demonstrate:

* What 3-Tier Architecture is
* Why separation of concerns is important
* Responsibilities of each layer
* Dependency Injection
* Interfaces
* Repository Pattern
* Service Layer
* DTOs
* Entity Framework Core
* CRUD operations
* SOLID principles
* Unit testing
* API request flow
* Database interaction

---

# 💼 Portfolio Goal

The project should demonstrate that you can take a simple .NET application and organize it using a maintainable layered architecture.

The final project should clearly show the complete flow:

**Client → Presentation → Business → Data Access → Database**

and:

**Database → Data Access → Business → Presentation → Client**
