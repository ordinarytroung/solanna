# Solanna: Event-Aware Stock Prediction Prototype

> [!WARNING]
> **Research, Education, and Controlled Demonstration Only**  
> This project is for research, education, and controlled demonstration only. It does not provide financial advice, and it is not an investment recommendation system. Predictions and estimates are directional research indicators only and may be inaccurate. Do not rely on this system for trading or investment decisions. Public/commercial release requires separate legal, financial, security, and data-source review.

**Research Integrity Note:** This is a research prototype with a source-verified evaluation dataset and empirical ablation artifacts. Outputs are prediction estimates and research signals that must not be used as financial advice or trading instructions. Passing research gates does not approve market use or public decision guidance.

Solanna is a React and FastAPI-based research prototype with empirical evaluation. It provides interactive charts, historical data visualization, future price estimates, event-aware news analysis, source-verified benchmark tooling, and Springer-ready research artifacts for selected Vietnamese and US market workflows.

## Current Status & Scope Boundaries

- **Research-Only Prototype:** This system is built for time-series forecasting research and empirical evaluation. It does not provide financial advice, trading signals, or investment recommendations.
- **Evidence Status:**
  - *Source-Verified Candidate Evidence:* Programmatic checks (leakage guard, chronological split, temporal hashes) confirm that the evaluation dataset has temporal integrity.
  - *External-Human-Gated Evidence:* The double-blind human audit framework (reviewer A/B templates) is prepared, but pending independent execution and human signoff. No completed independent audit exists.
- **Mobile Support Status:** A responsive PWA web shell and Capacitor native wrappers (Android/iOS scaffolds) are included. The mobile shells wrap the responsive web bundle. Local Android/iOS SDK-dependent native builds are environment-gated, and native capabilities (push notifications, offline model caching, production app-store billing) are not implemented.
- **Commercial & Production Gaps:** Watchlist alerts, database administration tables, and commercial telemetry modules are sandbox placeholders or simulation wrappers. They are not audited or licensed for production use.
- **Springer LaTeX Package:** Located in [docs/research/springer_latex/](docs/research/springer_latex/).
- **Docker Compose Stack:** Local execution stack for frontend, backend, TimescaleDB, Redis, and Celery workers is provided for controlled research runtimes.

## 🚀 Features

- **Authentication via Clerk**: Secure user sign-up and login.
- **Interactive Dashboard**: A user-friendly interface for selecting tickers and analyzing market trends.
- **Historical Data Visualization**: Interactive 5-year historical price charts.
- **Research Forecasting**: Future price estimates accompanied by confidence and uncertainty context.
- **Personalized Watchlist**: Save and monitor preferred tickers per account.
- **Flexible Price Alerts**: Configure research alerts for when a stock price crosses a target threshold.
- **Predictive Confidence Intervals**: Generates low/high prediction ranges to support cautious analysis.
- **Research Signals**: Provides signal scores, directional probabilities, and risk thresholds for research purposes.
- **Multi-Algorithm Time-Series Forecasting**: Evaluates Linear Regression (lagged), ElasticNet (lagged), Random Forest (lagged), Gradient Boosting (lagged), XGBoost (lagged), and ARIMA.
- **Automated Backtesting & Model Selection**: Automatically calculates MAE, RMSE, and MAPE to select the best-performing model per ticker.
- **Multimodal Evaluation**: Features a model evaluation page comparing technical-only, news-only, and hybrid models.
- **Responsive Design**: Mobile-first architecture ensuring seamless operation across devices.
- **Source-Verified Pipeline**: VNDirect/vnstock/yfinance fallback ingestion, RSS news ingestion, manifest hashes, chronological split, and leakage guard.
- **Security Hardening**: Route-level auth dependencies, CORS allowlist headers, trusted-proxy rate limiting, and encrypted provider keys at rest.
- **Springer Package**: Generated LNCS-style LaTeX manuscript, BibTeX references, tables, and PDF figures.

## 🛠️ Technology Stack

- **Frontend**: React 18, TypeScript, Vite, Tailwind CSS, Recharts
- **State Management & Data Fetching**: TanStack React Query
- **Routing**: React Router v6
- **Authentication**: Clerk
- **Backend**: FastAPI (Python), scikit-learn, yfinance

## 📦 Setup & Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd solanna
   ```

2. **Install frontend dependencies**
   ```bash
   npm install
   ```

3. **Configure frontend environment variables**
   Copy the example environment file:
   ```bash
   cp .env.example .env.local
   ```
   *(On Windows PowerShell: `Copy-Item .env.example .env.local`)*

   Update `.env.local` with your Clerk publishable key without exposing secrets:
   ```env
   VITE_CLERK_PUBLISHABLE_KEY=pk_test_... # Get from Clerk Dashboard
   VITE_API_BASE_URL=http://localhost:8000/api
   VITE_ENABLE_MOCK_FALLBACK=false
   VITE_BENCHMARK_SOURCE=prod
   ```

4. **Configure backend environment variables**
   Navigate to the backend directory and copy the example environment file:
   ```bash
   cd backend
   cp .env.example .env
   ```
   *(On Windows PowerShell: `Copy-Item .env.example .env`)*

   Configure the backend environment:
   ```env
   APP_ENV=development
   AUTH_ENABLED=false
   # For production (APP_ENV=production), configure Clerk:
   # CLERK_ISSUER=https://<your-clerk-domain>
   # CLERK_JWKS_URL=https://<your-clerk-domain>/.well-known/jwks.json
   # AUTH_EXEMPT_PATH_PREFIXES=/api/metrics
   ```
   *Note: When `APP_ENV=production`, the backend requires a valid bearer token for all `/api/*` routes unless exempted.*

5. **Start the frontend development server**
   ```bash
   npm run dev
   ```

6. **Start the backend development server**
   Open a new terminal, navigate to the backend directory, and start FastAPI:
   ```bash
   cd backend
   # Ensure your python environment (.venv) is activated and dependencies are installed
   # pip install -r requirements.txt
   uvicorn app.main:app --reload --port 8000
   ```

## 🧪 Testing & Quality Assurance

The project includes a robust suite of tools to ensure code quality and research integrity.

- **Lint frontend**:
  ```bash
  npm run lint
  ```
- **Typecheck frontend**:
  ```bash
  npm run typecheck
  ```
- **Run frontend unit tests**:
  ```bash
  npm run test:frontend
  ```
- **Check UI terminology**:
  ```bash
  npm run check:ui-terms
  ```
- **Run full frontend quality suite**:
  ```bash
  npm run quality:frontend
  ```
- **Run backend unit tests**:
  ```bash
  npm run test:backend
  ```

## Quick Start With Docker Compose

```bash
docker compose config
docker compose up --build
```

Open the frontend at `http://localhost:8080` and the backend health check at `http://localhost:8000/health`. Stop the stack with:

```bash
docker compose down
```

## 📊 Evaluation & Research Artifacts

- **Model Evaluation Page**: Access `http://localhost:5173/evaluation` to review technical-only, news-only, and hybrid research benchmarks and diagnostics.
- **Research Scripts**: The project includes several PowerShell and Python scripts to train models, generate latex tables, evaluate statistical significance, and build data quality reports. See the `package.json` and backend `scripts/` directory for commands like `npm run research:matrix` and `npm run research:backtest`.

## Research Paper

The Springer-ready package is under `docs/research/springer_latex/`. Generate or refresh it with:

```bash
python backend/scripts/generate_springer_package.py --format latex
```

The source-verified evaluation artifacts are in `backend/app/models/news_only_baseline_metrics.json`, `backend/app/models/hybrid_fusion_metrics.json`, `backend/app/models/ablation_comparison.json`, and `backend/app/models/ablation_significance.json`.
