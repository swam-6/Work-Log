# 📅 Day 3: Implementing Authentication Module with Spring Security & JWT

**Date:** 2026-05-22  
**Phase:** Core Backend Development

---

## 🎯 Today's Goals
- [x] Begin implementation of the Auth Module for Spring Boot backend
- [x] Resolve JWT secret key encoding issues
- [x] Clarify MySQL service vs. WAMP UI behavior

---

## 💻 Work Status & Progress

* **Architecture & Design:** 
  * Started implementing the **Auth Module** using Spring Security and JWT for the Spring Boot backend.
  * Designed JWT token handling with proper secret key encoding.

* **Code / Configuration:** 
  * Configured JWT secret key handling using UTF-8 byte encoding instead of Base64 decoding.
  * Updated Keys configuration to properly handle plain-text secrets without Base64 processing.

* **Blockers Overcome:**
  * **JWT Base64 Decoding Error** – Discovered that plain-text JWT secrets were failing with "Illegal base64 character: '-'" error. Fixed by switching to `secretKey.getBytes(StandardCharsets.UTF_8)` instead of Base64 decoding.
  * **MySQL / WAMP Confusion** – Clarified that Spring Boot connects directly to `mysqld.exe` process, not through WAMP UI. WAMP is just a management interface; MySQL runs independently as a Windows service.

---

## 🧠 What I Learned & Key Takeaways

* **JWT Secret Key Encoding:**
  * *Insight:* JWT secret keys should use UTF-8 byte encoding, not Base64 decoding, unless the key is explicitly Base64-encoded in configuration. Plain-text secrets containing characters like `-` are invalid in Base64.

* **WAMP vs. MySQL Service Architecture:**
  * *Insight:* WAMP is a UI wrapper around MySQL; the database engine (`mysqld.exe`) runs independently as a Windows service. Turning off the WAMP tray icon doesn't stop MySQL — must explicitly stop the MySQL service via Windows Services (`services.msc`) or Task Manager to fully disable the database.

* **Database Connectivity Debugging:**
  * *Insight:* Always verify which process is actually serving database connections when debugging connectivity issues. Don't assume UI wrappers control the underlying services.
