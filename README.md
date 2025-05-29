# AcademicJournal

A full-fledged academic journal platform for publishing and peer-reviewing research code. This project supports federated journal systems, allowing multiple teams to interconnect their journals via SSO and submission migration. Built with extensibility and collaboration at its core.

## ✨ Features

- 🔐 Secure single sign-on (SSO) federation login across journals
- 📝 Submissions with versioning, co-authors, and comment threads
- 📊 Customisable dashboard with real-time notifications and announcements
- 💬 Private multi-user discussions and stylized markdown comments
- 📦 Attach supporting documents, Jupyter notebooks, PDFs, and more
- 📤 GitHub integration for pulling submission repositories
- 🚦 Tiered role system: Users, Reviewers, Editors, and Administrators
- 🚫 Reporting and banning system for user moderation
- 🔍 Search functionality (basic title-based)
- 🔄 Submission migration between journals
- ✅ Email verification, password reset via email
- 🔐 Asymmetric encryption for sensitive requests
- 🧪 Comprehensive unit and integration tests

> **Note:** This list is not exhaustive. The project contains numerous additional enhancements beyond the required features.

---

## 📚 Motivation

AcademicJournal was developed to address the lack of a dedicated, sociable, and federated platform for reviewing and publishing research software. Unlike GitHub, our system adapts to academic peer-review workflows by allowing inline feedback, submission versioning, structured roles, and collaborative discussions.

---

## 🛠️ Tech Stack

- **Frontend**: ReactJS
- **Backend**: Node.js with Express
- **Database**: MongoDB
- **Caching**: Redis
- **Containerization**: Podman
- **Testing**: Jest for unit/integration tests

---

## 🚀 Getting Started

### Requirements

- Podman (recommended container runtime)
- MongoDB
- Redis

### Setup

1. Navigate to the `production` folder.
2. Run the provided Podman script:
   ```bash
       ./podman/run_production_podman.sh <port-number>
   ```
3. Access the app at `http://localhost:<port-number>`

> The script sets up all necessary dependencies inside a Podman pod.

---

## 🧪 Running Tests

1. Stop the container using `Ctrl + C`.
2. Start an interactive session:

   ```bash
   podman exec -it code_review bash
   ```
3. Run backend tests:

   ```bash
   cd backend
   npm run test_unit        # Unit tests
   npm run test_integration # Integration tests
   ```

---

## 🧑‍⚖️ Roles & Permissions

* New users are assigned the `user` role by default.
* To upgrade yourself (for development):

  ```bash
  podman exec -it mongo_cs3099 mongosh
  use code_review
  db.users.updateOne({id: '<youruserid>'}, {$set: {role: 3}})
  ```

Roles:

* **User**: Can submit and discuss
* **Reviewer**: Can review submissions
* **Editor**: Can assign reviewers and publish
* **Admin**: Full privileges

---
