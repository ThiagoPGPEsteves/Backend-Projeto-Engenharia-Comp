# FinanSmartAI - Backend Project

## Project Overview
FinanSmartAI is a personal finance management API built with **.NET 9.0**. It follows a layered architecture (inspired by Clean Architecture) to provide a robust and scalable backend for tracking transactions, managing users, and generating financial summaries.

### Architecture Layers:
- **FinanSmartAI.API**: The entry point. Contains Controllers, Program.cs (configuration), and Middlewares.
- **FinanSmartAI.Application**: Contains business logic (Services), Data Transfer Objects (DTOs), and request Validators.
- **FinanSmartAI.Domain**: Contains the core domain models and entities (User, Transaction).
- **FinanSmartAI.Infrastructure**: Handles data persistence using Entity Framework Core and database configuration.

## Key Technologies
- **Framework**: ASP.NET Core (.NET 9.0)
- **Database**: SQL Server (LocalDB by default) with Entity Framework Core
- **Authentication**: JWT (JSON Web Tokens)
- **Validation**: FluentValidation
- **Security**: BCrypt.Net-Next for password hashing
- **Documentation**: Swagger (OpenAPI)
- **Logging**: Microsoft.Extensions.Logging (Console & Debug)

## Building and Running

### Prerequisites
- .NET 9.0 SDK
- SQL Server (or LocalDB)

### Key Commands
- **Build the solution**: `dotnet build`
- **Run the API**: `dotnet run --project FinanSmartAI.API`
- **Run with Hot Reload**: `dotnet watch --project FinanSmartAI.API`
- **Restore Dependencies**: `dotnet restore`

### Database Setup
The application uses `dbContext.Database.EnsureCreated()` in `Program.cs`, which means it will automatically create the database and tables if they don't exist when the application starts (using the connection string in `appsettings.json`).

## Development Conventions

### General Rules
- **Async/Await**: All I/O-bound operations (database, external calls) must be asynchronous.
- **Separation of Concerns**: Keep business logic in the `Application` layer and data access in the `Infrastructure` layer.
- **DTOs**: Never return entities directly from controllers. Use DTOs for data transfer between layers and for API responses.
- **Validation**: Use FluentValidation in the `Application` layer to validate incoming requests.
- **Logging**: Use `ILogger<T>` for structured logging of important events and errors.

### Project Structure
- `Controllers/`: Handle HTTP requests and orchestrate service calls.
- `Services/`: Implement business logic and interact with the database context.
- `Entities/`: Represent the core domain and database schema.
- `Validators/`: Ensure data integrity before processing.

## Missing/Future Improvements (TODO)
- **Testing**: Add a dedicated Test project (Unit and Integration tests).
- **Migrations**: Transition from `EnsureCreated()` to EF Core Migrations for better schema management in production.
- **Docker**: Add Dockerfile and docker-compose for easier deployment.
