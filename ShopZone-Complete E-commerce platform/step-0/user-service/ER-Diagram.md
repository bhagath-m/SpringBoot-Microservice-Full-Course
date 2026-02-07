## **Entity Relationship Diagram**
```
┌─────────────────┐
│     users       │
├─────────────────┤
│ id (PK)         │
│ email           │
│ password        │
│ first_name      │
│ last_name       │
│ phone           │
│ is_active       │
│ created_at      │
│ updated_at      │
└─────────────────┘
        │
        │ 1
        │
        │ N
        ▼
┌─────────────────┐         ┌─────────────────┐
│  user_roles     │    N    │     roles       │
├─────────────────┤ ◄────── ├─────────────────┤
│ user_id (FK)    │         │ id (PK)         │
│ role_id (FK)    │         │ name            │
└─────────────────┘         │ description     │
                            │ created_at      │
                            └─────────────────┘

┌─────────────────┐
│     users       │
└─────────────────┘
        │
        │ 1
        │
        │ N
        ▼
┌─────────────────┐
│   addresses     │
├─────────────────┤
│ id (PK)         │
│ user_id (FK)    │
│ address_line1   │
│ address_line2   │
│ city            │
│ state           │
│ country         │
│ pincode         │
│ is_default      │
└─────────────────┘
