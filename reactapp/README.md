📘 Fullstack Todo App — Django + React

A full-stack web application built with Django (backend API) and React (frontend UI).
This project demonstrates how to integrate a Django backend with a modern React frontend in one unified project structure.

🚀 Features
Frontend (React)

Built with Create React App

Component-based UI

Fetches data from Django API

Hot reload during development

Production build served by Django

Backend (Django)

REST-style endpoints

SQLite database

Todo model + views

Admin panel enabled

Serves React build files in production

📁 Project Structure
project-root/
│
├── fullstack/          # Django project settings
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   ├── asgi.py
│
├── todo/               # Django app (backend logic)
│   ├── models.py
│   ├── views.py
│   ├── admin.py
│   ├── migrations/
│
├── reactapp/           # React frontend
│   ├── src/
│   ├── public/
│   ├── build/          # Generated after 'npm run build'
│   ├── package.json
│
├── db.sqlite3          # Database
└── manage.py

🛠️ Installation & Setup
🧩 1. Clone the repository
git clone https://github.com/your-username/fullstack-todo.git
cd fullstack-todo

📌 2. Backend Setup (Django)
Create virtual environment:
python -m venv venv
source venv/bin/activate     # Mac/Linux
venv\Scripts\activate        # Windows

Install dependencies:
pip install -r requirements.txt

Run migrations:
python manage.py migrate

Start Django server:
python manage.py runserver


Django runs on:

http://127.0.0.1:8000/

🌐 3. Frontend Setup (React)

Navigate into the React folder:

cd reactapp


Install frontend packages:

npm install


Run React in development mode:

npm start


React runs on:

http://localhost:3000/

📦 Building the React App for Production

To serve the React app through Django, build it:

cd reactapp
npm run build


This generates:

reactapp/build/


Then ensure your Django settings.py includes:

TEMPLATES[0]['DIRS'] = [BASE_DIR / 'reactapp' / 'build']

STATICFILES_DIRS = [
    BASE_DIR / 'reactapp' / 'build' / 'static'
]


And your urls.py serves the React index:

from django.urls import path, re_path
from django.views.generic import TemplateView

urlpatterns = [
    path('admin/', admin.site.urls),
    re_path(r'^.*$', TemplateView.as_view(template_name='index.html')),
]


Now Django can serve your entire frontend.

🧪 Running Both Servers Together
Option 1 — Run React and Django separately (development)

React: npm start → localhost:3000

Django: python manage.py runserver → localhost:8000

Option 2 — Use Django to serve React build (production)

Build React: npm run build

Start Django: python manage.py runserver

Now everything works on:

http://127.0.0.1:8000/

🧰 Technologies Used
Frontend

React

JavaScript

JSX

CSS

Backend

Django

Python

SQLite

🤝 Contributing

Pull requests welcome!
If you’d like to improve or extend the app, feel free to fork the repo and submit a PR.

📄 License

This project is open-source and available under the MIT License.