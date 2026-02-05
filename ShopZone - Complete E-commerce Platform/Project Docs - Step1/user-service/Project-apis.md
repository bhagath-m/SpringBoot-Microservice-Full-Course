## AUTHENTICATION APIs:

   POST /api/auth/register           → John creates account (email, password, name, phone).
   
   POST /api/auth/login              → John logs in (returns JWT token).
   
   POST /api/auth/refresh-token      → Refresh expired token.
   
   POST /api/auth/logout             → John logs out.
   
   POST /api/auth/forgot-password    → John forgot password, send reset email.
   
   POST /api/auth/reset-password     → John resets password using email token.
   

## USER PROFILE APIs:

   GET  /api/users/profile           → Get John's profile details
   
   PUT  /api/users/profile           → John updates his name, phone etc.
   
   PUT  /api/users/change-password   → John changes his password
   
   DELETE /api/users/account         → John deletes his account
   

## ADDRESS MANAGEMENT APIs (needed for delivery later):

   GET    /api/users/addresses       → Get all saved addresses of John
   
   POST   /api/users/addresses       → John adds new delivery address
   
   PUT    /api/users/addresses/{id}  → John updates an address

   DELETE /api/users/addresses/{id}  → John deletes an address
   
   PUT    /api/users/addresses/{id}/default → John sets default delivery address
   

## INTERNAL APIs (used by other microservices via Feign Client):

   GET  /internal/users/{userId}     → Other services fetch John's details
   
   GET  /internal/users/email/{email} → Fetch user by email
   
   POST /internal/users/validate-token → Validate if John's JWT token is valid
   
