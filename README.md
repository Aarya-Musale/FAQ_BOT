🤖 **FAQ Bot with Streamlit & Gemini RAG**

An interactive Retrieval-Augmented Generation (RAG) web application that allows users to upload PDF documents, index them instantly, and chat with an AI assistant that provides accurate, source-backed answers using Google's Gemini models.

---

### 🚀 Project Overview / Description

* **What the project does:** The FAQ Bot is a document-intelligence application built with Streamlit. It parses uploaded PDF documents, splits the text into manageable chunks, generates vector embeddings via Google’s embedding models, and stores them in an in-memory vector database (ChromaDB). Users can then ask natural language questions and receive precise, context-aware answers alongside real-time token tracking and source verification.
* **The problem it solves:** Manually scanning long documents, contracts, manuals, or research papers to find specific information is time-consuming and tedious. This project automates the search and extraction process, letting users query any PDF conversationally while eliminating hallucinations through strict RAG guardrails.
* **Primary use case:** Designed for students, researchers, professionals, or customer support teams who need to quickly extract insights, summarize sections, or answer questions based on specific documentation.

---

### ✨ Key Features

* **Instant PDF Processing & Chunking:** Automatically reads uploaded PDF files and breaks them down into overlapping text chunks for optimal semantic retrieval.
* **Vector Search with ChromaDB:** Uses Google’s `gemini-embedding-001` model to embed text and retrieve the most relevant context chunks for any given query.
* **RAG-Powered Conversational UI:** Leverages Google's `gemini-3.5-flash` model with customized system instructions to answer questions based *strictly* on the document context.
* **Source Transparency:** Expandable "Sources Used" drawer under each assistant response showing the exact chunks referenced.
* **Live Token Statistics:** A dedicated sidebar tracker monitoring input tokens, output tokens, and total usage metrics across the session.

---

### 📸 Application Preview

Here is a look at the interactive web interface and chat layout:

<img width="1600" height="900" alt="bot_ss" src="https://github.com/user-attachments/assets/f70f5efd-087e-4dc9-ba73-e309bffdaaf3" />

*(Note: Place your Streamlit app screenshot inside an `assets/` folder in your project directory or link it here)*

---

### 🛠 Tech Stack & Dependencies

* **Programming Language:** Python
* **Web Framework:** Streamlit (for building the interactive user interface and chat widgets)
* **LLM & Embeddings API:** Google GenAI SDK (`google-genai` using `gemini-3.5-flash` and `gemini-embedding-001`)
* **Vector Database:** ChromaDB (for local semantic search and retrieval)
* **PDF Parser:** PyPDF2 (for extracting text from uploaded documents)
* **Environment Configuration:** python-dotenv

---

### 📂 Project Structure

```text
faq-bot/
├── app.py             # Main Streamlit web application script
├── requirements.txt   # List of required Python packages and dependencies
├── .env               # Environment file containing your GEMINI_API_KEY (not uploaded)
└── README.md          # Comprehensive project documentation

```

---

### 📥 Installation & Setup Guide

#### Step 1: Clone the repository

Clone the project repository to your local machine using terminal or command prompt:

```bash
git clone <your-repository-url>
cd faq-bot

```

#### Step 2: Set up a virtual environment

Create and activate a Python virtual environment to manage dependencies locally:

* **On macOS and Linux:**
```bash
python3 -m venv .venv
source .venv/bin/activate

```


* **On Windows:**
```bash
python -m venv .venv
.venv\Scripts\activate

```



#### Step 3: Install dependencies

Install all required libraries specified in the project requirements file:

```bash
pip install -r requirements.txt

```

#### Step 4: Configure your API Key

Create a `.env` file in the root directory of your project and add your Gemini API key:

```env
GEMINI_API_KEY=your_actual_gemini_api_key_here

```

---

### ▶️ How to Run / Usage

#### Step 1: Launch the Streamlit application

Run the following command in your terminal to start the local web server:

```bash
streamlit run app.py

```

#### Step 2: Access the application in your browser

Streamlit will automatically open a local web page in your browser (typically at `http://localhost:8501`).

#### Step 3: Upload and Chat

1. Use the sidebar to upload your PDF file.
2. Wait for the success message confirming that the chunks have been indexed.
3. Type any question regarding the document into the chat input box at the bottom.
4. Review the AI's response, check the token stats in the sidebar, and expand the "Sources Used" drawer to verify the context source chunks.

---

### 📊 Architecture & RAG Pipeline Details

* **Ingestion & Chunking:** When a PDF is uploaded, `PyPDF2` extracts raw text page-by-page. The text is passed through a custom chunking function with a default size of 2,000 characters and a 200-character overlap to preserve semantic context across boundaries.
* **Embedding & Indexing:** Each chunk is converted into a vector embedding via `gemini-embedding-001` and stored dynamically in an isolated ChromaDB collection.
* **Retrieval & Generation:** When a query is submitted, it is embedded and matched against ChromaDB to find the top 3 most relevant chunks. These chunks form the strict grounding context passed alongside conversation history into `gemini-3.5-flash`.

---

### ⚖️ License

This project is licensed under the MIT License - feel free to use, modify, and build upon it.

---

### 👤 Author / Acknowledgments

Made with ❤️ using Streamlit and Google GenAI.
