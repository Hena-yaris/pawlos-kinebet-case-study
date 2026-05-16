# Case Study: Pawlos Online Qine Bet (ጳውሎስ online ቅኔ ቤት)

A simple, mobile-first Progressive Web App (PWA) built to transform traditional Ethiopian Ge'ez scholarship into a structured, scalable, and distractionfree digital learning environment.

[ Live Application](https://www.pawloskinebet.com/) | [ LinkedIn Profile](https://www.linkedin.com/in/henayaris/)

---

##  Problem Statement

Traditional Ethiopian education covering **ንባብ (Nibab), ቅኔ (Qine), ግእዝ (Ge'ez), and ባህረ ሃሳብ (Bahre Hasab)** has long relied on physical classrooms and Telegram based learning groups.

While functional, this creates structural limitations:

- Learning materials (audio, PDFs, schedules) get buried in chat history
- Instructors face high administrative overhead managing students and payments
- There is no centralized system for scalable content organization
- Students struggle with discoverability and learning continuity

---

##  Product Vision

This project was designed as a **structured digital learning layer** on top of an existing educational community.

Not to replace the culture of learning but to organize and amplify it.

The system focuses on:

- Simplicity over complexity
- Mobile first accessibility
- Scalable content architecture
- Low friction user experience

---

##  UI / UX Direction

The design system follows a **minimalist academic aesthetic** inspired by traditional manuscript clarity:

- Soft parchment style background for readability
- High contrast typography for learning focus
- Card based modular layout for structured navigation
- Mobile first design for real world usage conditions

The goal was clarity, not decoration.

---


## 🏗️ Architecture Overview

Built using **Next.js 14 (App Router)** and MongoDB with a strict feature-based architecture.

```txt
src/
├── app/                 # Routing & layout layer
├── components/shared/   # Reusable UI primitives
├── models/              # Database schemas (User, Course)
└── features/
    ├── admin/           # Course management & instructor tools
    ├── public/          # Public course discovery pages
    └── student/         # Private learning dashboard


---


##  Key Engineering Takeaways

Building this platform forced me to shift my perspective from a developer writing isolated components to a system architect designing long-term solutions.

* **Domain Isolation over File Duplication** Transitioning to a feature-based architecture proved that grouping files by business capability (`admin`, `student`, `public`) dramatically reduces regression bugs. It ensures a modification to a course creation form can never accidentally degrade the student viewing layout.

* **Mastering Next.js Runtime Boundaries** Working extensively with the Next.js App Router reinforced the importance of strict data boundaries. Keeping database state logic entirely on the server and selectively nesting client interactivity inside isolated hydration roots keeps our mobile bundle size incredibly small.

* **UX is a Core System Requirement** Real-world system design doesn't end at the database. Moving from a text button to a precise copy-icon script and explicitly laying out the 300/600 ETB pricing breakdown proved that clean UI is just as critical for reducing user drop-off as zero-latency queries.

* **Community-Driven Guardrails** Building an active platform for an academy like *Pawlos Online Qine Bet* leaves no room for brittle code. Knowing that real instructors and students rely on this system daily forces better structural engineering decisions and thorough testing protocols.

---

##  Architectural Shift

> This project marked my clear transition from:
> **“Writing code that works”** $\rightarrow$ **“Designing systems that scale with purpose.”**

---

## 📎 Technical Blueprint & Infrastructure

To achieve a mobile-first, high-fidelity user interface that remains fast across changing network conditions, the platform relies on a focused stack of modern web technologies:

| Layer | Technology | Engineering Context |
| :--- | :--- | :--- |
| **Framework** | **Next.js 14 (App Router)** | Leveraged for native Server Actions, optimized edge routing, and built-in component boundary isolation. |
| **Language** | **TypeScript** | Enforces strict, type-safe data schemas across async mutations and data models. |
| **Database** | **MongoDB + Mongoose** | Selected for dynamic schema flexibility to gracefully manage localized, multi-lingual string payloads. |
| **Styles** | **Tailwind CSS** | Used to engineer a responsive design system with a clean, minimalist Apple-style visual hierarchy. |
| **Media Layer** | **Uploadthing** | Handles secure, serverless file streaming for course cover assets and manuscript visuals. |
| **Identity** | **Next-Auth** | Manages role-based identity boundaries to isolate administrative control panels from private student rooms. |




---

## Preview

### Home Experience

![Home Page](./assets/screenshots/landing.png)

### Student Experience

![Dashboard](./assets/screenshots/student-dashboard.png)

### Admin Experience

![Dashboard](./assets/screenshots/admin-dashboard.png)

### Login Experience

![Login](./assets/screenshots/login.png)

### Course View

![Courses](./assets/screenshots/course-detail.png)