# Product Details: iPhone 15 Pro

**Variants:**

* **iPhone 15 Pro - 128GB - Natural Titanium**
    * **SKU:** IP15P-128-NT
    * **Stock:** 50
* **iPhone 15 Pro - 256GB - Blue Titanium**
    * **SKU:** IP15P-256-BT
    * **Stock:** 30
* **iPhone 15 Pro - 512GB - Black Titanium**
    * **SKU:** IP15P-512-BK
    * **Stock:** 0
    * **Availability:** False

---

## Entity Relationship Diagram

```text
┌─────────────────┐
│   categories    │
├─────────────────┤
│ id (PK)         │
│ name            │
│ description     │
│ image_url       │
│ is_active       │
│ parent_id (FK)  │───┐
│ created_at      │   │ Self-referencing
│ updated_at      │   │ (Parent-Child)
└─────────────────┘   │
        │             │
        │ 1           │
        │             │
        │ N           │
        ▼             │
┌─────────────────┐   │
│    products     │   │
├─────────────────┤   │
│ id (PK)         │   │
│ name            │   │
│ description     │   │
│ category_id(FK) │───┘
│ brand_id (FK)   │───────┐
│ base_price      │       │
│ discount_%      │       │
│ sku             │       │
│ is_active       │       │
│ specifications  │       │
│ average_rating  │       │
│ review_count    │       │
│ created_at      │       │
│ updated_at      │       │
└─────────────────┘       │
        │                 │
        │ 1               │
        │                 │
        │ N               │        ┌─────────────────┐
        ▼                 │        │     brands      │
┌─────────────────┐       │        ├─────────────────┤
│ product_images  │       └────────│ id (PK)         │
├─────────────────┤                │ name            │
│ id (PK)         │                │ description     │
│ product_id (FK) │                │ logo_url        │
│ image_url       │                │ is_active       │
│ is_primary      │                │ created_at      │
│ display_order   │                │ updated_at      │
└─────────────────┘                └─────────────────┘

┌─────────────────┐
│    products     │
└─────────────────┘
        │
        │ 1
        │
        │ N
        ▼
┌─────────────────┐
│product_variants │
├─────────────────┤
│ id (PK)         │
│ product_id (FK) │
│ variant_name    │
│ sku             │
│ price           │
│ attributes      │
│ stock_quantity  │
│ is_available    │
└─────────────────┘
