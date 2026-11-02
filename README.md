# AI data analyst

## Run it on your laptop

You need **Python 3.10+** and **Node.js 22.22+ or 24.15+** (Angular 22 requires one of these). Check with `python --version` and `node --version`.

### 1. Backend (Django), in terminal 1

**Windows (PowerShell)**
```powershell
cd backend
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
copy .env.example .env
python manage.py migrate
python manage.py seed_demo
python manage.py runserver
```

If PowerShell refuses to run `Activate.ps1`, run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` once, then try again.


### 2. Connect a real LLM

Out of the box it runs in **offline demo mode**: no key needed, but it can only answer the six sample questions. For the interview, connect a real model by editing `backend/.env` (all options are written out in `.env.example`), then restart the backend.

| Option | Cost | Needs internet | Setting |
|---|---|---|---|
| Google Gemini | Free tier | Yes | `LLM_PROVIDER=openai` + Gemini base URL |
| Ollama (local) | Free | No | `LLM_PROVIDER=openai` + `http://localhost:11434/v1` |
| OpenAI | Paid | Yes | `LLM_PROVIDER=openai` |
| Anthropic Claude | Paid | Yes | `LLM_PROVIDER=anthropic` |

Tip: set up a real provider **and** keep the demo mode as a backup. If the Wi-Fi fails, change `LLM_PROVIDER=demo` and restart.

---