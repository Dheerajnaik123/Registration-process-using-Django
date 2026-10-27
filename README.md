# Django Registration System

A beginner-friendly Django project demonstrating user registration, login/logout, profile creation, profile image upload, password changes, and a user profile/about page.

## Features

- User registration with username, email, and password
- Password hashing using Django's built-in authentication system
- User profile linked to the Django `User` model
- Address and profile-picture upload
- Login and logout
- Login-protected profile/about page
- Change-password page
- Django admin interface
- SQLite database for local development

## Tech stack

- Python
- Django
- SQLite
- HTML and CSS
- Bootstrap static assets

## Project structure

```text
project8/
├── app/
│   ├── migrations/
│   ├── admin.py
│   ├── apps.py
│   ├── form.py
│   ├── models.py
│   ├── signals.py
│   ├── tests.py
│   └── views.py
├── project8/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
├── static/
├── template/
├── .env.example
├── .gitignore
├── manage.py
└── README.md
```

## Run locally

1. Install Python and Git.
2. Clone this repository and open the project folder (the folder containing `manage.py`).
3. Create and activate a virtual environment:

   **Windows PowerShell**
   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

4. Install Django and the image-field dependency:
   ```powershell
   python -m pip install django pillow
   ```

5. Configure environment variables as described below before running the app.
6. Create the local database tables:
   ```powershell
   python manage.py migrate
   ```

7. (Optional) Create an admin account:
   ```powershell
   python manage.py createsuperuser
   ```

8. Start the development server:
   ```powershell
   python manage.py runserver
   ```

9. Open these local routes:
   - Registration: `http://127.0.0.1:8000/register/`
   - Login: `http://127.0.0.1:8000/login/`
   - Home: `http://127.0.0.1:8000/home/`
   - Profile/about: `http://127.0.0.1:8000/about/`
   - Django admin: `http://127.0.0.1:8000/admin/`

## Email and secret configuration — important

**Never commit your real email address credentials, Gmail app password, Django secret key, or `.env` file to GitHub.** The original local settings included mail credentials directly in Python files. Before publishing, remove those hard-coded values from `project8/settings.py`, `app/signals.py`, and any other source files.

Recommended approach:

- Store private values in a local `.env` file (it is ignored by `.gitignore`).
- Read the values from environment variables in Django settings.
- Use `DEFAULT_FROM_EMAIL` in signal/view code instead of hard-coding a sender address.
- Do not commit `.env`; commit `.env.example` only, with placeholder values.
- If a real Gmail app password or other credential has ever been committed or shared, revoke it and create a replacement. Removing it from the latest file does not erase it from Git history.

This repository's current email configuration may need updating to use standard Django `EMAIL_HOST`, `EMAIL_PORT`, `EMAIL_HOST_USER`, `EMAIL_HOST_PASSWORD`, and `EMAIL_USE_TLS` settings before email delivery will work.

## Security notes

- `DEBUG = True` is suitable only for local development.
- Set a new secret key through an environment variable before deployment.
- Configure `ALLOWED_HOSTS` for the deployment environment.
- The included SQLite database and uploaded media are intentionally ignored; each developer creates their own local database and uploads.
- Do not use real user information or private profile images in a public repository.

## Current limitations

This is a learning project, not a production-ready authentication service. Review validation, error handling, password-change session handling, email configuration, and deployment security before using it with real users.
