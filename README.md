AgriEnergyConnect
Overview
AgriEnergyConnect is a web-based platform that connects farmers and employees for managing agricultural products. The platform allows farmers to add their products, view their listings, and for employees to manage farmer profiles, view products, and filter products based on different criteria.

This prototype showcases the functionality for managing farmers and products within the application. The backend uses C# and ASP.NET Core with Entity Framework Core to interact with a SQL Server database. The frontend is designed to be user-friendly with intuitive navigation for both farmers and employees.

Features
Farmer Management:

Farmers can register and manage their profiles.
Farmers can add new products to their profile.
View their own products with details such as name, category, and production date.
Employee Management:

Employees can add new farmers and manage their profiles.
Employees can view and filter a list of products from various farmers.
Employees can filter products by category, production date, and more.
Authentication and User Roles:

Secure authentication system for role-based access control.
Farmers have access only to their own products and profile.
Employees can view all products and manage farmer profiles.

Tech Stack
Backend: C# with ASP.NET Core
Frontend: Razor Pages (MVC) for UI
Database: SQL Server, Entity Framework Core
Authentication: ASP.NET Identity for user authentication and authorization
Development Environment: Visual Studio

Prerequisites
Before running the AgriEnergyConnect application locally, ensure you have the following software installed:

Visual Studio 2022 or later (with ASP.NET Core development workload)
SQL Server 2017 or later (or SQL Server Express)
.NET 6.0 or later SDK (for .NET Core applications)
SQL Server Management Studio (SSMS) or an SQL client (optional but useful for database management)

Setup and Installation
Follow the steps below to set up the AgriEnergyConnect application locally:

1. Clone the Repository
First, clone the repository to your local machine:
git clone https://github.com/AvarnSewlal/PROG7312-POE
2. Set Up the Database
Open SQL Server Management Studio (SSMS) or use a SQL client of your choice.
Execute the provided SQL scripts to create the database and tables. You can execute the script using Visual Studio’s SQL Server Object Explorer or any SQL client.
Here is the SQL script to create the necessary tables and seed the data:
-- Create the Database
CREATE DATABASE AgriEnergyConnect;
GO

-- Use the Database
USE AgriEnergyConnect;
GO

-- Create Farmers Table
CREATE TABLE Farmers (
    Id INT IDENTITY(1,1) PRIMARY KEY,
    Name NVARCHAR(100) NOT NULL,
    Address NVARCHAR(255) NOT NULL
);
GO

-- Create Products Table
CREATE TABLE Products (
    Id INT IDENTITY(1,1) PRIMARY KEY,
    Name NVARCHAR(100) NOT NULL,
    Category NVARCHAR(50) NOT NULL,
    ProductionDate DATE NOT NULL,
    FarmerId INT NOT NULL,
    FOREIGN KEY (FarmerId) REFERENCES Farmers(Id)
);
GO

-- Insert Sample Data
INSERT INTO Farmers (Name, Address)
VALUES ('John Doe', '123 Farm Lane'), ('Jane Smith', '456 Countryside Rd');

INSERT INTO Products (Name, Category, ProductionDate, FarmerId)
VALUES ('Corn', 'Grain', '2023-10-10', 1), ('Tomato', 'Vegetable', '2023-10-12', 2);
GO
3. Configure the Connection String
Update the appsettings.json file with the connection string for your local SQL Server instance. Here’s an example configuration:
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=AgriEnergyConnect;Trusted_Connection=True;"
  }
}

Ensure that the SQL Server instance is running and accessible on your machine.

4. Restore NuGet Packages
Open the solution in Visual Studio and restore the NuGet packages:

In Visual Studio, right-click on the solution and select Restore NuGet Packages.
Alternatively, run the following command from the terminal:
dotnet restore
. Build the Application
Build the application to ensure that there are no errors. In Visual Studio, press Ctrl + Shift + B or use the Build menu.

6. Run the Application
Press F5 in Visual Studio to run the application.
The application will open in your default browser.

Usage
Farmer Functionality
Login as Farmer: The farmer can log in and manage their profile.
Add Products: After logging in, the farmer can add products to their profile by providing details such as product name, category, and production date.
View Products: Farmers can view the list of products they have added, along with relevant details.
Employee Functionality
Login as Employee: Employees can log in using their credentials.
Add Farmers: Employees can add new farmer profiles with their names and addresses.
View Products: Employees can view products from all farmers.
Filter Products: Employees can filter products by category or production date to easily manage and view products from different farmers.

Authentication
The application uses ASP.NET Core Identity for handling user authentication and role management:

Farmers: Farmers can register and manage their own profiles and products. They have access to their own data.
Employees: Employees have more privileges and can view and manage the data for multiple farmers and products.

Testing
Test User Roles: Test the different roles (Farmer and Employee) to ensure that role-based access control is working as expected.
Test CRUD Operations: Test the creation, reading, updating, and deletion of products and farmer profiles.

Troubleshooting
Database Connection Issues: Ensure that your SQL Server instance is running and that the connection string is correctly configured in appsettings.json.
Missing Packages: Ensure all NuGet packages are restored. If issues persist, try cleaning the solution and rebuilding it.

ontributing
Contributions are welcome! If you would like to contribute to the AgriEnergyConnect project, follow these steps:

Fork the repository.
Create a new branch (git checkout -b feature-branch).
Make your changes.
Commit your changes (git commit -am 'Add new feature').
Push to the branch (git push origin feature-branch).
Create a pull request with a description of the changes you made.

For any queries please contact: ST10083252@vcconnect.edu.za
