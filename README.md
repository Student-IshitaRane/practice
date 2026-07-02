System Architecture

Our project follows a layered architecture based on the Unit of Work design pattern, which separates responsibilities into different layers. This makes the application modular, scalable, and easy to maintain.

The flow of the application is as follows:

1. Frontend

The user interacts with the SMS Workbench through the web interface.

For example, if an administrator wants to create a new user, assign application access, modify user rights, or approve a pending request, the frontend sends an HTTP request to the appropriate backend API.

↓

2. Controller Layer

The request first reaches the corresponding Spring Boot REST Controller.

Examples include:

UsersController
RightsController
DepartmentsController
LoginsController
SettingsController
VerificationsController

The controller's responsibility is very limited:

Receive the request
Validate required inputs
Call the appropriate service
Return the response

No business logic is written inside the controller.

↓

3. Service Layer (Business Logic)

The service layer contains the complete business logic of the application.

Examples include:

User management
Login assignment
Rights management
Department assignment
Menu access management
Maker-Checker verification
Report generation

This layer decides:

Which operation needs to be performed
What validations are required
Which repository should be called
How the returned data should be processed

↓

4. Unit of Work

Instead of services communicating directly with multiple repositories, they interact through a Unit of Work.

The Unit of Work acts as a central coordinator.

It provides access to all repositories and manages database-related operations from a single place.

This keeps services independent from repository implementations and makes the code easier to maintain and extend.

↓

5. Repository Layer

The repository layer is responsible for communicating with the database.

It executes database operations such as:

Fetching users
Creating users
Updating user rights
Assigning applications
Retrieving reports
Saving configuration settings

Repositories do not contain business logic.
Their only responsibility is data access.

↓

6. Database

The database stores all application information, including:

Users
Departments
Applications
Login details
Access rights
Menu permissions
Maker-Checker requests
Configuration settings

The processed data is then returned back through the Repository → Service → Controller layers before being sent to the frontend.
