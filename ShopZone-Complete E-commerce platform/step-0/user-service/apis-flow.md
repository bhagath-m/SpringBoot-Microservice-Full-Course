# User Service

## Overview

- **Service Name:** User Service  
- **Port:** 8081  
- **Purpose:** User authentication, authorization, profile management, and address management  
- **Database:** MySQL (`shopzone_users`)

---

## Database Schema

### users

Stores user account information.

| Column Name | Type | Constraints | Description |
|------------|------|-------------|-------------|
| id | BIGINT | PRIMARY KEY, AUTO_INCREMENT | Unique user identifier |
| email | VARCHAR(255) | UNIQUE, NOT NULL | User's email (login) |
| password | VARCHAR(255) | NOT NULL | Encrypted password (BCrypt) |
| first_name | VARCHAR(100) | NOT NULL | User's first name |
| last_name | VARCHAR(100) | NULL | User's last name |
| phone | VARCHAR(20) | NULL | Phone number |
| is_active | BOOLEAN | DEFAULT TRUE | Account status |
| created_at | TIMESTAMP | AUTO | Creation timestamp |
| updated_at | TIMESTAMP | AUTO | Last update timestamp |

---

### roles

Stores role definitions.

| Column Name | Type | Constraints | Description |
|------------|------|-------------|-------------|
| id | BIGINT | PRIMARY KEY, AUTO_INCREMENT | Role ID |
| name | VARCHAR(50) | UNIQUE, NOT NULL | Role name |
| description | TEXT | NULL | Role description |
| created_at | TIMESTAMP | AUTO | Created time |

**Default Roles**
- ROLE_CUSTOMER
- ROLE_SELLER
- ROLE_ADMIN

---

### user_roles

Many-to-many mapping between users and roles.

| Column Name | Type | Constraints |
|------------|------|-------------|
| user_id | BIGINT | FK → users(id) |
| role_id | BIGINT | FK → roles(id) |

**Composite Primary Key:** (user_id, role_id)

---

### addresses

Stores user delivery addresses.

| Column Name | Type | Constraints | Description |
|------------|------|-------------|-------------|
| id | BIGINT | PRIMARY KEY, AUTO_INCREMENT | Address ID |
| user_id | BIGINT | FK → users(id), NOT NULL | User reference |
| address_line1 | VARCHAR(255) | NOT NULL | Address line 1 |
| address_line2 | VARCHAR(255) | NULL | Address line 2 |
| city | VARCHAR(100) | NOT NULL | City |
| state | VARCHAR(100) | NOT NULL | State |
| country | VARCHAR(100) | NOT NULL | Country |
| pincode | VARCHAR(10) | NOT NULL | Postal code |
| is_default | BOOLEAN | DEFAULT FALSE | Default address |

---

### password_reset_tokens

Stores password reset tokens.

| Column Name | Type | Constraints | Description |
|------------|------|-------------|-------------|
| id | BIGINT | PRIMARY KEY, AUTO_INCREMENT | Token ID |
| token | VARCHAR(255) | UNIQUE, NOT NULL | Reset token |
| email | VARCHAR(255) | NOT NULL | User email |
| expiry_date | TIMESTAMP | NOT NULL | Expiry time |
| used | BOOLEAN | DEFAULT FALSE | Token used |
| created_at | TIMESTAMP | AUTO | Created time |

---

# API Endpoints

## 🔐 Authentication APIs

### Register New User
- **Endpoint:** POST /api/auth/register  
- **Access:** Public  
- **Description:** Creates a new user account with default role  

---

### Login
- **Endpoint:** POST /api/auth/login  
- **Access:** Public  
- **Description:** Authenticates user and returns JWT tokens  

---

### Refresh Token
- **Endpoint:** POST /api/auth/refresh-token  
- **Access:** Public  
- **Description:** Generates new access token using refresh token  

---

### Logout
- **Endpoint:** POST /api/auth/logout  
- **Access:** Public  
- **Description:** Logs out user (client-side token removal)  

---

## 👤 User Profile APIs

### Get Current User Profile
- **Endpoint:** GET /api/users/profile  
- **Access:** Authenticated  
- **Description:** Retrieves logged-in user's profile  

---

### Update User Profile
- **Endpoint:** PUT /api/users/profile  
- **Access:** Authenticated  
- **Description:** Updates user's profile details  

---

### Change Password
- **Endpoint:** PUT /api/users/change-password  
- **Access:** Authenticated  
- **Description:** Changes user's password  

---

### Delete Account
- **Endpoint:** DELETE /api/users/account  
- **Access:** Authenticated  
- **Description:** Soft deletes user account  

---

## 📍 Address Management APIs

### Get All Addresses
- **Endpoint:** GET /api/users/addresses  
- **Access:** Authenticated  
- **Description:** Retrieves all addresses of logged-in user  

---

### Add New Address
- **Endpoint:** POST /api/users/addresses  
- **Access:** Authenticated  
- **Description:** Adds a new address for the user  

---

### Update Address
- **Endpoint:** PUT /api/users/addresses/{id}  
- **Access:** Authenticated  
- **Description:** Updates an existing address  
- **Path Parameters:**  
  - id — Address ID  

---

### Delete Address
- **Endpoint:** DELETE /api/users/addresses/{id}  
- **Access:** Authenticated  
- **Description:** Deletes an address  
- **Path Parameters:**  
  - id — Address ID  

---

### Set Default Address
- **Endpoint:** PUT /api/users/addresses/{id}/default  
- **Access:** Authenticated  
- **Description:** Sets an address as default  
- **Path Parameters:**  
  - id — Address ID  

---

## 🔑 Role Management APIs

### Get All Roles
- **Endpoint:** GET /api/roles  
- **Access:** Public  
- **Description:** Retrieves all available roles  

---

## 🔗 Internal APIs

### Get User By ID
- **Endpoint:** GET /internal/users/{userId}  
- **Access:** Internal only  
- **Description:** Retrieves user details by user ID  
- **Path Parameters:**  
  - userId — User ID  

---

### Get User By Email
- **Endpoint:** GET /internal/users/email/{email}  
- **Access:** Internal only  
- **Description:** Retrieves user details by email  
- **Path Parameters:**  
  - email — User email address  
