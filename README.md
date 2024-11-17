# Survivor API

This project is a Web API application designed for the Survivor competition. It allows managing competitors and categories with a one-to-many relationship. The API supports basic CRUD operations (Create, Read, Update, Delete) for both competitors and categories.

## Overview

The database consists of two tables:
1. **Competitors Table**:
   - Represents the competitors participating in the Survivor competition.
2. **Categories Table**:
   - Represents the categories that group the competitors (e.g., Celebrities, Volunteers).

### Tables and Relationships

#### Competitors Table
| Column         | Type    | Description                                  |
|----------------|---------|----------------------------------------------|
| `Id`           | `int`   | Primary key, auto-incremented.               |
| `CreatedDate`  | `DateTime` | The date when the competitor was created. |
| `ModifiedDate` | `DateTime` | The date when the competitor was last updated. |
| `IsDeleted`    | `bool`  | Marks the competitor as deleted.             |
| `FirstName`    | `string`| The first name of the competitor.            |
| `LastName`     | `string`| The last name of the competitor.             |
| `CategoryId`   | `int`   | Foreign key linking the competitor to a category. |

#### Categories Table
| Column         | Type    | Description                                  |
|----------------|---------|----------------------------------------------|
| `Id`           | `int`   | Primary key, auto-incremented.               |
| `CreatedDate`  | `DateTime` | The date when the category was created.   |
| `ModifiedDate` | `DateTime` | The date when the category was last updated. |
| `IsDeleted`    | `bool`  | Marks the category as deleted.               |
| `Name`         | `string`| The name of the category (e.g., Celebrities).|

### API Endpoints

#### CompetitorController
- **GET /api/competitors**: Retrieve all competitors.
- **GET /api/competitors/{id}**: Retrieve a specific competitor by ID.
- **GET /api/competitors/categories/{CategoryId}**: Retrieve competitors by category.
- **POST /api/competitors**: Add a new competitor.
- **PUT /api/competitors/{id}**: Update an existing competitor.
- **DELETE /api/competitors/{id}**: Soft delete a competitor.

#### CategoryController
- **GET /api/categories**: Retrieve all categories.
- **GET /api/categories/{id}**: Retrieve a specific category by ID.
- **POST /api/categories**: Add a new category.
- **PUT /api/categories/{id}**: Update an existing category.
- **DELETE /api/categories/{id}**: Soft delete a category.

### Key Features
- Implements a one-to-many relationship between categories and competitors.
- Uses a base entity class for shared properties like `CreatedDate`, `ModifiedDate`, and `IsDeleted`.
- Provides soft delete functionality for both entities.

## Setup Instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/survivor-api.git
   ```

2. Open the project in Visual Studio or your preferred IDE.

3. Install Entity Framework Core:
   ```bash
   dotnet add package Microsoft.EntityFrameworkCore
   dotnet add package Microsoft.EntityFrameworkCore.SqlServer
   dotnet add package Microsoft.EntityFrameworkCore.Tools
   ```

4. Add the migration and update the database:
   ```bash
   dotnet ef migrations add InitialCreate
   dotnet ef database update
   ```

5. Run the project:
   ```bash
   dotnet run
   ```

## Author

Created by **Batuhan Uzun**
