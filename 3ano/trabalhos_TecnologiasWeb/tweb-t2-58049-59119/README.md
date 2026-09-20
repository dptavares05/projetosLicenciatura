# Room Rent — University Student Housing Platform

Full-stack web application engineered to simulate a student union housing management system, facilitating university room rentals by connecting landlords (listings) and students (housing requests). Built with a robust MVC architecture, relational data persistence, and fine-grained access control.

Developed as part of the Web Technologies curriculum at the University of Évora.

---

## Tech Stack & Tools

### Core Technologies & Frameworks
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/postgresql-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![Thymeleaf](https://img.shields.io/badge/thymeleaf-%23005F0F.svg?style=for-the-badge&logo=thymeleaf&logoColor=white)
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)
![Maven](https://img.shields.io/badge/Apache%20Maven-C71A36?style=for-the-badge&logo=Apache%20Maven&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

---

## System Architecture

The system is structured following the **Model-View-Controller (MVC)** architectural pattern to ensure separation of concerns, maintainability, and clean code boundaries:

| Layer / Component | Technology | Responsibility |
| :--- | :--- | :--- |
| **Backend / API** | Java & Spring Boot | Core domain logic, routing controllers, transaction coordination, and security rules. |
| **Persistence** | PostgreSQL & Spring Data JPA | Relational data schema management, query optimization, and entity mappings. |
| **Presentation** | Thymeleaf & CSS3 (Flexbox) | Server-side rendered responsive user interface without external framework bloat. |
| **Security** | Spring Security | Role-based access control (RBAC), session management, and cryptographic password hashing. |

---

## Access Levels & Core Features

* **Public Portal**:
  * Dynamic dashboard aggregating the latest listings (rooms offered vs. housing requests).
  * Multi-parameter search engine with filtering by zone, listing type, and free-text queries.
* **Private User Dashboard (Authenticated Landlords & Students)**:
  * Full lifecycle listing management (create, update, and remove housing offers or search posts).
  * Internal private messaging channel enabling direct, real-time communication between landlords and prospective student tenants.
  * Account profile center managing user preferences and credentials.
* **Administration & Moderation Suite**:
  * Moderation engine for user account lifecycle (review, approval, and moderation of new registrations).
  * Platform-wide content governance and validation for all submitted housing listings.

---

## Key Technical Decisions

* **Advanced JPA Queries**: Utilized custom `@Query` definitions and advanced repository specifications in Spring Data JPA to support composite, multi-criteria filtering across large datasets.
* **Granular Security Architecture**: Mitigated critical vulnerabilities (such as Broken Object-Level Authorization) by enforcing strict method-level and URL-based security constraints.
* **Lightweight Custom UI**: Implemented a responsive user experience using modern CSS3 (Flexbox) rather than heavy CSS frameworks (e.g., Bootstrap), minimizing bundle overhead and ensuring bespoke visual styling.

---

## Repository Structure

```text
├── src/
│   ├── main/
│   │   ├── java/                 # Application source code (Controllers, Services, Models, Repositories)
│   │   └── resources/
│   │       ├── static/           # Static assets (CSS stylesheets, images, client scripts)
│   │       ├── templates/        # Thymeleaf server-side templates
│   │       └── application.properties # Environment and database configuration
├── relatorio.pdf                 # Comprehensive technical documentation & report
└── pom.xml                       # Maven dependencies and build lifecycle setup
```
