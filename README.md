# 🏥 SmartClaim AI

> **AI-Powered Insurance Claims Processing & Verification System**

SmartClaim AI is an intelligent insurance claim verification system that analyzes medical insurance claims and automatically determines whether a claim should be **Accepted ✅** or **Rejected ❌**.

The application leverages **Retrieval-Augmented Generation (RAG)** to retrieve relevant insurance policy information and combines it with submitted claim details and uploaded medical bills to generate an intelligent, explainable claim decision.

---

## 🚀 Features

| Feature | Description |
|---------|-------------|
| 📄 **PDF Bill Upload** | Upload medical bills in PDF format for automated analysis |
| 🔍 **Smart Extraction** | Automatically extract key information from medical bills |
| 🧠 **AI-Powered Analysis** | Intelligent claim evaluation using advanced language models |
| 📚 **RAG-Based Retrieval** | Retrieve relevant insurance policy context in real-time |
| 🔎 **Exclusion Checking** | Automatically check policy exclusions against submitted claims |
| 💰 **Amount Validation** | Validate claim amounts against policy limits and rules |
| 📋 **Document Verification** | Verify all required documents are present and valid |
| 🤖 **Groq LLM Integration** | High-speed reasoning powered by Groq's LLM infrastructure |
| 📊 **Detailed Reports** | Generate comprehensive claim analysis reports |
| ⚡ **Real-Time Decisions** | Instant claim acceptance or rejection with reasoning |

---

## 🎯 Problem Statement

Insurance claim processing is traditionally a **manual, time-consuming, and error-prone** process. Insurance providers must review:

- Claim forms and patient details
- Medical bills and treatment records
- Policy documents and coverage rules
- Exclusion lists and limitations
- Reimbursement calculations

### Challenges

| Challenge | Impact |
|-----------|--------|
| ⏱️ Time-consuming verification | Delayed claim processing |
| 📄 Manual document analysis | Human fatigue and oversight |
| ❌ Human errors | Inconsistent claim decisions |
| 📚 Large policy documents | Difficulty finding relevant clauses |
| 🐌 Processing delays | Poor customer experience |
| ⚖️ Inconsistent decisions | Trust and compliance issues |

**SmartClaim AI** automates the entire insurance claim verification pipeline using **Artificial Intelligence** and **Retrieval-Augmented Generation**.

---

## 💡 Solution

SmartClaim AI allows users to submit insurance claim information along with a medical bill. The system then performs a comprehensive multi-step analysis:

### How It Works

```
1️⃣  Upload → User submits claim form + medical bill PDF
2️⃣  Extract → System extracts data from the uploaded bill
3️⃣  Collect → Claim details (type, reason, amount, facility, date) are gathered
4️⃣  Retrieve → RAG system fetches relevant policy information
5️⃣  Verify → System checks policy requirements & exclusions
6️⃣  Validate → Claim amount is validated against policy rules
7️⃣  Analyze → Groq LLM performs intelligent claim reasoning
8️⃣  Report → Detailed claim analysis report is generated
9️⃣  Decide → Final verdict: ACCEPTED ✅ or REJECTED ❌
```

---

## 🏗️ System Architecture

```
                         ┌─────────────────────┐
                         │       USER          │
                         └──────────┬──────────┘
                                    │
                                    ▼
                      ┌──────────────────────────┐
                      │   Flask Web Application  │
                      └───────────┬──────────────┘
                                  │
                ┌─────────────────┴─────────────────┐
                │                                   │
                ▼                                   ▼
     ┌─────────────────────┐            ┌─────────────────────┐
     │   Claim Details     │            │   Medical Bill PDF  │
     │                     │            │                     │
     │ • Patient Name      │            └──────────┬──────────┘
     │ • Claim Type        │                       │
     │ • Claim Reason      │                       ▼
     │ • Claim Amount      │            ┌─────────────────────┐
     │ • Medical Facility  │            │  PDF Bill Extraction │
     │ • Treatment Date    │            └──────────┬──────────┘
     └──────────┬──────────┘                       │
                │                                   │
                └─────────────────┬─────────────────┘
                                  │
                                  ▼
                    ┌─────────────────────────┐
                    │   Claim Information     │
                    │        Processing       │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │       RAG System        │
                    └────────────┬────────────┘
                                 │
                                 ▼
             ┌─────────────────────────────────────┐
             │    Insurance Policy Documents       │
             │                                     │
             │      Membership Handbook PDFs       │
             └─────────────────┬───────────────────┘
                               │
                               ▼
                 ┌──────────────────────────┐
                 │  HuggingFace Embeddings  │
                 └────────────┬─────────────┘
                              │
                              ▼
                     ┌──────────────────┐
                     │      FAISS       │
                     │  Vector Database │
                     └────────┬─────────┘
                              │
                              ▼
                  ┌────────────────────────┐
                  │ Relevant Policy Context │
                  └────────────┬───────────┘
                               │
                               ▼
                     ┌───────────────────┐
                     │     Groq LLM      │
                     └─────────┬─────────┘
                               │
                               ▼
                 ┌─────────────────────────┐
                 │ Insurance Claim Analysis │
                 └────────────┬────────────┘
                              │
                    ┌─────────┴──────────┐
                    │                    │
                    ▼                    ▼
          ┌────────────────┐    ┌────────────────┐
          │    ACCEPTED    │    │    REJECTED    │
          └────────────────┘    └────────────────┘
```

---

## 🧠 RAG Pipeline

SmartClaim AI uses a **Retrieval-Augmented Generation (RAG)** pipeline to analyze insurance policies and evaluate claims with grounded, factual reasoning.

```
Insurance Policy PDFs
        │
        ▼
┌───────────────────┐
│ PDF Document      │
│ Loader            │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ Text Splitting    │
│ (Chunking)        │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ HuggingFace       │
│ Embeddings        │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ FAISS Vector      │
│ Database          │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ User Claim Query  │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ Similarity Search │
└─────────┬─────────┘
          │
          ▼
┌──────────────────────────┐
│ Relevant Insurance       │
│ Policy Context           │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│ Groq LLM                 │
│ (Reasoning & Decision)   │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│ Insurance Claim Decision │
└──────────────────────────┘
```

### RAG Components

| Component | Technology | Purpose |
|-----------|------------|---------|
| **Document Loader** | PyPDF / PDFPlumber | Load and parse policy PDFs |
| **Text Splitter** | Recursive Character Splitter | Chunk documents for embedding |
| **Embeddings** | HuggingFace `all-MiniLM-L6-v2` | Convert text to vector representations |
| **Vector Store** | FAISS | Fast similarity search over policy documents |
| **LLM** | Groq (Llama 3 / Mixtral) | Intelligent claim analysis and decision-making |

---

## 📋 Claim Verification Criteria

The system evaluates every insurance claim based on two major criteria:

### 1️⃣ Information Criteria

Checks whether all required information and supporting documents are **available and valid**.

| Check | Description |
|-------|-------------|
| 👤 Patient Information | Name, address, policy number verification |
| 🩺 Diagnosis | Medical condition and diagnosis details |
| 💊 Treatment Details | Type of treatment received |
| 🏥 Medical Facility | Hospital or clinic verification |
| 🧾 Medical Bill | Original receipt with itemized charges |
| 💵 Charges Breakdown | Detailed cost breakdown |
| ✍️ Documentation | Required signatures and stamps |
| 🔐 Hospital Verification | Authenticity of medical provider |

### 2️⃣ Policy Criteria

Validates the claim against the insurance policy terms.

| Check | Description |
|-------|-------------|
| 📜 Coverage Check | Is the claim type covered by the policy? |
| 🚫 Exclusion Check | Does the treatment fall under exclusions? |
| ⏳ Waiting Period | Is the waiting period satisfied? |
| 💰 Amount Limit | Is the claim within the policy limit? |
| 📅 Validity Period | Is the policy active during treatment? |
| 🔄 Pre-existing | Is it a pre-existing condition? |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| **Frontend** | HTML5, Tailwind CSS |
| **Backend** | Python, Flask |
| **PDF Processing** | PyPDF2, pdfplumber |
| **Embeddings** | HuggingFace Transformers, Sentence-Transformers |
| **Vector DB** | FAISS (Facebook AI Similarity Search) |
| **LLM** | Groq API (Llama 3 / Mixtral) |
| **RAG Framework** | LangChain |

---

## 📁 Project Structure

```
smartclaim-ai/
├── 📄 app.py                  # Flask application entry point
├── 📁 templates/
│   ├── 📄 index.html          # Claim submission form
│   └── 📄 result.html         # Claim decision display
├── 📁 static/
│   └── 📁 uploads/            # Uploaded medical bills
├── 📁 data/
│   └── 📁 policies/           # Insurance policy PDFs
├── 📁 vectorstore/            # FAISS vector database
├── 📄 requirements.txt        # Python dependencies
└── 📄 README.md               # You are here! 📍
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- Groq API Key
- Insurance policy PDFs

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/smartclaim-ai.git
cd smartclaim-ai

# 2. Create a virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scriptsctivate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Set up environment variables
export GROQ_API_KEY="your-groq-api-key-here"

# 5. Add insurance policy PDFs to data/policies/

# 6. Build the vector database (run once)
python build_vectorstore.py

# 7. Run the application
python app.py
```

### Access the App

Open your browser and navigate to:

```
http://localhost:5000
```

---

## 📸 Screenshots

### 📝 Claim Submission Form

> Clean, intuitive form for entering claim details and uploading medical bills.

### ✅ Claim Result Page

> Detailed breakdown of the AI's analysis with an **Accepted** or **Rejected** verdict.

---

## 🔮 Future Enhancements

- [ ] Multi-language support for international policies
- [ ] OCR integration for scanned/image-based bills
- [ ] Real-time policy document updates
- [ ] Blockchain-based claim audit trail
- [ ] Mobile app for on-the-go claim submission
- [ ] Integration with hospital EMR systems
- [ ] Fraud detection using anomaly detection
- [ ] Multi-insurer policy aggregation

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [Groq](https://groq.com/) for ultra-fast LLM inference
- [HuggingFace](https://huggingface.co/) for open-source embeddings
- [FAISS](https://github.com/facebookresearch/faiss) for efficient vector search
- [LangChain](https://www.langchain.com/) for the RAG framework
- [Tailwind CSS](https://tailwindcss.com/) for beautiful UI components

---

<div align="center">

### Made with ❤️ for smarter insurance claims

**[⬆ Back to Top](#-smartclaim-ai)**

</div>
