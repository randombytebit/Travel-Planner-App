<div align="center">

# Travel Planner

**A full-stack web application for planning, managing, and budgeting your trips.**

[![Node.js](https://img.shields.io/badge/Node.js-18.x-339933?style=flat-square&logo=node.js&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-4.x-000000?style=flat-square&logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-6.x-47A248?style=flat-square&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=flat-square&logo=bootstrap&logoColor=white)](https://getbootstrap.com/)
[![Live Demo](https://img.shields.io/badge/Live%20Demo-Render-46E3B7?style=flat-square&logo=render&logoColor=white)](https://hkmu381-travel-planner-app.onrender.com)

[Live Demo](https://hkmu381-travel-planner-app.onrender.com) · [Report Bug](https://github.com/) · [Request Feature](https://github.com/)

</div>

---

## Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [REST API Reference](#-rest-api-reference)
- [Team](#-team)

---

## About the Project

Travel Planner is a cloud-deployed web application that allows users to plan trips, manage itineraries, and calculate travel budgets — all in one place. Built with Node.js and MongoDB, it supports full user authentication, CRUD operations for trips, and an interactive budget calculator with chart exports.

**Live at:** [https://hkmu381-travel-planner-app.onrender.com](https://hkmu381-travel-planner-app.onrender.com)

---

## Features

| Category | Feature |
|---|---|
| **Authentication** | Register, Login, Logout, Profile Management |
| **Trip Management** | Create, View, Edit, Delete Trips |
| **Budget Calculator** | Calculate total trip costs & export pie chart |
| **Contact Form** | Submit inquiries to admin |
| **Profile** | Update name, email, and password |
| **Admin Panel** | View all user contact submissions |

---

## Tech Stack

**Backend**
- [Node.js](https://nodejs.org/) + [Express.js](https://expressjs.com/)
- [MongoDB](https://www.mongodb.com/) + [Mongoose](https://mongoosejs.com/)
- [Passport.js](http://www.passportjs.org/) — Local, Facebook & Instagram OAuth
- [bcrypt](https://github.com/kelektiv/node.bcrypt.js) — Password hashing
- [EJS](https://ejs.co/) — Server-side templating

**Frontend**
- [Bootstrap 5](https://getbootstrap.com/)
- [Font Awesome 4](https://fontawesome.com/)
- Vanilla JavaScript (smooth scroll, form validation, card hover effects)

**Infrastructure**
- [Render](https://render.com/) — Cloud deployment
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) — Cloud database

---

## Project Structure

```
travel-planner/
├── models/
│   ├── Contact.js          # Contact form submissions
│   ├── Trip.js             # Trip data model
│   └── User.js             # User accounts & auth
├── routes/                 # Express route handlers
├── views/
│   ├── admin/
│   │   └── contacts.ejs    # Admin contact list
│   ├── partials/
│   │   ├── header.ejs
│   │   ├── footer.ejs
│   │   └── messages.ejs    # Flash messages
│   ├── trips/
│   │   ├── new.ejs
│   │   └── edit.ejs
│   ├── index.ejs           # Landing page
│   ├── dashboard.ejs
│   ├── login.ejs
│   ├── register.ejs
│   ├── my-trips.ejs
│   ├── trip-planner.ejs
│   ├── budget-calculator.ejs
│   ├── profile.ejs
│   ├── contact.ejs
│   └── about.ejs
├── public/
│   ├── js/main.js          # Client-side JS
│   └── css/style.css
├── .env                    # Environment variables (not committed)
├── .env.sample
├── server.js               # App entry point
└── package.json
```

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18+
- A [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) account

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/travel-planner.git
   cd travel-planner
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**

   Copy the sample env file and fill in your values:
   ```bash
   cp .env.sample .env
   ```

   ```env
   SESSION_SECRET=your_session_secret_here
   MONGODB_URL=your_mongodb_atlas_connection_string
   ```

4. **Start the development server**
   ```bash
   npm run dev
   ```

5. **Verify the server is running**

   You should see:
   ```
   server is running on port 3001
   Connected to MongoDB
   MongoDB Atlas Connected
   Database ping Check Connection successful
   ```

6. **Open your browser** at [http://localhost:3001](http://localhost:3001)

### Quick Start (User Flow)

```
Home → Register → Login → Dashboard → Add Trip
```

---

## 📡 REST API Reference

The application exposes a RESTful API for user management at `/users`.

> **Base URL (local):** `http://localhost:3001`  
> **Base URL (production):** `https://hkmu381-travel-planner-app.onrender.com`

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/users` | Get all users |
| `GET` | `/users/:id` | Get a user by ID |
| `POST` | `/users` | Create a new user |
| `PATCH` | `/users/:id` | Update a user |
| `DELETE` | `/users/:id` | Delete a user |

### Examples

<details>
<summary><b>POST</b> — Create a user</summary>

```bash
curl -X POST http://localhost:3001/users \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "email": "john@example.com",
    "password": "password123"
  }'
```
</details>

<details>
<summary><b>GET</b> — Fetch all users</summary>

```bash
curl http://localhost:3001/users
```
</details>

<details>
<summary><b>GET</b> — Fetch a specific user</summary>

```bash
curl http://localhost:3001/users/{USER_ID}
```
</details>

<details>
<summary><b>PATCH</b> — Update a user</summary>

```bash
# Update a single field
curl -X PATCH http://localhost:3001/users/{USER_ID} \
  -H "Content-Type: application/json" \
  -d '{"name": "Updated Name"}'

# Update multiple fields
curl -X PATCH http://localhost:3001/users/{USER_ID} \
  -H "Content-Type: application/json" \
  -d '{
    "name": "New Name",
    "email": "newemail@example.com"
  }'
```
</details>

<details>
<summary><b>DELETE</b> — Delete a user</summary>

```bash
curl -X DELETE http://localhost:3001/users/{USER_ID}
```
</details>

---

## Team

**COMP S381F — Group 8**

| Name | Student ID | Role |
|------|-----------|------|
| **Ng Man Hei** *(Group Leader)* | 13505304 | |
| Tse Man Hin | 13515463 | |
| Wong Sin Ngai | 13588511 | |
| Pau Ka Lok | 13068093 | |
| Leung Aidan | 13626010 | |

---

<div align="center">

Made with by Group 8 · COMP S381F

</div>
