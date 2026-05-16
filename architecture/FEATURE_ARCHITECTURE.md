# Feature-Based Architecture (የስርዓት አደረጃጀት)

This repository leverages a **Feature-Based Architecture** pattern rather than a traditional layered structure (such as putting all hooks, components, and actions into separate global folders). 

---

## 🧠 Core Philosophy

The fundamental goal of this design system is **high cohesion and low coupling**. Instead of organizing the codebase by technical definitions (e.g., placing every form in a massive global components folder), files are grouped directly by the **business domain capability** they fulfill.
By packaging UI components, server actions, data shapes, and local formatting utilities inside a single feature folder, the system gains a massive advantage: **Deleting or scaling a feature requires modifying files in exactly one domain directory.**

---

##  Feature Domain Breakdown

The application is split into three core feature spaces that define **Pawlos Online Qine Bet**:

### 1.  `features/admin/` (The Management Plane)
* **Responsibility:** Orchestrates curriculum creation, dynamic course mapping, and registration tracking workflows.
* **Core Mechanics:** * Houses the complex multi lingual form components where Memhir Pawlos builds out syllabus data trees (**ንባብ, ቅኔ, ግእዝ, and ባህረ ሃሳብ**).
  * Encapsulates secure server actions that process course edits, parse arrays, and validate pricing tiers before hitting the database layer.

### 2.  `features/student/` (The Learning Sanctuary)
* **Responsibility:** Delivers a secure, distraction free environment for registered students to consume assets.
* **Core Mechanics:**
  * Coordinates user session checks with  progress tracking layouts.
  * Optimizes heavy data dependencies (like rendering course timelines, playing instructional audio nodes, or downloading lesson PDFs) inside isolated sub routes.

### 3.  `features/public/` (The Discovery Node)
* **Responsibility:** Handles top-of-funnel guest discovery, anonymous browsing, and secure payment onboarding.
* **Core Mechanics:**
  * Completely public and heavily optimized for high speed edge delivery.
  * Encapsulates the enrollment visualizer system where new students scan pricing transparency details (the 300 ETB registration vs. 600 ETB regular tuition split) and interact with asynchronous clipboard copy utilities for bank transfers.

---

##  Structural Rules & Boundaries

To ensure this architectural style remains pristine as the system evolves, I instituted two strict architectural boundaries:

1. **The Shared Primitive Rule:** General components that do not hold domain specific logic such as a custom minimal input wrapper, an Apple style loading skeleton, or a primary submit button must live in `src/components/shared/` or `src/lib/`. They must never be coupled to a specific feature directory.
2. **The Strictly One Way Boundary:** A feature should never reach deep into another feature's folder to pull private elements. If `features/student/` requires a list layout originally engineered inside `features/admin/`, that layout must be refactored and extracted into a **shared feature model** or a global utility component. This prevents circular dependency traps.

---

##  Engineering Evaluation

### The Tradeoffs We Embraced

* **The Gain (Why I built it this way):** When working on the `fix/student-payment-ui` branch to resolve pricing confusion among users, my changes were completely isolated within `features/public/` and `features/student/`. The code driving the administrative database mutations remained entirely untouched, preventing development bugs from leaking into production engines.
* **The Cost (The Challenge):** It requires a higher level of discipline during initial system modeling. You have to constantly pause and ask yourself: *"Is this input component unique to the admin form, or will the student space need it tomorrow?"* This extra thought process pays off immensely down the line.