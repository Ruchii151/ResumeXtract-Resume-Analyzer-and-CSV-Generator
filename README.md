# ResumeXtract-Resume-Analyzer-and-CSV-Generator

A production-ready, LLM-powered bulk resume analysis application built with **Streamlit, LangChain, Pydantic, and Google Gemini**.
The app allows users to upload a ZIP file containing multiple resumes (PDF/DOCX) and automatically extracts structured candidate information in a clean, tabular format.

This project is designed as a **focused information extraction system**, not a generic text summarizer. It enforces **strict schema-based outputs**, prevents hallucination, and demonstrates real-world usage of **LLMs for document intelligence at scale**.

---

## Features

### Bulk Resume Processing

* Upload a **single ZIP file** containing multiple resumes
* Supports **PDF and DOCX** formats
* Automatic extraction without manual parsing

### Structured Information Extraction

Extracts the following fields for every resume:

* Name
* Email
* Phone
* Skills
* Experience Summary
* LinkedIn
* GitHub

All outputs strictly follow a **predefined Pydantic schema**.

### Hallucination-Safe LLM Design

* Zero-temperature LLM configuration
* Strict JSON-only output enforcement
* Missing information returned as empty strings
* No fabricated data

### Clean & Modern UI

* Dark gradient / neon-style UI
* Progress bar for bulk processing
* Responsive dataframe display
* One-click CSV export

### Downloadable Results

* Structured resume data downloadable as a **CSV file**
* Ready for ATS pipelines, analytics, or dashboards

---

## Architecture

### High-Level Flow

ZIP Upload → Resume Parsing → Prompt Construction → Gemini LLM → Schema Validation → UI Render → CSV Export

---

## Components

### 1. Streamlit UI Layer

* ZIP file uploader
* Progress indicator during analysis
* Tabular display of extracted resume data
* CSV download button
* Custom CSS for modern UI styling

### 2. Prompt Engineering Layer

A **strict system prompt** defines the analyzer’s role and constraints:

* Acts only as a resume information extractor
* Returns output strictly in the defined JSON schema
* Does not hallucinate missing information
* Returns JSON only (no explanations or markdown)

Implemented using:

* Plain prompt strings
* `PydanticOutputParser` for validation

### 3. LLM Layer (Google Gemini)

* Model: **gemini-2.5-flash-lite**
* Accessed via `ChatGoogleGenerativeAI`
* Stateless invocation per resume
* Deterministic behavior using temperature = 0

### 4. Schema Validation Layer

* Resume fields defined using **Pydantic**
* LLM output parsed and validated automatically
* Any deviation from schema raises parsing errors (fail-fast design)

### 5. File Handling & Parsing

* ZIP extraction using `zipfile`
* PDF parsing via `PyPDF2`
* DOCX parsing via `python-docx`
* Text consolidated before LLM invocation

---

## Tech Stack

| Layer         | Tool / Library      |
| ------------- | ------------------- |
| UI            | Streamlit           |
| LLM           | Google Gemini       |
| Prompting     | LangChain           |
| Validation    | Pydantic            |
| File Parsing  | PyPDF2, python-docx |
| Data Handling | Pandas              |
| Environment   | python-dotenv       |
| Language      | Python              |

---

## How It Works (Step-By-Step)

### Resume Upload

User uploads a ZIP file containing multiple resumes.

### Resume Extraction

Each PDF/DOCX file is:

* Read
* Converted to raw text
* Prepared for LLM processing

### Prompt Initialization

A strict system prompt is constructed defining:

* Extraction rules
* Output schema
* Hallucination constraints

### LLM Invocation

* Gemini processes each resume independently
* Returns structured JSON only

### Schema Validation

* Output parsed using `PydanticOutputParser`
* Ensures consistency and correctness

### UI Rendering

* All parsed resumes displayed in a dataframe
* Progress bar shows real-time processing status

### Export

* Entire dataset downloadable as a CSV file

---

## Setup and Installation

### Clone the Repository

```bash
git clone https://github.com/Ruchii151/ai-resume-analyzer.git
cd ai-resume-analyzer
```

### Create and Activate Virtual Environment (Recommended)

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

**Core dependencies:**

* streamlit
* langchain
* langchain-google-genai
* pandas
* PyPDF2
* python-docx
* python-dotenv

---

## Environment Variables

Create a `.env` file in the project root:

```
gemini=YOUR_GOOGLE_API_KEY
```

The app automatically maps this to `GOOGLE_API_KEY`.

---

## Run the App

```bash
streamlit run main.py
```

Open the local URL (usually `http://localhost:8501`) in your browser.

---

## Usage

1. Open the app
2. Upload a ZIP containing resumes
3. Wait for analysis to complete
4. View structured resume data
5. Download results as CSV

---

## Project Goals (Why This Exists)

* Demonstrate **real-world LLM document processing**
* Show **schema-driven prompt discipline**
* Avoid generic summarization or chat-style hallucination
* Prove understanding of:

  * LangChain output parsing
  * Deterministic LLM usage
  * Bulk document automation
* Build a **portfolio-ready AI application**

---

## Possible Improvements

* Resume scoring & ranking
* Skill matching against job descriptions
* Duplicate candidate detection
* Database persistence
* Authentication & role-based access
* Cloud deployment (GCP / AWS)

---

## UI

<img width="1915" height="946" alt="image" src="https://github.com/user-attachments/assets/dd80ee75-55fe-450c-9af4-b0e885c00cad" />


## Demo Video: 


---

## Support & Feedback

Have questions or found a bug?

📧 Email: **[pruchita565@gmail.com](mailto:pruchita565@gmail.com)**
💼 LinkedIn: **[www.linkedin.com/in/patil-ruchita](http://www.linkedin.com/in/patil-ruchita)**

---

⭐ If you like this project and want to implement by yourself, don't forget to star the repository!

Just tell me.
