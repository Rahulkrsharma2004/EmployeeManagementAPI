# 🚀 Employee Management System API in .NET 8

A RESTful API for managing employee data in an organization. The API supports CRUD operations and follows SOLID principles, dependency injection, and JWT authentication.

## 📂 Project Setup

1️⃣ Open VS Code and create a new .NET 8 Web API project:

```bash
mkdir EmployeeManagementAPI
cd EmployeeManagementAPI
dotnet new webapi
```

2️⃣ Install the necessary packages:

```bash
dotnet add package Microsoft.EntityFrameworkCore
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer
```

## 🏗️ Project Structure

```
EmployeeManagementAPI/
│
├── Controllers/
│   └── EmployeeController.cs
├── Services/
│   └── IEmployeeService.cs
│   └── EmployeeService.cs
├── Data/
│   └── EmployeeContext.cs
├── Models/
│   └── Employee.cs
├── DTOs/
│   └── EmployeeDTO.cs
├── Authentication/
│   └── AuthController.cs
│   └── JwtService.cs
└── Program.cs
```

## 🌟 Employee Entity

```csharp
public class Employee {
    public int Id { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public string Email { get; set; }
    public DateTime DateOfBirth { get; set; }
    public string Position { get; set; }
    public decimal Salary { get; set; }
}
```

## 🔗 Endpoints

| Method | Endpoint               | Description                  |
|--------|----------------------|-----------------------------|
| GET    | /api/employees       | Fetch all employees         |
| GET    | /api/employees/{id} | Fetch an employee by ID     |
| POST   | /api/employees       | Create a new employee       |
| PUT    | /api/employees/{id} | Update an employee by ID   |
| DELETE | /api/employees/{id} | Delete an employee by ID   |

## 🔐 Authentication (JWT)

1️⃣ Generate JWT token:

```bash
POST /api/auth/login
```

2️⃣ Use the token in the Authorization header for CRUD operations.

## 🛠️ Database Configuration

1️⃣ Add DbContext class:

```csharp
public class EmployeeContext : DbContext {
    public DbSet<Employee> Employees { get; set; }
    public EmployeeContext(DbContextOptions<EmployeeContext> options) : base(options) { }
}
```

2️⃣ Run Migrations:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

## 🛡️ Implementing SOLID Principles

✅ Single Responsibility Principle: Separate controllers and services.
✅ Open/Closed Principle: Easily extendable without modifying existing code.
✅ Liskov Substitution Principle: Interfaces allow flexible implementations.
✅ Interface Segregation Principle: Small, focused interfaces.
✅ Dependency Inversion Principle: Dependency injection for better code management.

## 📜 API Documentation with Swagger

1️⃣ Install Swagger:

```bash
dotnet add package Swashbuckle.AspNetCore
```

2️⃣ Enable Swagger in `Program.cs`:

```csharp
builder.Services.AddSwaggerGen();
```

## ✅ Run the API

```bash
dotnet run
```

Visit `http://localhost:5000/swagger` to access the Swagger UI.

## 🌐 Conclusion

This Employee Management System API is built with .NET 8, follows best practices, and is secured with JWT authentication. Enjoy building! 🚀

