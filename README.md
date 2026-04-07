# House Worker Hiring Platform 🏠🛠️

A modern, professional Django-based platform for hiring house workers. This project is fully production-ready with automated CI/CD and cloud deployment.

---

## 🚀 Features
- **Worker Registration**: Detailed profiles with Image support (via Pillow).
- **Hiring System**: Easy listing and worker management.
- **Production-Ready**: Secure configuration for the cloud.
- **Automated CI/CD**: Tests and deploys on every push.

---

## 💻 Local Setup & Development

### 1. Clone the Repository
```bash
git clone https://github.com/RadhaTawar/house-worker-platform.git
cd "House Worker Hiring Platform"
```

### 2. Create Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux/Mac
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Run Migrations & Start Server
```bash
python manage.py migrate
python manage.py runserver
```

---

## ☁️ Deployment Architecture

This project is configured for **Render** using a "Infrastructure-as-Code" approach.

### Key Production Files:
- **`render.yaml`**: The Blueprint file that automates the creation of the Web Service and PostgreSQL database.
- **`build.sh`**: A custom build script that handles static file collection and migrations automatically.
- **`Procfile`**: Defines the production server command using `Gunicorn`.
- **`runtime.txt`**: Specifies the Python version for the cloud environment.

---

## ⚡ GitHub Actions (CI/CD)

The project includes a fully automated pipeline in `.github/workflows/deploy.yml`:

1.  **Test Job**: Every `push` to `main` triggers a series of checks:
    - **Django Check**: Ensures no configuration errors.
    - **Migration Check**: Verifies database integrity.
    - **Unit Tests**: Runs all developed test cases.
2.  **Deploy Job**: If all tests pass, it "pings" Render to start a new deployment automatically.

---

## 🚀 How to Deploy This to Render

Want to deploy your own version? Here’s how:

1.  **Push to GitHub**: Push this code to your own repository.
2.  **Connect to Render**:
    - Go to [Render Dashboard](https://dashboard.render.com).
    - Click **"New +"** → **"Blueprint"**.
    - Connect your GitHub repository.
    - Name your blueprint (e.g., `house-worker-platform`).
    - Click **"Apply"**.
3.  **Automate Deployment (GitHub Secret)**:
    - On Render: Copy the **"Deploy Hook URL"** from your Web Service settings.
    - On GitHub: Go to **Settings** → **Secrets** → **Actions**.
    - Add a secret named `RENDER_DEPLOY_HOOK_URL` with that URL.

---

## 🛠️ Built With
- **Django 4.2**
- **PostgreSQL** (Production) / **SQLite** (Development)
- **Bootstrap 5** & **Crispy Forms**
- **WhiteNoise** (Static File Serving)
- **Cloud Hosting**: [Render](https://render.com)
