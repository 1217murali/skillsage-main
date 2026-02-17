# Project Setup Guide (SkillSage AI)

This guide will help you set up and run the SkillSage AI project on a new machine (e.g., your friend's laptop).

## Prerequisites

Before starting, ensure you have the following installed on your system:

1.  **Node.js & npm** (for the frontend): [Download Node.js](https://nodejs.org/) (LTS version recommended).
2.  **Python** (for the backend): [Download Python](https://www.python.org/downloads/) (Version 3.10 or higher recommended).
3.  **Git**: [Download Git](https://git-scm.com/downloads).

---

## 1. Get the Code

### Option A: Clone with Git (Recommended)

Open a terminal and run:

```bash
git clone <YOUR_REPOSITORY_URL>
cd skillsage-main
```

### Option B: Download via Zip / USB

1.  **Extract the Zip file** to a folder on your computer (e.g., `Desktop` or `Documents`).
2.  Open that folder in VS Code or your terminal.
3.  **Important:** Ensure you **delete** the following folders if they exist (they might cause issues):
    -   `node_modules` (in `project/`)
    -   `venv` (in `backend/`)
    -   `__pycache__` folders (inside `backend/` subdirectories)


---

## 2. Backend Setup (Django)

Navigate to the `backend` folder:

```bash
cd backend
```

### a. Create a Virtual Environment

It is recommended to use a virtual environment to manage dependencies isolated from your system.

**Windows:**
```bash
python -m venv venv
.\venv\Scripts\activate
```

**Mac/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

*(You should see `(venv)` appear at the beginning of your terminal prompt).*

### b. Install Dependencies

Install the required Python packages:

```bash
pip install -r requirements.txt
```

### c. Environment Variables

Create a file named `.env` in the `backend` directory (parallel to `manage.py`) if it doesn't already exist.
Add your API keys (ask the project owner for these or generate new ones):

```env
OPENROUTER_API_KEY=your_openrouter_api_key_here
GEMINI_API_KEY=your_gemini_api_key_here
```

### d. Database Migration

Set up the database:

```bash
python manage.py migrate
```

### e. Run the Backend Server

Start the Django development server:

```bash
python manage.py runserver
```

The backend should now be running at `http://127.0.0.1:8000/`.

---

## 3. Frontend Setup (React + Vite)

Open a **new** terminal window (keep the backend terminal running). Navigate to the `project` folder:

```bash
cd project
```

### a. Install Dependencies

Install the required Node packages:

```bash
npm install
```

### b. Run the Frontend Server

Start the React development server:

```bash
npm run dev
```

The frontend should now be running (usually at `http://localhost:5173/`).

---

## 4. Verify Setup

1.  Open your browser and search for `http://localhost:5173/`.
2.  Try logging in or navigating to the main dashboard.
3.  Test a feature that requires the backend (e.g., the AI chat or Interview session).

## Troubleshooting

-   **"Module not found" errors:** Make sure you ran `pip install -r requirements.txt` (backend) or `npm install` (frontend) successfully.
-   **Database errors:** Ensure you ran `python manage.py migrate`.
-   **API Key errors:** specific features like the AI chat might fail if the `.env` file is missing or has invalid keys.
-   **Command not found:** Ensure Python and Node.js are added to your system's PATH.
