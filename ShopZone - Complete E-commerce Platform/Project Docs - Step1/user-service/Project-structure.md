## **Step 4: Project Structure**
```
user-service/
└── src/main/java/com/shopzone/userservice/
    ├── UserServiceApplication.java
    ├── config/
    │   ├── SecurityConfig.java
    │   ├── JwtAuthenticationFilter.java
    │   └── OpenApiConfig.java
    ├── controller/
    │   ├── AuthController.java
    │   ├── UserController.java
    │   └── InternalUserController.java
    ├── dto/
    │   ├── request/
    │   │   ├── RegisterRequest.java
    │   │   ├── LoginRequest.java
    │   │   ├── ChangePasswordRequest.java
    │   │   └── AddressRequest.java
    │   └── response/
    │       ├── LoginResponse.java
    │       ├── UserResponse.java
    │       └── AddressResponse.java
    ├── entity/
    │   ├── User.java
    │   └── Address.java
    ├── repository/
    │   ├── UserRepository.java
    │   └── AddressRepository.java
    ├── service/
    │   ├── AuthService.java
    │   ├── UserService.java
    │   ├── JwtService.java
    │   └── impl/
    │       ├── AuthServiceImpl.java
    │       ├── UserServiceImpl.java
    │       └── JwtServiceImpl.java
    ├── exception/
    │   ├── GlobalExceptionHandler.java
    │   ├── UserNotFoundException.java
    │   ├── UserAlreadyExistsException.java
    │   └── InvalidCredentialsException.java
    └── util/
        └── SecurityUtils.java