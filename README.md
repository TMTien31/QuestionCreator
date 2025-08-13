# QuestionCreator

An intelligent FastAPI-based web application that automatically generates interview questions and answers from PDF documents using **Google Gemini 2.0** and **LangChain RAG** (Retrieval-Augmented Generation) architecture. The system processes coding materials and documentation to create comprehensive question-answer pairs for exam preparation and coding tests.

## Technology Stack

- **Backend**: FastAPI with Uvicorn server
- **Language Model**: Google Gemini 2.0 Flash Lite
- **Document Processing**: LangChain, PyPDF2, PyPDFLoader
- **Embeddings**: HuggingFace sentence-transformers (all-MiniLM-L6-v2)
- **Vector Database**: FAISS
- **Text Processing**: TokenTextSplitter with GPT-3.5-turbo tokenization
- **Frontend**: HTML/CSS with Jinja2 templating
- **File Handling**: Async file operations with aiofiles

## Installation & Setup

### Step 1: Clone the Repository
```bash
git clone https://github.com/TMTien31/QuestionCreator.git
cd QuestionCreator
```

### Step 2: Create Virtual Environment
```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate

# On macOS/Linux:
source venv/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Get Google Gemini API Key
1. Go to [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Create a new API key
3. Copy the generated key

### Step 5: Create Environment File
Create a `.env` file in the project root directory:
```bash
# Create .env file
touch .env  # On macOS/Linux
# or create manually on Windows
```

Add your API key to the `.env` file:
```env
GEMINI_API_KEY=your_gemini_api_key_here
```

### Step 6: Prepare Documents
- Place your PDF documents (coding materials, documentation) in the `data/` folder
- The system supports PDFs up to 5 pages for optimal processing
- Sample documents are included: `SDG.pdf` and `stats.pdf`

## Running the Application

### Start the FastAPI Server
```bash
python app.py
```

### Access the Application
1. Open your web browser
2. Navigate to: `http://0.0.0.0:8080` or `http://localhost:8080`
3. You should see the Interview Question Creator interface

## How It Works

### 1. Document Upload
- Upload PDF files through the web interface
- Files are stored in `static/docs/` directory
- Maximum recommended: 5 pages per document

### 2. Question Generation Process
- **Text Extraction**: PyPDFLoader extracts content from PDF documents
- **Text Chunking**: TokenTextSplitter divides content into manageable chunks (10,000 tokens for questions, 1,000 for answers)
- **Question Creation**: Google Gemini 2.0 generates relevant interview questions using LangChain's refine summarization chain
- **Vector Store**: FAISS creates embeddings using HuggingFace transformers for efficient answer retrieval
- **Answer Generation**: RetrievalQA chain generates accurate answers based on document context

### 3. Output
- Questions and answers are saved as CSV files in `static/output/QA.csv`
- Each row contains a question-answer pair ready for study or interview preparation

## Project Structure

- **`app.py`** — FastAPI application with upload and analysis endpoints
- **`src/helper.py`** — Core processing pipeline with LangChain integration
- **`src/prompt.py`** — Prompt templates for question generation and refinement
- **`templates/index.html`** — Web interface for document upload and processing
- **`static/`** — Static assets including uploaded docs and generated outputs
- **`data/`** — Sample PDF documents for testing
- **`research/experiment.ipynb`** — Jupyter notebook for experimentation
- **`requirements.txt`** — Python dependencies
- **`setup.py`** — Package installation metadata
