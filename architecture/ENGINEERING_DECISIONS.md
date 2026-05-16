# Engineering Decisions & Technical Challenges

This document captures key engineering problems encountered during development and how they were solved.

---

## ⚙️ 1. Next.js Redirect Behavior in Server Actions

### Problem
Redirects inside server actions were not behaving as expected when wrapped inside try/catch blocks.

### Root Cause
Next.js uses an internal exception (`NEXT_REDIRECT`) to handle redirects.  
This exception was being caught unintentionally.

### Solution
- Isolated `redirect()` outside of try/catch boundaries
- Kept database logic inside error handling only

---

## ⚙️ 2. MongoDB + Client Boundary Issue

### Problem
MongoDB was being imported into client-side components, causing runtime errors (`net module not found`).

### Root Cause
Next.js bundled server-only modules into client-side builds due to incorrect imports.

### Solution
- Ensured all DB logic stays inside server actions or server components
- Removed any DB imports from client components

---

## ⚙️ 3. Feature-Based Refactor Decision

### Problem
Initial structure mixed UI, logic, and actions globally.

### Solution
Migrated to feature-based architecture:
- admin
- student
- public
- auth

This reduced coupling and improved scalability.

---

## 🧠 Key Learning

The most important shift was understanding:

> Framework correctness is not enough   boundary discipline is what makes apps production grade.