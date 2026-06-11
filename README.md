# Solanna: A Multimodal Event-Aware Hybrid Framework for Stock Price Prediction

> [!WARNING]
> **Research, Education, and Controlled Demonstration Only**
> This project is for research, education, and controlled demonstration only. It does not provide financial advice, and it is not an investment recommendation system. Predictions and estimates are directional research indicators only and may be inaccurate. Do not rely on this system for trading or investment decisions. Public/commercial release requires separate legal, financial, security, and data-source review.

**Research Integrity Note:** This is a research prototype with a source-verified evaluation dataset and empirical ablation artifacts. Outputs are prediction estimates and research signals that must not be used as financial advice or trading instructions. Passing research gates does not approve market use or public decision guidance.

---

## 📖 Citation

If you use this software or the associated research, please cite:

```bibtex
@inproceedings{truong2025multimodal,
  title={A Multimodal Event-Aware Hybrid Framework for Stock Price Prediction Using Technical Signals and News Impact Analysis},
  author={Truong, Tan Dat},
  booktitle={Lecture Notes in Computer Science (LNCS/LNAI)},
  year={2025},
  publisher={Springer Nature},
  organization={University of Information Technology, Vietnam National University Ho Chi Minh City},
  doi={},
  url={https://github.com/ordinarytroung/solanna}
}
```

**Citation formats:**
- **APA**: Truong, T. T. D. (2025). *A Multimodal Event-Aware Hybrid Framework for Stock Price Prediction Using Technical Signals and News Impact Analysis*. Lecture Notes in Computer Science. Springer Nature.
- **IEEE**: T. T. D. Truong, "A Multimodal Event-Aware Hybrid Framework for Stock Price Prediction Using Technical Signals and News Impact Analysis," in *Lecture Notes in Computer Science*, Springer Nature, 2025.

**Citation file**: [CITATION.cff](CITATION.cff) (machine-readable)

---

## 📄 License

This project is dual-licensed:

- **Paper/Documentation**: [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE)
- **Source Code**: [MIT License](LICENSE)

See [LICENSE](LICENSE) for full terms.

---

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines on:

- Code of Conduct ([CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md))
- Development setup and workflow
- Branch strategy and commit conventions
- Pull request process
- Paper-specific guidelines (LaTeX, figures, bibliography)
- Code standards (Python, TypeScript, LaTeX)

### Quick Contribution Checklist

- [ ] Read [CONTRIBUTING.md](CONTRIBUTING.md)
- [ ] Sign off on [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)
- [ ] Follow [conventional commits](https://www.conventionalcommits.org/)
- [ ] All tests pass (CI)
- [ ] Paper compiles (0 errors) if modifying `paper/`

---

## 📊 Data Availability & Reproducibility

### Data Availability Statement

The evaluation dataset consists of:
- **985 unique Vietnamese news URLs** from VnExpress, CafeF, and Vietstock (2021-2025)
- **20,885 event-return rows** across 27 VN30 tickers
- **Chronological split**: Training (70%), Validation (10%), Test (20%)
- **ArchiveBox provenance**: 984/985 URLs archived (1 pending human review)

**Data access**: The curated dataset (metadata + extracted features) is available upon reasonable request for academic research purposes. Original article text is subject to respective publishers' Terms of Service.

### Reproducibility

All experiments are reproducible from this repository:

| Aspect | Details |
|--------|---------|
| **Repository** | `https://github.com/ordinarytroung/solanna` |
| **Commit** | `080691a9aae689f0ad6132ad56f5040c26a8238c` |
| **Random Seeds** | PyTorch/NumPy: 1000; scikit-learn/XGBoost: 42 |
| **Software** | Python 3.11.9, PyTorch 2.3.1, scikit-learn 1.5.0, XGBoost 2.1.1, LightGBM 4.4.0, Transformers 4.41.0, Optuna 3.6.1 |
| **Hardware** | Intel i7-12700K, 32GB RAM, RTX 3080 10GB (CUDA 12.1) |
| **Determinism** | `torch.use_deterministic_algorithms(True)`, `cudnn.deterministic=True` |

**Full dependencies**: `backend/requirements-research.txt` (locked versions)

### Artifacts

| Artifact | Location | Description |
|----------|----------|-------------|
| Dataset | `backend/app/models/data_quality_report.csv` | SHA256: `fd56c3be...` |
| Split manifest | `backend/app/models/chronological_split.json` | SHA256: `15f1d659...` |
| Model checkpoint | `backend/app/models/prediction_model.pkl` | SHA256: `36b5ab94...` |
| Paper manuscript | `paper/main.tex` | Springer LNCS format |
| Supplementary | `paper/supplementary.tex` | Supplementary material |

---

## 📚 Citation & Bibliography

### Key References

| # | Citation |
|---|----------|
| [1] | Fama, E.F. (1970). "Efficient Capital Markets: A Review of Theory and Empirical Work." *J. Finance* |
| [2] | Devlin et al. (2019). "BERT: Pre-training of Deep Bidirectional Transformers." NAACL-HLT |
| [3] | Nguyen & Nguyen (2020). "PhoBERT: Pre-trained Language Models for Vietnamese." EMNLP |
| [4] | Hamilton (1989). "Regime Switching in Time Series." *Econometrica* |
| [5] | Lei et al. (2018). "Distribution-free Predictive Inference." JASA |

Full bibliography: [`paper/references.bib`](paper/references.bib) (31 entries)

---

## ⚠️ Research Ethics & Disclaimer

> **⚠️ IMPORTANT**: This is a **research prototype** for academic purposes only.
>
> - **Not financial advice**: Outputs are research signals, not investment recommendations
> - **Not production-ready**: Not audited for trading, compliance, or regulatory use
> - **No trading claims**: No backtested returns, Sharpe ratios, or profit guarantees
> - **Research integrity**: All results reported with appropriate caveats and limitations
> - **Human oversight required**: All outputs require human expert review before any action

### Research Scope Boundaries

| In Scope | Out of Scope |
|----------|--------------|
| Methodology research | Live trading deployment |
| Prototype evaluation | Investment advice |
| Ablation studies | Regulatory compliance |
| Uncertainty quantification | Production trading systems |
| Reproducibility artifacts | Financial licensing |

---

## 🏗️ Architecture & Technologies

| Layer | Technology |
|-------|------------|
| **Frontend** | React 18, TypeScript, Vite, Tailwind CSS, Recharts |
| **State Management** | TanStack React Query |
| **Routing** | React Router v6 |
| **Authentication** | Clerk |
| **Backend** | FastAPI (Python), scikit-learn, yfinance |
| **ML** | LightGBM, XGBoost, PyTorch, Transformers (PhoBERT) |
| **Database** | TimescaleDB (TimescaleDB), Redis |
| **Queue** | Celery |
| **Paper** | LaTeX (Springer `llncs.cls`), BibTeX |

---

## 🚀 Quick Start

### Prerequisites

- Python 3.11+
- Node.js 18+
- Docker & Docker Compose
- LaTeX (TeX Live / MiKTeX) for paper compilation

### Installation

```bash
# Clone
git clone https://github.com/ordinarytroung/solanna.git
cd solanna

# Frontend
npm install
npm run dev

# Backend
cd backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt -r requirements-research.txt
uvicorn app.main:app --reload --port 8000

# Paper (LaTeX)
cd paper
pdflatex main.tex && bibtex main && pdflatex main.tex && pdflatex main.tex
```

### Docker (Full Stack)

```bash
docker compose up --build
# Frontend: http://localhost:8080
# Backend API: http://localhost:8000
```

---

## 📁 Repository Structure

```
solanna/
├── .github/workflows/ci.yml    # CI/CD pipeline
├── paper/                       # Springer LNCS manuscript
│   ├── main.tex                 # Main manuscript
│   ├── references.bib           # Bibliography
│   ├── figures/                 # 8 PDF figures
│   └── supplementary.tex        # Supplementary material
├── backend/                     # FastAPI backend
├── src/                         # React frontend
├── docs/                        # Documentation
│   ├── drafts/                  # Agent/collaborator drafts
│   ├── research/                # Research notes
│   └── agent_tasks/             # Agent task definitions
├── CITATION.cff                 # Citation metadata
├── LICENSE                      # CC-BY-4.0 / MIT
├── CONTRIBUTING.md              # Contribution guidelines
├── CODE_OF_CONDUCT.md           # Code of conduct
└── README.md                    # This file
```

---

## 📞 Contact

- **Author**: Truong Tan Dat
- **Affiliation**: University of Information Technology, VNU-HCM
- **Email**: datttruong.uit@gmail.com
- **Repository**: https://github.com/ordinarytroung/solanna

---

## 🏷️ Badges

![License](https://img.shields.io/badge/license-CC--BY--4.0%20%7C%20MIT-blue)
![Paper](https://img.shields.io/badge/paper-Springer%20LNCS-green)
![Build](https://img.shields.io/badge/build-passing-brightgreen)
![Python](https://img.shields.io/badge/python-3.11+-blue)
![Node](https://img.shields.io/badge/node-18+-green)

---

*Last updated: 2025-06-10 | Version 1.0.0*