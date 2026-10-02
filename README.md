# Grok Resume Optimizer Bot 🚀

**AI-powered Resume Optimization, Skill Gap Analysis, Study Roadmaps & Mock Interview Simulator**

Built to help job seekers tailor resumes for ATS, close skill gaps with personalized learning paths, and practice interviews with real-time feedback.

## Features

### 1. Resume Optimization
- Parse resume text (skills, achievements, experience)
- Identify ATS-friendly keywords from Job Descriptions
- Suggest quantified achievements aligned with JD

### 2. JD Analysis
- Extract **mandatory** vs **preferred** vs **nice-to-have** skills
- Compute match score & detailed gap analysis
- Highlight strengths and missing skills

### 3. Preparation Guidelines & Resource Recommender
- Generate personalized **study roadmaps** for each skill gap
- Curated resources: official docs, blogs, GitHub repos, YouTube tutorials
- Practice tasks for hands-on learning

### 4. Skill Tracking
- Persistent skill profile (SQLite)
- Track proficiency levels and progress over time
- Dynamic gap highlighting against any JD

### 5. Mock Interview Simulation
- Technical, behavioral, scenario-based, and system design questions
- Tailored to your resume + target role
- Instant feedback on **clarity, depth, and confidence**
- STAR-method friendly evaluation

## Architecture

```
Frontend: Streamlit Chat Interface (web)
Backend:
  ├── LLM-ready modules (plug in OpenAI / xAI / local)
  ├── Resume Parser
  ├── JD Analyzer
  ├── Resource Recommender (curated + extensible RAG)
  ├── Skill Tracker (SQLite)
  └── Interview Simulator
```

Future extensions planned:
- RAG pipeline for fresh YouTube/docs
- Teams / Slack / WhatsApp bots
- Full LLM integration for advanced extraction & generation
- Vector DB for skill embeddings

## Quick Start

### 1. Clone & Install
```bash
git clone https://github.com/manignadark/grok-resume-optimizer-bot.git
cd grok-resume-optimizer-bot
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

### 2. Run the App
```bash
streamlit run app.py
```

Open http://localhost:8501

### 3. Usage Flow
1. Paste your **Resume** in the expander or sidebar
2. Paste a **Job Description**
3. Click **Analyze Gaps** or type "analyze gaps"
4. Generate **Study Roadmaps** for missing skills
5. Start a **Mock Interview** and answer questions
6. Receive scored feedback

## Project Structure
```
grok-resume-optimizer-bot/
├── app.py                          # Streamlit main app
├── requirements.txt
├── README.md
├── backend/
│   ├── modules/
│   │   ├── resume_parser.py
│   │   ├── jd_analyzer.py
│   │   ├── resource_recommender.py
│   │   ├── skill_tracker.py
│   │   └── interview_simulator.py
│   └── __init__.py
├── data/                           # SQLite DB (auto-created)
└── docs/
```

## Extending with Real LLM
The modules accept an optional `llm_client`. You can plug in:
- OpenAI / Azure OpenAI
- xAI Grok API
- Local models via Ollama / LM Studio

Example:
```python
from openai import OpenAI
client = OpenAI(api_key="...")
parser = ResumeParser(llm_client=client)
```

## Roadmap
- [ ] Full LLM structured extraction (JSON mode)
- [ ] RAG over documentation + YouTube transcripts
- [ ] PDF / DOCX resume upload + parsing
- [ ] Export optimized resume (ATS-friendly PDF/DOCX)
- [ ] Multi-user auth
- [ ] Slack / Teams / WhatsApp connectors
- [ ] Progress dashboard & analytics

## Contributing
PRs welcome! Focus areas: better question banks, more curated resources, LLM prompt engineering, frontend polish.

## License
MIT

---
Built with ❤️ using Grok capabilities for job seekers everywhere.
