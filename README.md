# 🩺 Medical Chatbot with HuggingFace, FAISS, and Mistral

This project demonstrates how to build a **smart Medical Chatbot** using open-source tools.  
It leverages:

- **HuggingFace** → For embeddings and LLM access  
- **FAISS (CPU)** → For fast vector similarity search  
- **LangChain** → For orchestration and memory management  
- **Streamlit** → For a simple web-based conversational interface  
- **Mistral** → As the large language model for chatbot responses  

The chatbot can read and understand medical documents (e.g., *The Gale Encyclopedia of Medicine*) and answer user queries conversationally.  

---

## 📂 Project Structure

```bash
├── Pipfile
├── Pipfile.lock
├── README.md
├── connect_memory_with_llm.py
├── create_memory_for_llm.py
├── data
│   └── The_GALE_ENCYCLOPEDIA_of_MEDICINE_SECOND.pdf
├── medibot.py
├── medical-chatbot-ppt.pdf
├── requirements.txt
└── vectorstore
    └── db_faiss
        ├── index.faiss
        └── index.pkl

- data/ → Contains medical knowledge base (PDFs).  
- vectorstore/ → Stores FAISS vector indexes for retrieval.  
- create_memory_for_llm.py → Preprocesses documents and builds the vector store.  
- connect_memory_with_llm.py → Connects embeddings with the LLM.  
- medibot.py → Main chatbot app powered by Streamlit.  
- requirements.txt → Dependencies for pip.  
- Pipfile / Pipfile.lock → Environment management with Pipenv.  

```
## 🔑 Environment Variables

Before running the chatbot, make sure you set the following environment variables:

- **`HF_TOKEN`** → Your Hugging Face access token (used for embeddings/models).  
- **`GROQ_API_KEY`** → Your Groq API key (used for running the Mistral model).  

### 1. Create a `.env` file

In the root of your project, create a file named `.env`:

```bash
HF_TOKEN=your_huggingface_token_here
GROQ_API_KEY=your_groq_api_key_here
```

## 🚀 Getting Started

### 1. Prerequisites

- Python 3.9+  
- [Pipenv](https://pipenv.pypa.io/en/latest/) installed on your system  

Install Pipenv (if not already installed):

```bash
pip install pipenv
```

### 2. Set Up the Environment

Navigate to the project directory and install dependencies:

```bash
pipenv install langchain langchain_community langchain_huggingface faiss-cpu pypdf
pipenv install huggingface_hub
pipenv install streamlit

Alternatively, install dependencies via `requirements.txt`:

pip install -r requirements.txt
```
### 3. Prepare the Knowledge Base

Process the medical PDF and create a FAISS vector index:

```bash
pipenv run python create_memory_for_llm.py

This will generate embeddings and store them in:

vectorstore/db_faiss/
```
### 4. Launch the Chatbot

Start the Streamlit application:

```bash
pipenv run streamlit run medibot.py
```

## ⚙️ How It Works

1. **Document Ingestion** → PDFs from `data/` are read and chunked.  
2. **Embeddings** → Text chunks are embedded using HuggingFace models.  
3. **Vector Store** → Embeddings are indexed in FAISS for efficient retrieval.  
4. **Retrieval + LLM** → Relevant chunks are retrieved and passed to the Mistral LLM.  
5. **Conversational Interface** → Streamlit provides a user-friendly chat interface.  

