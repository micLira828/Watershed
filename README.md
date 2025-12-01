---

# 🎸 Watershed Band Backend (Flask Fullstack)

A Flask-powered backend that renders dynamic pages and exposes JSON API routes for the Watershed Band website.

This backend manages the band’s content, including shows, albums, tracks, news posts, band members, gallery items, subscribers, and contact messages. It uses PostgreSQL + SQLAlchemy for data modeling and Jinja templates for HTML rendering.

---

## 📖 Overview

This project is a hybrid Flask application that supports:

* **Public-facing HTML pages** rendered with Jinja
* **JSON API routes** for admin tools, integrations, or future dashboards
* **PostgreSQL database** with SQLAlchemy ORM
* **JWT-based admin authentication**

This backend makes the Watershed Band site fully dynamic while preserving the existing frontend design.

---

## 🗂 Tech Stack

* Python
* Flask
* Jinja2 Templates
* SQLAlchemy ORM
* PostgreSQL
* JWT Authentication
* Werkzeug Security

---

## 🧠 Core Features

### Public-Facing

* List and view **shows**
* Browse **albums**
* View individual **album detail pages** with tracklists
* Read **news posts**
* View **band members**
* Browse the **photo gallery**
* Submit **contact messages**
* Subscribe to the **email list**

### Admin (via JSON API)

* Manage shows
* Manage albums & tracks
* Manage news posts
* Manage band members
* Manage gallery items
* View contact messages
* View subscriber list

---

# 🔄 Page Routes (HTML, Jinja)

```
GET /                   # home
GET /shows              # upcoming shows
GET /albums             # all albums
GET /albums/<id>        # single album + tracks
GET /news               # all news posts
GET /news/<id>          # single news post
GET /members            # band members
GET /gallery            # photo gallery
GET /contact            # contact form page
POST /contact           # submit form → save message
POST /subscribe         # subscribe to email list
```

---

# 🧊 JSON API Routes (Admin / Programmatic)

All JSON routes begin with `/api`.

---

### 🔐 Authentication

```
POST /api/auth/login
GET  /api/auth/me
```

---

### 🎤 Shows API

```
GET    /api/shows
GET    /api/shows/<id>
POST   /api/shows
PUT    /api/shows/<id>
DELETE /api/shows/<id>
```

---

### 💿 Albums & Tracks API

```
GET    /api/albums
GET    /api/albums/<id>
POST   /api/albums
PUT    /api/albums/<id>
DELETE /api/albums/<id>
```

Tracks:

```
GET    /api/albums/<album_id>/tracks
POST   /api/albums/<album_id>/tracks
PUT    /api/tracks/<track_id>
DELETE /api/tracks/<track_id>
```

---

### 📰 News API

```
GET    /api/news
GET    /api/news/<id>
POST   /api/news
PUT    /api/news/<id>
DELETE /api/news/<id>
```

---

### 🎸 Band Members API

```
GET    /api/members
GET    /api/members/<id>
POST   /api/members
PUT    /api/members/<id>
DELETE /api/members/<id>
```

---

### 🖼 Gallery API

```
GET    /api/gallery
GET    /api/gallery/<id>
POST   /api/gallery
DELETE /api/gallery/<id>
```

---

### 📧 Subscribers API

```
POST /api/subscribe
GET  /api/subscribers
```

---

### ✉️ Contact Messages API

```
POST /api/contact
GET  /api/contact
GET  /api/contact/<id>
```

---

# 🏗 Database Schema (SQLAlchemy Summary)

Models include:

* `User` — Admin authentication
* `Show` — Live shows
* `Album` — Music releases
* `Track` — Tracks belonging to albums
* `NewsPost` — Blog/news posts
* `BandMember` — Members of the band
* `GalleryItem` — Photo gallery items
* `Subscriber` — Email list
* `ContactMessage` — Form submissions

A full dbdiagram is included in:
`schema.dbdiagram.txt`

---

# 📁 Project Structure

```
watershed_backend/
│
├── app.py
├── config.py
├── requirements.txt
├── .env
│
├── templates/
│   ├── base.html
│   ├── index.html
│   ├── shows.html
│   ├── albums.html
│   ├── album_detail.html
│   ├── news.html
│   ├── news_detail.html
│   ├── members.html
│   ├── gallery.html
│   ├── contact.html
│   └── subscribe_success.html
│
├── static/
│   ├── css/
│   ├── js/
│   └── images/
│
├── models/
│   ├── __init__.py
│   ├── user.py
│   ├── show.py
│   ├── album.py
│   ├── track.py
│   ├── news_post.py
│   ├── band_member.py
│   ├── gallery_item.py
│   ├── subscriber.py
│   └── contact_message.py
│
├── routes/
│   ├── __init__.py
│   ├── page_routes.py
│   ├── auth_routes.py
│   ├── show_routes.py
│   ├── album_routes.py
│   ├── track_routes.py
│   ├── news_routes.py
│   ├── member_routes.py
│   ├── gallery_routes.py
│   ├── subscriber_routes.py
│   └── contact_routes.py
│
├── db/
│   ├── __init__.py
│   └── database.py
│
└── tasks.csv   # Trello planning
```

---

# 🚀 Getting Started

### 1. Create virtual environment

```
python -m venv venv
source venv/bin/activate
```

### 2. Install dependencies

```
pip install -r requirements.txt
```

### 3. Create `.env`

```
FLASK_APP=app.py
FLASK_ENV=development
DATABASE_URL=postgresql://user:pass@localhost:5432/watershed_api
JWT_SECRET=supersecretkey
```

### 4. Initialize the database

Run migrations or a custom setup script.

### 5. Start the server

```
flask run
```

---

# 🧩 Included Files

* `schema.dbdiagram.txt` – for DB modeling
* `tasks.csv` – Trello Kanban import

---

# ✨ Author

**Michelle Liran Gepshtein**
Digital Alchemist • Full-Stack Developer (Flask, Python, SQLAlchemy, Jinja2)

---
