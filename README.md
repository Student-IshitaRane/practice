User clicks "Create User"
            │
            ▼
UsersController
Receives API request
            │
            ▼
RightsMgmtService
Validates request &
applies business logic
            │
            ▼
ServiceDto is created
            │
            ▼
UnitOfWork
Calls Repository
            │
            ▼
Repository
Executes database operation
            │
            ▼
Result received
            │
            ▼
Mapped to Response DTO
            │
            ▼
ApiResponse
            │
            ▼
Frontend displays success
