# FinTrack

FinTrack is a Django personal finance tracker that brings everyday spending and financial records together in one dashboard. Track expenses, recurring payments, savings, investments, loans, EMIs, and insurance; review financial summaries and budget alerts; and keep documents organized in a PIN-protected vault.

## Features

- **Expense tracking:** Add, categorize, review, edit, and delete expenses.
- **Recurring transactions:** Manage recurring expenses, bills, savings, and investments.
- **Savings and investments:** Track savings and investment holdings by category, quantity, invested amount, and current value.
- **Loans and EMI planning:** Manage loans and calculate monthly EMIs, total repayments, and interest.
- **Insurance policies:** Record policy types, coverage, premiums, and upcoming premium dates.
- **Dashboard and analytics:** Review income, expenses, savings, investments, loans, and budget status.
- **Budget tools:** Compare spending with suggested budget targets and view alerts.
- **Document vault:** Upload and manage documents through a PIN-protected area.
- **Search and finance chatbot:** Search financial records and ask the built-in chatbot about the financial summary.
- **Optional integrations:** The code includes mutual-fund data lookup, Experian integration scaffolding, and WhatsApp reports and alerts. These require additional configuration; some integration data is mocked or intended for development.

## Technology

- Python
- Django
- SQLite for local development
- HTML, CSS, and JavaScript

## Run locally

### 1. Prerequisites

Install Python 3 and Git.

### 2. Clone the repository

```bash
git clone https://github.com/aniketshirude/FinTrack.git
cd FinTrack/EMIProject
```

### 3. Create and activate a virtual environment

```bash
python -m venv .venv
```

On Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

### 4. Install dependencies

The repository does not currently include a dependency lock or requirements file. Install the packages used by the app:

```bash
python -m pip install Django requests pywhatkit
```

### 5. Apply migrations and create an account

```bash
python manage.py migrate
python manage.py createsuperuser
```

### 6. Start the development server

```bash
python manage.py runserver
```

Open [http://127.0.0.1:8000/](http://127.0.0.1:8000/) in your browser and sign in.

## Configuration

For local development, the application uses SQLite and generates a temporary Django secret key if `DJANGO_SECRET_KEY` is not set.

For a non-debug environment, configure a strong secret key and set debug mode off before starting the application:

```text
DJANGO_DEBUG=False
DJANGO_SECRET_KEY=<your-secret-key>
```

The chatbot and external-service settings can be provided through environment variables when needed:

```text
GOOGLE_API_KEY=<your-google-api-key>
OPENAI_API_KEY=<your-openai-api-key>
EXPERIAN_API_KEY=<your-experian-api-key>
EXPERIAN_BASE_URL=<your-experian-api-base-url>
```

Do not commit real credentials, local databases, or personal documents to the repository. Optional integrations may require provider credentials, account setup, and additional production configuration.

## Run tests

From the `EMIProject` directory:

```bash
python manage.py test
```

## Repository layout

```text
EMIProject/
├── accounts/       # Account and profile functionality
├── config/         # Django project configuration
├── core/           # Finance features, dashboard, and integrations
├── expenses/       # Expense and recurring expense functionality
├── static/         # CSS, JavaScript, and image assets
└── templates/      # Django HTML templates
```

## Notes

- The repository intentionally excludes the local SQLite database, uploaded media, and generated files. A fresh setup creates its database by running migrations.
- This project is intended for learning and local development. Review Django's deployment checklist and configure production security, allowed hosts, database, static/media storage, and integration credentials before deploying.
