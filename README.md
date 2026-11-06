# FinTrack

FinTrack is a Django web application for keeping everyday finance records and summaries in one place. Record expenses, savings, investments, loans, and insurance policies; review EMI estimates, recurring payments, budget alerts, and analytics from the dashboard.

## What you can do

### Track spending and plan a budget

- Add expenses, assign categories such as food, transport, bills, entertainment, EMI, or other, and edit or remove records.
- Set up recurring expenses and bills with weekly or monthly schedules and a payment day.
- View spending summaries and category breakdowns on the dashboard and analytics page.
- Compare needs, wants, and savings against a 50/30/20 budget guideline and review budget alerts.

### Manage savings, investments, loans, and policies

- Record savings and investment contributions.
- Categorize investments (including stocks, mutual funds, gold, fixed deposits, real estate, and crypto) and track quantity, invested amount, and current value.
- Set recurring savings or investment contributions.
- Store loan principal, annual interest rate, tenure, and start date; calculate estimated monthly EMI, total repayment, and interest.
- Record insurance policy type, sum assured, premium, and next premium due date.
- Review income and financial summaries alongside recent activity.

### Keep documents and find information

- Upload and browse documents in the document vault, with a PIN setup/unlock flow.
- Search financial records.
- Ask the built-in chatbot questions about the available financial summary.

### Optional integrations

The code includes mutual-fund NAV lookup, Experian integration scaffolding, and WhatsApp report/alert flows. These integrations are not all ready for production: some responses or portfolio entries are mock/demo data, and provider credentials or local setup may be required.

## Technology

- Python 3.12+
- Django
- SQLite for local development
- HTML, CSS, and JavaScript

## Run locally

### Prerequisites

Install Python 3.12 or newer and Git.

### 1. Clone the repository

```bash
git clone https://github.com/aniketshirude/FinTrack.git
cd FinTrack/EMIProject
```

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

macOS or Linux:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

There is currently no `requirements.txt` in the repository. Install the packages used by the app:

```bash
python -m pip install Django requests python-dateutil
```

To try the optional WhatsApp flow, install its additional package:

```bash
python -m pip install pywhatkit
```

### 4. Set up the database and account

```bash
python manage.py migrate
python manage.py createsuperuser
```

Alternatively, open `/register/` after starting the server to use the app's registration page.

### 5. Start the development server

```bash
python manage.py runserver
```

Visit [http://127.0.0.1:8000/](http://127.0.0.1:8000/) and sign in.

## Configuration

For local development, the app uses SQLite and generates a temporary Django secret key when `DJANGO_SECRET_KEY` is not set. For deployments, set a strong secret key and disable debug mode:

```text
DJANGO_DEBUG=False
DJANGO_SECRET_KEY=<your-secret-key>
```

Optional chatbot and Experian settings are read from environment variables:

```text
GOOGLE_API_KEY=<your-google-api-key>
OPENAI_API_KEY=<your-openai-api-key>
EXPERIAN_API_KEY=<your-experian-api-key>
EXPERIAN_BASE_URL=<your-experian-api-base-url>
```

Never commit real credentials, personal financial records, the local database, or uploaded documents.

## Run tests

From the `EMIProject` directory:

```bash
python manage.py test
```

## Project structure

```text
EMIProject/
├── accounts/       # Registration and profile functionality
├── config/         # Django settings and URL configuration
├── core/           # Dashboard, financial records, analytics, and integrations
├── expenses/       # Expense and recurring expense features
├── static/         # CSS, JavaScript, and image assets
└── templates/      # Django HTML templates
```

## Important notes

- The repository excludes the local SQLite database, uploaded media, and generated files. Run migrations to create a fresh local database.
- Before using real financial data or allowing multiple accounts, review the data model and access controls: not all financial record models are explicitly associated with an individual account.
- This project is intended for development and learning. Before deployment, configure production-grade secrets, `ALLOWED_HOSTS`, database and media storage, HTTPS, and any required integration credentials; review Django's deployment checklist.
