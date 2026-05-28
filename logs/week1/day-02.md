# Daily Work Log | E-Commerce API Development

## 📅 Date: May 21, 2026

**Status:** Complete (Database Design Phase)

---

## 🛠️ Today's Accomplishments

* Successfully finalized the **Database Schema Design** for the core e-commerce API.
* Mapped out relational tables, primary/foreign key constraints, and essential indexes.
* Designed core entities including:
  * **Users & Roles** (Authentication/Authorization)
  * **Products, Categories, & Inventory** (Catalog Management)
  * **Orders & Order Items** (Transactional Data)
  * **Cart & Cart Items** (Session/State Management)

---

## 🔍 Database Design Review: Common Mistakes & Fixes

Before locking in the schema and moving to the implementation phase, it is highly recommended to double-check the design against these common e-commerce database architectural pitfalls:

### 1. Using FLOAT Instead of DECIMAL(10,2) for Monetary Values

* **The Mistake:** Using `FLOAT`, `REAL`, or `DOUBLE` data types for storing prices, taxes, and order totals. Floating-point types use approximate math, which introduces tiny rounding errors over time (e.g., a total calculation might randomly result in `$19.9999994` instead of `$20.00`), causing financial reports to mismatch.
* **The Fix:** Always use `DECIMAL(10,2)` (or `NUMERIC`). This forces the database to store exact fixed-point numbers, ensuring exact mathematical accuracy for currencies.
