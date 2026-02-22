# Twelvemark Studio

**Tagline:** The Standard of Next

A clean, fully-responsive Django web application for Twelvemark Studio — featuring a bold black-and-white design with lime-green accent (#c8ff00), contact form with database storage, and a Django Admin panel for reviewing submissions.

---

## Project Structure

```
twelvemark/
├── twelvemark/               # Django project config
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── contact/                  # Main app
│   ├── templates/
│   │   └── contact/
│   │       └── index.html    # Full frontend template
│   ├── __init__.py
│   ├── admin.py              # Admin panel config
│   ├── forms.py              # Contact form with validation
│   ├── models.py             # ContactSubmission model
│   ├── urls.py
│   └── views.py              # index + contact_submit views
├── static/                   # Static files directory
├── manage.py
├── requirements.txt
└── README.md
```

---

## Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/twelvemark-studio.git
cd twelvemark-studio
```

### 2. Create and activate a virtual environment

```bash
python -m venv venv

# On macOS/Linux:
source venv/bin/activate

# On Windows:
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run database migrations

```bash
python manage.py migrate
```

### 5. Create a superuser (for Admin panel access)

```bash
python manage.py createsuperuser
```

### 6. Start the development server

```bash
python manage.py runserver
```

Visit **http://127.0.0.1:8000/** to view the site.  
Visit **http://127.0.0.1:8000/admin/** to manage contact submissions.

---

## Features

| Feature | Details |
|---|---|
| **Hero Section** | Full-viewport, animated headline with ticker |
| **About Section** | Studio overview paragraph |
| **Services Section** | 3 cards: Brand & Identity, Web Dev, Digital Strategy |
| **Contact Form** | Name, Email, Message — AJAX submit, stored in SQLite |
| **Admin Panel** | View, search, and filter all contact submissions |
| **Responsive** | Mobile-first grid layout — works on all screen sizes |
| **Theme** | Black & white + `#c8ff00` (lime) accent |
| **Validation** | Client-side (JS) + server-side (Django forms) |

---

## Project Approach

The frontend uses a single Django template (`index.html`) with embedded CSS and JavaScript — no build tools required. The contact form submits via AJAX using the Fetch API, with CSRF protection handled by Django's middleware. Submitted entries are stored in a `ContactSubmission` model (SQLite by default, swappable for PostgreSQL in production). The Django Admin panel is configured to display, search, and filter all submissions with read-only fields to prevent accidental edits.

---

## Production Notes

- Set `DEBUG = False` in `settings.py` before deploying
- Replace `SECRET_KEY` with a securely generated key (use `python -m django startproject` or a secrets manager)
- Configure `ALLOWED_HOSTS` with your actual domain
- For production, use PostgreSQL and serve static files via WhiteNoise or a CDN
