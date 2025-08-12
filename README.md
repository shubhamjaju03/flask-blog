# Flask Blog Application

## Overview

A clean and user-friendly blog web application built with **Flask**. It supports user authentication, admin-protected blog post management, rich text content editing, and commenting. The backend uses **PostgreSQL** and is optimized for deployment on **Render.com**.

## Live Site

You can visit the live deployed application here: [https://shubham-flask-blog.onrender.com/](https://shubham-flask-blog.onrender.com/)

## Features

- User registration and secure login with hashed passwords (PBKDF2 SHA-256)
- Admin-only access to create, edit, and delete blog posts
- Rich text editing for blog content via CKEditor integration
- Commenting system for authenticated users
- User avatars via Gravatar
- Responsive interface powered by Bootstrap 5
- Easy switch between SQLite (local dev) and PostgreSQL (production)
- Secure environment variable management for secrets and database URLs

## Technology Stack

- **Python 3.12**
- **Flask 2.2.x** framework
- **Flask-Login** for user session management
- **Flask-WTF & WTForms** for forms and validation
- **Flask-CKEditor** for rich text editing
- **Flask-Bootstrap 5** for responsive UI
- **SQLAlchemy ORM** with PostgreSQL (psycopg driver)
- **Render.com** for cloud hosting and managed PostgreSQL
- **Gunicorn** as the production WSGI server

## Installation and Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/shubhamjaju03/flask-blog.git
   cd flask-blog
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate    # Windows: venv\Scripts\activate
   ```

3. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Set up environment variables:
   - `SECRET_KEY` for Flask session security
   - `DB_URI` for PostgreSQL connection string (use internal Render URL when deployed)

5. Initialize the database schema:
   ```bash
   flask shell
   >>> from main import db
   >>> db.create_all()
   >>> exit()
   ```

6. Run the app locally:
   ```bash
   flask run
   ```

## Deployment Guidelines

- Provision a PostgreSQL instance on Render.
- Supply `DB_URI` with the internal database URL for low latency.
- Set the Flask `SECRET_KEY` securely in Render environment variables.
- Deploy the app with Gunicorn.
- Monitor logs and environment variables via the Render dashboard.

## Usage

- Register and login users.
- Admin user (default user ID 1) can manage blog posts.
- Authenticated users can comment on posts.
- Blog posts support title, subtitle, image URL, and formatted content.
- Comments display user avatars using Gravatar.

## Project Structure

- `main.py` — primary Flask app and route definitions
- `forms.py` — form classes using Flask-WTF
- `templates/` — Jinja2 templates for rendering HTML
- `static/` — stylesheets, images, and JavaScript assets
- `requirements.txt` — pinned Python dependencies

## Notes

- Admin restriction is based on user ID 1 by default; customize as necessary.
- Passwords are securely hashed with salt and multiple iterations.
- The app gracefully supports local SQLite and PostgreSQL backends.
- Use Render’s internal Postgres URL for best performance and security.

## License

This project is licensed under the MIT License.

***
