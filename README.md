# QuestionCreator

A Flask-based web app that generates and serves quiz questions with a simple HTML interface. The repository includes data samples, Jupyter research notebooks, server routes, and Jinja2 templates for rendering interview questions.

## Technology Stack

- Backend: Flask
- Templates: Jinja2 (templates/)
- Frontend assets: Static files (CSS/JS under static/)
- Data/Content: CSV/JSON or text assets under data/ and research/ notebooks
- Packaging: setup.py for installation metadata
- Dependencies: requirements.txt for Python packages

## Installation & Setup

### Step 1: Clone the Repository
```bash
git clone https://github.com/TMTien31/QuestionCreator.git
cd QuestionCreator
```


### Step 2: Create Virtual Environment
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```


### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```


### Step 4: Configure Environment (Optional)
- If environment variables are needed (API keys or config flags), create a .env in the project root and export variables before running the app.
- Typical pattern:
```bash
# macOS/Linux
export FLASK_ENV=development
export FLASK_APP=app.py

# Windows (PowerShell)
$env:FLASK_ENV="development"
$env:FLASK_APP="app.py"
```


### Step 5: Prepare Data
- Place question source files in data/ as required by the app logic (e.g., JSON/CSV/TXT used by app.py).
- Research/ notebooks are available for experimentation or preprocessing, not required for runtime.

## Running the Application

### Start the Flask Server
```bash
python app.py
# or with Flask CLI if configured:
flask run --host=0.0.0.0 --port=8080
```


### Access the Application
- Open a browser at http://localhost:8080 or as configured in app.py.

## Project Structure

- app.py — Flask entry point and routes
- templates/ — Jinja2 templates for quiz UI and results pages
- static/ — CSS/JS assets for the frontend
- data/ — Source datasets or curated question/answer files
- research/ — Jupyter notebooks for prototyping/question generation research
- requirements.txt — Python dependencies used by the app
- setup.py — Packaging metadata (optional installable module)
- README.md — Project documentation


