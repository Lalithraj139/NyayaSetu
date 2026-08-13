# ⚖️ NyayaSetu — AI-Powered Legal & Constitutional Awareness Assistant

NyayaSetu is an **AI-powered civic and legal-awareness platform** designed to help users understand their constitutional rights, relevant Indian laws, similar case examples, and possible legal remedies in simple language.

> **Disclaimer:** NyayaSetu is an educational and legal-awareness tool. It is **not a substitute for a qualified lawyer or professional legal advice**.

---

## 🚀 Overview

Understanding Indian laws and constitutional rights can be difficult because legal information is often complex and scattered across different sources.

**NyayaSetu** aims to bridge this gap by allowing users to describe a real-world situation in natural language and receive an easy-to-understand explanation of:

* 🇮🇳 Applicable constitutional rights
* ⚖️ Relevant Indian laws
* 📚 Similar case examples
* 🏛️ Relevant authorities or institutions
* 📝 Possible legal remedies and next steps
* 💡 Simplified explanations of legal concepts

The system is designed with an emphasis on **legal awareness, accessibility, and responsible AI usage**.

---

## ✨ Key Features

### 🧑‍⚖️ Constitutional Rights Analysis

Analyzes a user's situation and identifies potentially relevant constitutional rights.

### ⚖️ Indian Law Identification

Provides information about laws that may be relevant to the described situation.

### 📚 Case-Based Awareness

Helps users understand similar legal situations and important judicial decisions.

### 🏛️ Authority Identification

Identifies potentially relevant authorities, institutions, or departments that users may need to approach.

### 💡 Simple Legal Explanations

Converts complex legal concepts into easier-to-understand language.

### 📝 Remedy Awareness

Provides general information about possible courses of action without presenting itself as a legal advisor.

### 🤖 AI-Powered Reasoning

Uses an LLM to analyze natural-language descriptions and generate contextual responses.

### 🔐 Secure API Configuration

API credentials are loaded through **Streamlit Secrets** rather than being hard-coded into the source code.

---

## 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │       User           │
                    │  Describes Situation │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Streamlit Web UI   │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  AI Legal Analysis   │
                    │       Engine         │
                    └──────────┬───────────┘
                               │
             ┌─────────────────┼─────────────────┐
             │                 │                 │
             ▼                 ▼                 ▼
     ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
     │ Rights/Law   │  │ Case & Legal │  │  Authority/  │
     │  Analysis    │  │  Information │  │   Remedies   │
     └──────────────┘  └──────────────┘  └──────────────┘
             │                 │                 │
             └─────────────────┼─────────────────┘
                               ▼
                    ┌──────────────────────┐
                    │      LLM / Groq      │
                    │   Response Engine    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Simplified Response  │
                    │  & Awareness Steps   │
                    └──────────────────────┘
```

---

## 🧠 How It Works

### Step 1 — User Input

The user describes a real-life situation in natural language.

Example:

```text
My employer has not paid my salary for several months.
What rights and legal options may be available to me?
```

### Step 2 — Situation Analysis

The application analyzes the user's description and identifies the relevant legal domain.

Possible domains include:

* Employment
* Education
* Consumer
* Cybercrime
* Traffic
* Housing
* General constitutional rights

### Step 3 — Legal Reasoning

The system evaluates potentially relevant:

* Constitutional provisions
* Indian laws
* Legal concepts
* Authorities
* Previous cases
* Possible remedies

### Step 4 — AI Response Generation

The identified information is passed to the AI reasoning layer, which generates a simplified response.

### Step 5 — User-Friendly Output

The user receives a structured explanation containing relevant legal-awareness information and possible next steps.

---

## 🛠️ Technology Stack

| Technology             | Purpose                                 |
| ---------------------- | --------------------------------------- |
| Python                 | Core application logic                  |
| Streamlit              | Web application interface               |
| Groq API               | LLM inference                           |
| Large Language Model   | Natural-language analysis and reasoning |
| JSON / Structured Data | Legal information storage               |
| Git & GitHub           | Version control                         |
| Streamlit Cloud        | Deployment                              |

---

## 📂 Project Structure

```text
NyayaSetu/
│
├── indian_legal_ai.py
│
├── data/
│   ├── constitution.json
│   ├── laws.json
│   ├── cases.json
│   └── remedies.json
│
├── .streamlit/
│   └── secrets.toml
│
├── requirements.txt
│
├── README.md
│
└── .gitignore
```

> The exact structure may vary depending on the current implementation.

---

## 🔐 API Key Security

NyayaSetu does **not** store the Groq API key directly in the source code.

The application retrieves the key using Streamlit Secrets:

```python
try:
    GROQ_API_KEY = st.secrets["GROQ_API_KEY"]
except:
    GROQ_API_KEY = ""
```

For local development, create:

```text
.streamlit/secrets.toml
```

and add:

```toml
GROQ_API_KEY = "your_api_key_here"
```

Make sure the file is included in `.gitignore`:

```gitignore
.streamlit/secrets.toml
.env
__pycache__/
*.pyc
```

**Never commit API keys or other credentials to GitHub.**

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/Lalithraj139/NyayaSetu.git
```

### 2. Navigate to the project

```bash
cd NyayaSetu
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

### 4. Activate the virtual environment

Windows:

```bash
venv\Scripts\activate
```

Linux/macOS:

```bash
source venv/bin/activate
```

### 5. Install dependencies

```bash
pip install -r requirements.txt
```

### 6. Configure Streamlit Secrets

Create:

```text
.streamlit/secrets.toml
```

Add:

```toml
GROQ_API_KEY = "your_api_key_here"
```

### 7. Run the application

```bash
streamlit run indian_legal_ai.py
```

The application will open in your browser.

---

## 🌐 Deployment

NyayaSetu can be deployed using **Streamlit Community Cloud**.

Basic deployment process:

```text
GitHub Repository
        ↓
Streamlit Community Cloud
        ↓
Connect Repository
        ↓
Configure Secrets
        ↓
Deploy
```

Add the following secret in the Streamlit deployment settings:

```toml
GROQ_API_KEY = "your_api_key_here"
```

Do not place the API key inside the GitHub repository.

---

## 🎯 Project Objectives

The major objectives of NyayaSetu are:

1. Make legal information easier to understand.
2. Improve awareness of constitutional rights.
3. Help users identify potentially relevant laws.
4. Provide simplified explanations of legal concepts.
5. Help users discover possible authorities and remedies.
6. Demonstrate the application of AI to civic and legal awareness.
7. Promote responsible and accessible use of AI in the legal-information domain.

---

## 🔮 Future Enhancements

Potential future improvements include:

* [ ] Multi-agent legal reasoning architecture
* [ ] Retrieval-Augmented Generation (RAG)
* [ ] FAISS/Chroma-based legal document retrieval
* [ ] Larger verified Indian legal dataset
* [ ] Constitutional article search
* [ ] Advanced case-law retrieval
* [ ] Multilingual support including Kannada, Hindi, and other Indian languages
* [ ] Voice-based interaction
* [ ] Document/PDF analysis
* [ ] Citation and source verification
* [ ] Mobile application
* [ ] Improved hallucination detection
* [ ] Human/legal-expert review workflow
* [ ] Legal information update pipeline

---

## ⚠️ Legal & AI Disclaimer

NyayaSetu is developed for **educational, informational, and civic-awareness purposes only**.

The information generated by the system should not be considered:

* Legal advice
* A lawyer-client consultation
* A substitute for professional legal services
* A guarantee of a particular legal outcome

AI-generated information may contain errors or incomplete interpretations. Users should verify important legal information using authoritative sources and consult a qualified legal professional when appropriate.

---

## 🔒 Responsible AI

NyayaSetu is designed with responsible AI principles in mind:

* Avoid presenting AI output as definitive legal advice.
* Encourage verification of important information.
* Protect API credentials.
* Clearly communicate system limitations.
* Avoid guaranteeing legal outcomes.
* Use authoritative legal sources wherever possible.

---

## 👨‍💻 Author

**Lalith Raju**

Computer Science Engineer

GitHub:
https://github.com/Lalithraj139

---

## 📜 License

Add the appropriate license to this repository based on the project's ownership and the licenses of any third-party datasets, code, or legal resources used.

---

## ⭐ Support

If you find this project useful, consider giving the repository a ⭐ on GitHub.

**NyayaSetu — Bridging the gap between people and legal awareness through AI.**
