## 🎯 What is AI Study Buddy?

AI Study Buddy is a Streamlit web application that transforms any PDF or TXT study material into an interactive learning experience. It combines **RAG (Retrieval-Augmented Generation)** with **Groq's Llama 3.3** to give you accurate, grounded answers — not hallucinations.

Upload your notes, textbook chapter, or research paper and instantly get:

- 💬 **Ask Questions** — Chat with your document like a tutor
- 🧠 **Quiz Generator** — Auto-generate MCQ questions at easy / medium / hard
- 🃏 **Flashcards** — Front/back cards with shuffle and reveal
- 📋 **Smart Summary** — Structured summary with key concepts and definitions

---

## 🚀 Demo

```
Upload PDF → Process → Ask / Quiz / Flashcard / Summarize
```

**Example questions you can ask:**
- *"What is the difference between supervised and unsupervised learning?"*
- *"Explain overfitting in simple terms"*
- *"What is RAG and how does it work?"*

---

## 🏗️ How It Works

```
User uploads PDF/TXT
        ↓
rag_engine.py extracts and chunks the text
        ↓
TF-IDF vectorization + cosine similarity search
        ↓
Top relevant chunks retrieved as context
        ↓
Groq API (Llama 3.3) generates grounded answer
        ↓
Result shown in Streamlit UI
```

### Why RAG?

Instead of letting the AI answer from memory (which can hallucinate), RAG first **searches your uploaded document** for relevant passages, then gives those passages as context to the LLM. Every answer is grounded in your actual study material.

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| UI | Streamlit | Web interface with 4 study modes |
| LLM | Groq API (Llama 3.3-70b) | Question answering, quiz, flashcard generation |
| RAG | TF-IDF + Cosine Similarity | Search relevant chunks from document |
| PDF | PyPDF2 | Extract text from uploaded PDFs |
| Language | Python 3.10+ | Core programming language |

> **Built without LangChain** — the entire RAG pipeline is implemented from scratch using only `math` and standard Python libraries.

---

## 📁 Project Structure

```
studybuddy/
├── app.py              ← Main Streamlit app (4 study modes, custom UI)
├── rag_engine.py       ← PDF reader, text chunker, TF-IDF search
├── llm_engine.py       ← All Groq API calls (Q&A, quiz, flashcards, summary)
├── requirements.txt    ← Dependencies
├── .env                ← Your API key (never commit this!)
└── data/               ← Optional: store sample documents
```

---

## ⚙️ Setup & Installation

### Prerequisites
- Python 3.10 or higher
- A free Groq API key from [console.groq.com](https://console.groq.com)

### Step 1 — Clone the repository
```bash
git clone https://github.com/your-username/ai-study-buddy.git
cd ai-study-buddy
```

### Step 2 — Create virtual environment
```bash
python -m venv venv
```

### Step 3 — Activate virtual environment
```bash
# Windows
venv\Scripts\activate.bat

# Mac / Linux
source venv/bin/activate
```

### Step 4 — Install dependencies
```bash
pip install -r requirements.txt
```

### Step 5 — Add your Groq API key

Create a `.env` file in the project folder:
```
GROQ_API_KEY=gsk_your_key_here
```

Or set it directly in terminal:
```bash
# Windows
set GROQ_API_KEY=gsk_your_key_here

# Mac / Linux
export GROQ_API_KEY=gsk_your_key_here
```

### Step 6 — Run the app
```bash
streamlit run app.py
```

Open your browser at `http://localhost:8501` 🎉

---

## 📖 How to Use

1. **Upload** a PDF or TXT file using the sidebar
2. Click **Process Document** — wait for "Indexed X chunks!"
3. Choose a mode from the sidebar:

| Mode | What to do |
|---|---|
| Ask Questions | Type any question in the chat box |
| Quiz Me | Choose difficulty → click Generate Quiz |
| Flashcards | Click Generate Cards → use Prev/Next/Reveal |
| Summary | Click Generate Summary → enter a concept for deep dive |

---

## ✨ Features

- **RAG from scratch** — No LangChain or vector databases needed
- **Multi-format support** — Works with both PDF and plain text files
- **Overlapping chunks** — 300-word chunks with 50-word overlap for better context
- **Source transparency** — See exactly which document excerpts were used to answer
- **Quiz scoring** — Automatic grading with percentage and letter grade
- **Flashcard shuffle** — Randomize cards for better memorization
- **Dark theme UI** — Easy on the eyes for long study sessions
- **Session memory** — Chat history preserved within the session

---

## 📦 Dependencies

```txt
streamlit>=1.35.0
groq>=0.9.0
PyPDF2>=3.0.0
python-dotenv>=1.0.0
```

---

## 🔑 Getting a Free Groq API Key

1. Go to [console.groq.com](https://console.groq.com)
2. Sign up with Google (free, no credit card needed)
3. Click **API Keys** → **Create API Key**
4. Copy the key (starts with `gsk_`)
5. Paste it in your `.env` file

---

## 🧠 What I Learned Building This

- Building a **RAG pipeline from scratch** without any framework
- **TF-IDF vectorization** and cosine similarity for text search
- **PDF text extraction** and overlapping chunking strategies
- **Streamlit session state** for multi-step interactive apps
- **Prompt engineering** for structured JSON outputs (quiz, flashcards)
- Integrating **Groq API** with Llama 3.3 for fast free inference

---

## 🚧 Future Improvements

- [ ] Add ChromaDB for persistent vector storage
- [ ] Support multiple documents at once
- [ ] Add Hindi and Tamil language support
- [ ] Export quiz results as PDF report
- [ ] Add spaced repetition algorithm for flashcards
- [ ] Deploy on Streamlit Cloud

---

## ⚠️ Disclaimer

This tool is for educational purposes. Always verify important information with authoritative sources. The AI answers are based only on your uploaded document.

---

## 👨‍💻 Author

**Krishna Bai B**
- 📧 krishnabaib03@gmail.com
- 💼 [LinkedIn](www.linkedin.com/in/krishna-bai03)
- 🐙 [GitHub](https://github.com/krishnabaib)

---

## 📄 License

This project is licensed under the MIT License — feel free to use, modify, and share.

---

*Built with ❤️ using Python, Streamlit, and Groq*
