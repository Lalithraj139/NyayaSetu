# ⚖️ NyayaSetu Pro — Indian Legal Intelligence Suite

**NyayaSetu Pro** is an AI-powered Indian legal-awareness application built with **Streamlit, Python, Groq API, and Llama 3.3**.

The application provides an interactive interface for exploring Indian legal concepts, analyzing uploaded legal documents, mapping legacy laws to the newer 2023 criminal-law framework, and generating basic legal-document drafts.

> ⚠️ **Disclaimer:** NyayaSetu Pro is an educational and legal-awareness tool. It does not provide professional legal advice and should not be used as a substitute for a qualified advocate or legal professional.

---

## 🚀 Features

### 💬 1. AI Legal Assistant

The Legal Assistant allows users to ask questions about Indian law using natural language.

The application supports two selectable legal frameworks:

* **BNS 2023**
* **IPC 1860**

When BNS mode is enabled, the AI is instructed to prioritize the Bharatiya Nyaya Sanhita, 2023.

When IPC mode is enabled, the AI is instructed to use the legacy Indian Penal Code, 1860.

### Example

```text
What is the punishment for cheating?
```

The application sends the question to the Groq-hosted Llama model and displays the generated response in the legal assistant interface.

---

## 📄 2. Legal PDF Document Analysis

Users can upload a PDF document through the sidebar.

NyayaSetu Pro:

1. Accepts a PDF file.
2. Extracts text using `pypdf`.
3. Stores the extracted text during the current Streamlit session.
4. Passes up to 15,000 characters of extracted content to the AI as document context.
5. Uses that context while answering legal questions.

### Supported format

```text
PDF
```

This feature can be useful for analyzing legal documents, notices, agreements, or other text-based PDF material.

> Note: The current implementation performs text extraction. Scanned/image-only PDFs may not produce useful text without an OCR layer.

---

## 🔄 3. IPC / CrPC / IEA Converter

NyayaSetu Pro provides a legacy-to-new-law mapping interface.

Users can select:

* IPC
* CrPC
* IEA

and enter a section number.

The AI is then asked to map the selected provision to the newer 2023 legal framework:

* **BNS** — Bharatiya Nyaya Sanhita
* **BNSS** — Bharatiya Nagarik Suraksha Sanhita
* **BSA** — Bharatiya Sakshya Adhiniyam

The generated response is requested to include:

* Section number
* Definition
* Key changes

### Example

```text
Code: IPC
Section: 420
```

The system then requests an AI-generated mapping to the newer legal framework.

> Important: The converter currently relies on the LLM's generated response rather than a verified legal-section mapping database. Important legal information should therefore be independently verified against authoritative sources.

---

## 📝 4. AI Legal Document Drafter

The Document Drafter provides an interface for generating basic legal-document drafts.

Supported document types include:

* Rental Agreement
* Affidavit
* Legal Notice
* Employment Contract

Users provide:

* Party 1 name
* Party 2 name
* Jurisdiction
* Key terms

The application sends the information to the AI model and generates a draft.

The generated document can then be downloaded as a `.txt` file.

---

## 🧠 AI Architecture

The current application uses an LLM-based architecture centered around the Groq API.

```text
                    ┌──────────────────────┐
                    │        User          │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Streamlit UI      │
                    └──────────┬───────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
       Legal Assistant    Law Converter    Document Drafter
              │                │                │
              └────────────────┼────────────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │    Groq API          │
                    │ OpenAI-Compatible API│
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Llama 3.3 70B        │
                    │ Versatile Model      │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ AI Generated Output  │
                    └──────────────────────┘
```

---

## 📄 PDF Processing Workflow

```text
Upload PDF
    │
    ▼
PdfReader
    │
    ▼
Extract text from pages
    │
    ▼
Limit context to 15,000 characters
    │
    ▼
Add document context to AI messages
    │
    ▼
Groq / Llama
    │
    ▼
Legal response
```

---

## 🛠️ Technology Stack

| Technology        | Purpose                  |
| ----------------- | ------------------------ |
| Python            | Application development  |
| Streamlit         | Web interface            |
| OpenAI Python SDK | API client               |
| Groq API          | LLM inference            |
| Llama 3.3 70B     | AI language model        |
| pypdf             | PDF text extraction      |
| HTML/CSS          | Custom Streamlit styling |
| Git               | Version control          |
| GitHub            | Source-code hosting      |

---

## 📦 Python Dependencies

The application requires the following main packages:

```text
streamlit
openai
pypdf
```

A `requirements.txt` file can contain:

```text
streamlit
openai
pypdf
```

---

## 📂 Project Structure

For the current implementation, the project can be organized as:

```text
NyayaSetu/
│
├── indian_legal_ai.py
├── requirements.txt
├── README.md
│
└── .streamlit/
    └── secrets.toml
```

The `secrets.toml` file should **never be committed to GitHub**.

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/Lalithraj139/NyayaSetu.git
```

### 2. Open the project directory

```bash
cd NyayaSetu
```

### 3. Create a virtual environment

Windows:

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

Linux/macOS:

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

---

## 🔐 API Configuration

NyayaSetu Pro uses the Groq API through the OpenAI-compatible client.

The application does **not** hard-code the API key.

It reads the key using Streamlit Secrets:

```python
GROQ_API_KEY = st.secrets["GROQ_API_KEY"]
```

### Local configuration

Create:

```text
.streamlit/secrets.toml
```

Add:

```toml
GROQ_API_KEY = "YOUR_GROQ_API_KEY"
```

### `.gitignore`

Make sure the following is ignored:

```gitignore
.streamlit/secrets.toml
.env
__pycache__/
*.pyc
venv/
```

**Never upload your API key to GitHub.**

---

## ▶️ Running the Application

After installing the dependencies and configuring the API key:

```bash
streamlit run indian_legal_ai.py
```

Streamlit will start the application locally and provide a browser URL.

---

## 🔧 Application Configuration

The application currently uses:

```python
MODEL_NAME = "llama-3.3-70b-versatile"
```

The Groq API is accessed using:

```python
client = openai.OpenAI(
    base_url="https://api.groq.com/openai/v1",
    api_key=GROQ_API_KEY
)
```

The model is called using the OpenAI-compatible chat-completions interface.

---

## 💾 Session Management

The application uses Streamlit's session state to maintain conversation history.

```python
if "chat_history" not in st.session_state:
    st.session_state.chat_history = []
```

Conversation messages are stored as:

```text
user
assistant
user
assistant
...
```

The **Clear Chat History** button removes the current conversation from the session.

---

## 🎨 User Interface

The application contains:

### Sidebar

* PDF document upload
* Legal framework toggle
* Current framework indicator
* Clear chat history button

### Main Interface

Three tabs:

```text
💬 Legal Assistant
🔄 IPC ⇄ BNS Converter
📝 Document Drafter
```

Custom CSS is also used to create styled legal-response cards and improve the overall interface.

---

## 🔄 Application Workflow

```text
                   START
                     │
                     ▼
             Streamlit Application
                     │
                     ▼
              Load API Secret
                     │
                     ▼
              Display Main UI
                     │
        ┌────────────┼────────────┐
        │            │            │
        ▼            ▼            ▼
      Chat       Converter      Drafter
        │            │            │
        └────────────┼────────────┘
                     │
                     ▼
                 Build Prompt
                     │
                     ▼
                 Groq API
                     │
                     ▼
              Llama 3.3 Model
                     │
                     ▼
              Generate Response
                     │
                     ▼
                Display Output
```

---

## 🛡️ Security

Security is an important part of the application.

The current implementation uses:

* Streamlit Secrets for API credentials
* No hard-coded API key in the source code
* `.gitignore` protection for local secrets
* Session-based chat history

### Recommended security practices

Do not commit:

```text
secrets.toml
.env
API keys
access tokens
passwords
private credentials
```

If an API key is accidentally committed to Git, revoke/rotate the key immediately and remove it from Git history.

---

## ⚠️ Current Limitations

The current implementation has several important limitations.

### 1. AI-generated legal information

The application relies on an LLM for its legal responses.

The model can potentially produce:

* Incorrect sections
* Outdated information
* Incomplete interpretations
* Hallucinated legal references

Therefore, generated information should be verified against authoritative legal sources.

### 2. No verified legal database

The current code does not contain a dedicated legal database or retrieval system.

The IPC/BNS/CrPC/BNSS/BSA converter currently asks the LLM to perform the mapping.

### 3. PDF extraction limitations

The application uses `pypdf` for text extraction.

Scanned PDFs or image-only documents may require OCR.

### 4. Context limitation

Only the first 15,000 characters of extracted PDF text are currently passed to the AI:

```python
document_context[:15000]
```

Large documents therefore aren't fully provided to the model.

### 5. Legal-document generation

Generated agreements, affidavits, notices, and contracts are drafts only and should be reviewed by an appropriately qualified legal professional before use.

---

## 🔮 Future Improvements

Potential improvements for future versions include:

* [ ] Retrieval-Augmented Generation (RAG)
* [ ] Verified Indian legal document database
* [ ] Constitutional article retrieval
* [ ] Official case-law retrieval
* [ ] Citation and source verification
* [ ] FAISS or vector-database integration
* [ ] OCR for scanned PDFs
* [ ] Better long-document processing
* [ ] Multi-agent legal reasoning
* [ ] Improved hallucination detection
* [ ] Multilingual support
* [ ] Voice-based legal queries
* [ ] PDF/document export for generated drafts
* [ ] User authentication
* [ ] Conversation persistence
* [ ] Legal information update pipeline

---

## 🎯 Project Objectives

NyayaSetu Pro aims to:

1. Make Indian legal concepts easier to understand.
2. Provide an accessible AI interface for legal awareness.
3. Help users explore the transition from legacy laws to the 2023 criminal-law framework.
4. Enable users to provide legal documents as contextual input.
5. Assist with preliminary legal-document drafting.
6. Demonstrate practical applications of LLM technology in the legal-awareness domain.
7. Encourage responsible and informed use of AI-generated legal information.

---

## ⚖️ Legal Disclaimer

NyayaSetu Pro is intended strictly for **educational, informational, and legal-awareness purposes**.

The application does not establish an advocate-client relationship and does not constitute professional legal advice.

AI-generated responses may contain inaccuracies or omissions. Users should verify important information using authoritative legal sources and consult a qualified legal professional for specific legal matters.

The generated legal documents are drafts and should be reviewed before being used for any legal or contractual purpose.

---

## 👨‍💻 Author

**Lalith Raju**

Computer Science Engineer

GitHub:
https://github.com/Lalithraj139

---

## ⭐ Project

**NyayaSetu Pro — Indian Legal Intelligence Suite**

Built with:

```text
Python
+
Streamlit
+
Groq API
+
Llama 3.3
+
pypdf
```

> **NyayaSetu Pro — Making Indian legal information more accessible through AI.**
