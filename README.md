# 🌊 Watershed — Backend API

A lightweight Flask API powering the Watershed site’s dynamic content: **news posts, shows, gallery items, albums, and tracks**.
This backend supports your existing static front-end and allows you to update site content without touching the HTML.

---

## 📦 Tech Stack

* **Python 3.11+**
* **Flask** (API framework)
* **SQLAlchemy** (ORM)
* **PostgreSQL** (database)
* **Marshmallow** (serialization)

---

## 🗄 Database Schema (Updated)

The backend uses the following entities:

### **news_posts**

| Column     | Type         | Notes       |
| ---------- | ------------ | ----------- |
| id         | serial       | PK          |
| title      | varchar(200) | required    |
| body       | text         | required    |
| image_url  | varchar      | optional    |
| created_at | timestamp    | default NOW |

---

### **shows**

| Column      | Type      | Notes       |
| ----------- | --------- | ----------- |
| id          | serial    | PK          |
| title       | varchar   | required    |
| venue       | varchar   | required    |
| address     | varchar   | required    |
| city        | varchar   | required    |
| date        | date      | required    |
| time        | varchar   | required    |
| ticket_url  | varchar   | optional    |
| description | text      | optional    |
| created_at  | timestamp | default NOW |

---

### **albums**

| Column          | Type      | Notes       |
| --------------- | --------- | ----------- |
| id              | serial    | PK          |
| title           | varchar   | required    |
| release_date    | date      | required    |
| cover_image_url | varchar   | optional    |
| created_at      | timestamp | default NOW |

---

### **tracks**

(Each track belongs to an album.)

| Column       | Type      | Notes          |
| ------------ | --------- | -------------- |
| id           | serial    | PK             |
| album_id     | int       | FK → albums.id |
| title        | varchar   | required       |
| audio_url    | varchar   | required       |
| track_number | int       | optional       |
| created_at   | timestamp | default NOW    |

---

### **gallery_items**

| Column     | Type      | Notes       |
| ---------- | --------- | ----------- |
| id         | serial    | PK          |
| image_url  | varchar   | required    |
| caption    | varchar   | optional    |
| created_at | timestamp | default NOW |

---

## 🔗 API Endpoints

### **News Posts**

| Method | Endpoint         | Description         |
| ------ | ---------------- | ------------------- |
| GET    | `/api/news`      | List all news posts |
| GET    | `/api/news/<id>` | Get one post        |
| POST   | `/api/news`      | Create a news post  |
| PUT    | `/api/news/<id>` | Update a post       |
| DELETE | `/api/news/<id>` | Delete a post       |

---

### **Shows**

| Method | Endpoint          |
| ------ | ----------------- |
| GET    | `/api/shows`      |
| GET    | `/api/shows/<id>` |
| POST   | `/api/shows`      |
| PUT    | `/api/shows/<id>` |
| DELETE | `/api/shows/<id>` |

---

### **Albums**

| Method | Endpoint           |
| ------ | ------------------ |
| GET    | `/api/albums`      |
| GET    | `/api/albums/<id>` |
| POST   | `/api/albums`      |
| PUT    | `/api/albums/<id>` |
| DELETE | `/api/albums/<id>` |

---

### **Tracks**

| Method | Endpoint                        |
| ------ | ------------------------------- |
| GET    | `/api/albums/<album_id>/tracks` |
| GET    | `/api/tracks/<id>`              |
| POST   | `/api/albums/<album_id>/tracks` |
| PUT    | `/api/tracks/<id>`              |
| DELETE | `/api/tracks/<id>`              |

---

### **Gallery Items**

| Method | Endpoint            |
| ------ | ------------------- |
| GET    | `/api/gallery`      |
| GET    | `/api/gallery/<id>` |
| POST   | `/api/gallery`      |
| PUT    | `/api/gallery/<id>` |
| DELETE | `/api/gallery/<id>` |

---

## 📁 Project Structure (Flask)

```
watershed_api/
│── app.py
│── config.py
│── models/
│     ├── news_posts.py
│     ├── shows.py
│     ├── albums.py
│     ├── tracks.py
│     └── gallery_items.py
│── routes/
│     ├── news_routes.py
│     ├── show_routes.py
│     ├── album_routes.py
│     ├── track_routes.py
│     └── gallery_routes.py
│── schemas/
│── migrations/
└── README.md
```

---

## 🎯 Purpose of This API

This backend allows you to update the Watershed site dynamically without editing HTML.
Perfect for:

✔ Adding new shows
✔ Posting announcements / news
✔ Updating the gallery
✔ Managing albums & tracks
✔ Making the site fully maintainable

---

## 🧪 Future Enhancements

* Admin dashboard
* Authentication for posting content
* Search & filters
* Pagination
* Spotify/YouTube embeds for tracks

---


