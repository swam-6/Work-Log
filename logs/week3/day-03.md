# Day 13: Entity Design and Relational Mapping for Cart Module

**Date:** 2026-06-03  
**Phase:** Core Backend Development

---

## Today's Goals

- [x] Design and implement the Cart entity inside the Cart Module
- [x] Design and implement the Cart Item entity to handle line-item details
- [x] Map the relationships between Cart, Cart Item, and User/Product entities
- [ ] Create repository interfaces for Cart and Cart Item entities
- [ ] Design and implement Data Transfer Objects (DTOs) for Cart operations

---

## Work Status & Progress

> A concise, bulleted summary of what you built, designed, or resolved today.

- **Architecture & Design:**
  - Mapped out the database entities for the Cart Module, establishing the relational mapping between users, carts, cart items, and catalog products.
  - Structured a bidirectional one-to-many relationship between the `Cart` entity and `CartItem` entities.
- **Code / Configuration:**
  - **Cart Entity:** Created the `Cart` domain model containing user associations, a collection of cart items, and overall cart total and item count attributes.
  - **Cart Item Entity:** Coded the `CartItem` domain model to represent individual line items, linking each entry to a specific `Product` and capturing quantities and unit pricing.
- **Blockers Overcome:**
  - Configured cascade and orphan removal settings (`cascade = CascadeType.ALL, orphanRemoval = true`) on the bidirectional mapping to prevent orphan records in the database when removing items from the cart.

---

## What I Learned & Key Takeaways

> Document technical concepts, architectural choices, or new tools mastered today.

- **JPA Cascade & Bidirectional Mapping:**
  - *Insight:* Learned how to configure and synchronize bidirectional relationships properly in Spring Data JPA. Ensuring that utility helper methods are used to add/remove items ensures both sides of the object graph remain in sync before database commits.
- **Handling Database Orphans:**
  - *Insight:* Understood why `orphanRemoval = true` is critical for cart mechanics, ensuring that items deleted from the memory list are actively deleted as rows in the database, avoiding database leak issues.

---

## Module Milestone Status

> Summary of completed modules so far.

- **Auth Module:** Completed and fully integrated with JWT Bearer security.
- **Category Module:** Completed and fully tested from controller to repository.
- **Product Module:** Fully completed, tested E2E in Swagger UI, and equipped with dynamic filtering and pageable endpoints.
- **Cart Module:** In progress. Entity design and relational mapping completed.

---

## Next Steps

- Create repository interfaces for `Cart` and `CartItem` entities.
- Draft Data Transfer Objects (DTOs) for cart requests and responses, preparing for service-level mapping and controller implementation.
