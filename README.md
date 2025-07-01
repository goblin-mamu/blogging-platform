# 📝 Simple Blogging Platform - Django Backend

A backend for a blogging platform where users can write, edit, and delete blog posts. This Django-based system features user authentication, role-based permissions, and real-time post updates using WebSockets via Django Channels and Redis.

---

## 🚀 Features

- 🔐 User registration, login, and logout
- ✍️ Create, update, delete blog posts
- 📚 View all posts (with pagination)
- 🛡️ Role-based permissions (Admin, Author, Reader)
- ⚡ Real-time post updates using WebSockets (Django Channels + Redis)
- 🧵 Scalable architecture for production
- 📦 Support for PostgreSQL or MongoDB (via Djongo or custom driver)

---

## 🛠️ Tech Stack

- *Backend Framework*: Django
- *WebSocket Support*: Django Channels
- *Real-Time Layer*: Redis
- *Database*: PostgreSQL or MongoDB
- *Authentication*: Django Auth System + JWT (optional)

---

## 🧑‍💻 Project Structure

blogbackend/
├── blog/ # Blog app (models, views, urls)
├── users/ # User registration and roles
├── blogbackend/ # Project settings and routing
├── templates/ # HTML templates (optional)
├── static/ # Static files
├── manage.py
├── requirements.txt
└── README.md

yaml
Copy
Edit

---

## ⚙️ Installation

### Prerequisites

- Python 3.9+
- Redis server
- PostgreSQL or MongoDB
- Virtual environment (optional)

### Step-by-Step

```bash
# Clone the repository
git clone https://github.com/yourusername/blogbackend.git
cd blogbackend

# Create virtual environment and activate
python3 -m venv blogenv
source blogenv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Setup Redis server
sudo service redis-server start

# Migrate database
python manage.py migrate

# Create superuser
python manage.py createsuperuser

# Run server
python manage.py runserver
🌐 WebSocket Server (Daphne)
To enable real-time updates:

bash
Copy
Edit
# Install Daphne
pip install daphne

# Run using Daphne
daphne -b 0.0.0.0 -p 8001 blogbackend.asgi:application
For production, use systemd or supervisor to manage Daphne as a service.

🔌 Running Redis (Ubuntu)
bash
Copy
Edit
sudo apt update
sudo apt install redis-server
sudo systemctl enable redis-server.service
Ensure your settings.py includes:

python
Copy
Edit
CHANNEL_LAYERS = {
    "default": {
        "BACKEND": "channels_redis.core.RedisChannelLayer",
        "CONFIG": {
            "hosts": [("127.0.0.1", 6379)],
        },
    },
}
📫 API Endpoints (Sample)
Method	Endpoint	Description
POST	/api/login/	Login
POST	/api/register/	Register
GET	/api/posts/	List all posts
POST	/api/posts/create/	Create a new post
PUT	/api/posts/<id>/	Update post
DELETE	/api/posts/<id>/	Delete post

✅ To-Do
 Add JWT-based API authentication

 Add WebSocket front-end interface

 Add Markdown support for posts

 Unit and integration tests

📄 License
This project is licensed under the MIT License.

🤝 Contributing
Contributions are welcome! Please fork the repo and submit a pull request.

vbnet
Copy
Edit