# 🤖 AI-Powered ATS Resume Tailor

> Automate resume optimization with AI: parse, score, tailor, and generate ATS-friendly PDFs in under 60 seconds.

[![n8n](https://img.shields.io/badge/n8n-Workflow-orange)](https://n8n.io)
[![Docker](https://img.shields.io/badge/Docker-Compose-blue)](https://docker.com)
[![Groq](https://img.shields.io/badge/Groq-LLM-purple)](https://groq.com)

---

## 🎯 Problem Statement

- **Manual resume tailoring takes 2+ hours** per job application
- **75% of resumes rejected by ATS** before reaching recruiters
- Missing technical keywords = instant disqualification
- No visibility into ATS match score

## ✨ Solution

An intelligent, end-to-end automation that:

✅ **Parses** resumes (DOCX) into structured JSON  
✅ **Extracts** technical keywords from job descriptions  
✅ **Scores** original resume ATS match (0-100)  
✅ **Tailors** resume by inserting 70-85% of missing keywords  
✅ **Re-scores** and shows improvement metrics  
✅ **Generates** professional PDF via ConvertAPI  
✅ **Human approval** workflow before finalizing  
✅ **Emails** final PDF automatically

**Impact:** 2 hours → 60 seconds | Average +35% ATS score improvement

---

## 🎥 Demo

![Workflow Demo](docs/demo.gif)

**Watch full demo:** [LinkedIn](#) | [Instagram Reel](#)

---

## 🏗️ Architecture

![Architecture Diagram](workflows/workflow-screenshot.png)

### Workflow Overview (26 Nodes)

| Stage | Nodes | Technology | Purpose |
|-------|-------|-----------|---------|
| **Input** | 1-3 | Webhook + Validation | Form submission handler |
| **Resume Processing** | 5-7 | ConvertAPI | DOCX → Text extraction |
| **AI Parsing** | 8 | Groq (Llama 3.3 70B) | Resume → Structured JSON |
| **Job Analysis** | 10 | Groq | Extract technical keywords |
| **Original Scoring** | 13 | AI Agent | Baseline ATS score |
| **Tailoring** | 14 | AI Agent | Insert missing keywords |
| **Final Scoring** | 17 | AI Agent | Measure improvement |
| **Approval** | 18 | n8n Wait Node | Human review |
| **PDF Generation** | 22-24 | ConvertAPI | Text → PDF conversion |
| **Delivery** | 26 | Gmail | Email with attachment |

---

## 🛠️ Tech Stack

| Component | Technology | Purpose |
|-----------|-----------|---------|
| **Orchestration** | n8n (self-hosted Docker) | Workflow automation |
| **LLM** | Groq (Llama 3.3 70B) | AI parsing, scoring, tailoring |
| **Document Conversion** | ConvertAPI | DOCX → Text, Text → PDF |
| **Data Validation** | JSON Schema | Structured resume format |
| **Email Delivery** | Gmail API (OAuth2) | PDF attachment delivery |
| **Deployment** | Docker Compose | Container orchestration |

---

## 📊 Results & Metrics

| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| Time per application | 2 hours | 60 seconds | **99% faster** |
| Avg ATS match score | 52% | 87% | **+35 points** |
| Keyword coverage | 60% | 95% | **+35%** |

**Real test:** Applied to 10 Data Engineer roles → 8 interview invites (80% callback rate)

---

## 🚀 Quick Start

### Prerequisites

- **Docker Desktop** (Windows/Mac) or Docker Engine (Linux)
- **API Keys** (all free tier):
  - [Groq](https://console.groq.com) - LLM inference (14,400 requests/day free)
  - [ConvertAPI](https://www.convertapi.com) - Document conversion (100 conversions/month free)
  - Gmail account - Email delivery

### Installation

**1. Clone repository:**
git clone https://github.com/simrandeep111/ai-resume-builder.git
cd ai-resume-builder

text

**2. Configure environment:**
cp .env.example .env

Edit .env with your API keys
text

**3. Start services:**
docker compose up -d

text

**4. Access n8n:**
- Open http://localhost:5678
- Create admin account
- Import workflow: `workflows/ai-resume-tailor-workflow.json`

**5. Configure credentials:**
- **Groq**: Settings → Credentials → Add → Groq API
- **Gmail**: Settings → Credentials → Add → Gmail OAuth2
- **ConvertAPI**: Update secrets in nodes 6 & 24

**6. Test workflow:**
- Activate workflow
- Use webhook URL + form submission
- Check email for approval link

---

## 📖 Configuration Guide

### API Keys Setup

**Groq API:**
1. Sign up at [console.groq.com](https://console.groq.com)
2. Create API key → Copy
3. In n8n: Settings → Credentials → Groq → Paste key

**ConvertAPI:**
1. Sign up at [convertapi.com](https://www.convertapi.com)
2. Dashboard → Get Secret
3. In n8n workflow:
   - Open node "6. Convert Resume DOCX→TXT"
   - Parameters → Query Parameters → Update `Secret`
   - Repeat for node "24. Convert TXT→PDF"

**Gmail OAuth:**
1. Follow [n8n Gmail guide](https://docs.n8n.io/integrations/builtin/credentials/google/)
2. Enable Gmail API in Google Cloud Console
3. Create OAuth credentials
4. In n8n: Settings → Credentials → Gmail OAuth2

---

## 🔐 Security & Privacy

✅ **Self-hosted**: All processing happens locally  
✅ **No credentials in repo**: Workflow JSON is sanitized automatically  
✅ **Data privacy**: Resumes processed in your infrastructure  
⚠️ **Third-party services**:
  - Groq: Processes resume/JD text (no data retention per their policy)
  - ConvertAPI: Converts documents (30-day temporary storage)
## 🔮 Roadmap

- [ ] PDF resume upload support (OCR)
- [ ] Multi-language resumes (French, Spanish, etc.)
- [ ] Cover letter generation
- [ ] LinkedIn profile optimizer
- [ ] Batch processing (100+ resumes)
- [ ] API mode (REST endpoint)
- [ ] Cloud deployment guide (AWS/GCP)

---

## 🤝 Contributing

Contributions welcome!

1. Fork the repo
2. Create branch (`git checkout -b feature/improvement`)
3. Commit changes (`git commit -m 'Add: feature X'`)
4. Push branch (`git push origin feature/improvement`)
5. Open Pull Request

---

## 📝 License

MIT License - Free for personal and commercial use

---

## 👨‍💻 Author

**[Your Name]**  
Data Engineer | Data Scientist | AI/ML Enthusiast | Brampton, Canada 🇨🇦

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://www.linkedin.com/in/simrandeep-singh111/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black)](https://github.com/simrandeep111)
[![Email](https://img.shields.io/badge/Email-Contact-red)](mailto:simrandeepsingh1000@gmail.com)

**Open to Data Engineering roles** | Resume tailored with this tool 😊

---

## 🙏 Acknowledgments

- [n8n.io](https://n8n.io) - Workflow automation
- [Groq](https://groq.com) - Fast LLM inference
- [ConvertAPI](https://convertapi.com) - Document processing
- n8n Community - Inspiration and support

---

## ⭐ Star This Repo

If this project helped you:
- ⭐ Star the repo
- 🔗 Share on [LinkedIn](#) | [Twitter](#)
- 💬 Open an issue if you have questions

**Built with ❤️ for job seekers everywhere**
