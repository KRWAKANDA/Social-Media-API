# Social Media API

A RESTful Social Media API built with **Django** and **Django REST Framework (DRF)**.
This API allows users to register, create posts, follow other users, and view a feed of posts from followed users. It also implements JWT authentication for secure access.

---

## **Features**

### Core Functionality

* **User Management**: Register, view, update, and delete user profiles.
* **Post Management**: Create, read, update, and delete posts (with optional media).
* **Follow System**: Follow and unfollow other users.
* **Feed**: View posts from users you follow in reverse chronological order.
* **Authentication**: JWT-based authentication for secure API access.
* **Pagination**: Paginated post lists and feeds for efficient browsing.

### Optional Stretch Goals (Future Enhancements)

* Likes and comments
* Media uploads (images/videos to cloud storage)
* Hashtags and mentions
* Notifications
* Direct messaging

---

## **Tech Stack**

* Python 3.10+
* Django 4.x
* Django REST Framework
* Simple JWT (for token-based authentication)
* SQLite (default DB, can be switched to PostgreSQL or MySQL)
* Pillow (for image handling)

---

## **Project Structure**

```
social_api/
├─ social_api/
│  ├─ settings.py
│  └─ urls.py
├─ users/
│  ├─ models.py
│  ├─ serializers.py
│  ├─ views.py
│  └─ urls.py
├─ posts/
│  ├─ models.py
│  ├─ serializers.py
│  ├─ views.py
│  └─ urls.py
└─ manage.py
```

---

## **Setup & Installation**

1. **Clone the repository**

```bash
git clone <YOUR_REPO_URL>
cd social_api
```

2. **Create a virtual environment and activate**

```bash
python -m venv venv
source venv/bin/activate   # Linux/macOS
venv\Scripts\activate      # Windows
```

3. **Install dependencies**

```bash
pip install -r requirements.txt
```

4. **Apply migrations**

```bash
python manage.py makemigrations
python manage.py migrate
```

5. **Create a superuser**

```bash
python manage.py createsuperuser
```

6. **Run the server**

```bash
python manage.py runserver
```

---

## **API Endpoints**

### **Authentication**

* `POST /api/token/` → Obtain JWT token
* `POST /api/token/refresh/` → Refresh JWT token

### **Users**

* `POST /api/users/register/` → Register new user
* `GET /api/users/<id>/` → Get user details
* `PUT /api/users/<id>/` → Update user profile
* `DELETE /api/users/<id>/` → Delete user profile
* `POST /api/users/follow/` → Follow a user
* `DELETE /api/users/unfollow/<username>/` → Unfollow a user

### **Posts**

* `GET /api/posts/` → List all posts
* `POST /api/posts/` → Create a new post
* `GET /api/posts/<id>/` → Retrieve a single post
* `PUT /api/posts/<id>/` → Update a post (own posts only)
* `DELETE /api/posts/<id>/` → Delete a post (own posts only)
* `GET /api/posts/feed/` → List posts from followed users (feed)

---

## **Authentication**

All protected endpoints require the JWT token in the request headers:

```
Authorization: Bearer <your_token_here>
```

---

## **Testing**

You can use **Postman** or **curl** to test API endpoints.
Example using curl:

```bash
# Register a user
curl -X POST http://127.0.0.1:8000/api/users/register/ \
-H "Content-Type: application/json" \
-d '{"username": "testuser", "email": "test@example.com", "password": "testpass"}'

# Get JWT token
curl -X POST http://127.0.0.1:8000/api/token/ \
-H "Content-Type: application/json" \
-d '{"username": "testuser", "password": "testpass"}'
```

---

## **Next Steps**

* Implement likes and comments
* Add media uploads to cloud storage (e.g., AWS S3)
* Implement notifications and messaging
* Deploy API on Heroku or PythonAnywhere

---

## **License**

This project is for educational purposes and does not have a commercial license.

---

**Author:** Tyrone Kedidimetse
**Project:** Capstone Social Media API
