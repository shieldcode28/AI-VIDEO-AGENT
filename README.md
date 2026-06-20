# 🎬 AI Meeting Intelligence Assistant

An AI-powered Meeting Intelligence Assistant that can transcribe meetings, generate summaries, extract action items, identify key decisions, detect open questions, and allow users to chat with meeting content using Retrieval-Augmented Generation (RAG).

---

## 🚀 Features

### 🎙️ Automatic Transcription

* Upload local audio/video files or provide a YouTube URL.
* Supports:

  * English meetings using OpenAI Whisper.
  * Hindi/Hinglish meetings using Sarvam AI Speech-to-Text Translation.

### 📋 AI Meeting Summary

* Generates concise professional meeting summaries.
* Handles long transcripts using Map-Reduce summarization.

### 🏷️ Automatic Meeting Title Generation

* Generates a short and meaningful meeting title automatically.

### ✅ Action Item Extraction

* Detects tasks assigned during the meeting.
* Extracts:

  * Task Description
  * Owner
  * Deadline (if mentioned)

### 🔑 Key Decision Extraction

* Identifies important decisions made during discussions.

### ❓ Open Question Detection

* Finds unresolved questions and follow-up topics.

### 🧠 Chat With Your Meeting (RAG)

* Ask natural language questions about the meeting.
* Uses ChromaDB vector search and Mistral LLM for accurate retrieval-based responses.
* Reduces hallucinations by grounding answers in the transcript.

---

# 🏗️ System Architecture

```text
YouTube URL / Local File
            │
            ▼
      Audio Processor
      (yt-dlp + FFmpeg)
            │
            ▼
      Audio Chunking
            │
            ▼
       Transcriber
 ┌─────────────────────┐
 │ Whisper (English)   │
 │ Sarvam (Hinglish)   │
 └─────────────────────┘
            │
            ▼
      Full Transcript
            │
 ┌──────────┼──────────┐
 ▼          ▼          ▼
Title     Summary    Extractor
Gen       Gen        (Actions,
                     Decisions,
                     Questions)
            │
            ▼
      Vector Store
       (ChromaDB)
            │
            ▼
       Retriever
            │
            ▼
      Mistral LLM
            │
            ▼
      Meeting Chat
```

---

# 🛠️ Tech Stack

## Frontend

* Streamlit

## LLM & AI

* Mistral AI
* LangChain
* OpenAI Whisper
* Sarvam AI

## RAG Pipeline

* ChromaDB
* HuggingFace Embeddings
* all-MiniLM-L6-v2

## Media Processing

* yt-dlp
* FFmpeg
* pydub

## Backend

* Python

---

# 📂 Project Structure

```text
AI-Meeting-Assistant/
│
├── app.py                 # Streamlit UI
├── main.py                # CLI version
│
├── core/
│   ├── transcriber.py
│   ├── summarizer.py
│   ├── extractor.py
│   ├── rag_engine.py
│   └── vector_store.py
│
├── utils/
│   └── audio_processor.py
│
├── vector_db/
│
├── requirements.txt
├── .env
└── README.md
```

---

# ⚙️ Installation

## Clone Repository

```bash
git clone https://github.com/yourusername/ai-meeting-assistant.git

cd ai-meeting-assistant
```

## Create Virtual Environment

```bash
python -m venv .venv
```

### Windows

```bash
.venv\Scripts\activate
```

### Linux / Mac

```bash
source .venv/bin/activate
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

---

# 🔑 Environment Variables

Create a `.env` file:

```env
MISTRAL_API_KEY=your_mistral_api_key

SARVAM_API_KEY=your_sarvam_api_key

WHISPER_MODEL=small
```

---

# ▶️ Run Application

## Streamlit UI

```bash
streamlit run app.py
```

Open:

```text
http://localhost:8501
```

---

## CLI Version

```bash
python main.py
```

---

# 💡 How It Works

### Step 1: Audio Processing

* Download audio from YouTube or load local media.
* Convert audio to WAV format.
* Split audio into 10-minute chunks.

### Step 2: Speech-to-Text

* English → Whisper
* Hinglish → Sarvam AI

### Step 3: Transcript Generation

* Merge all chunk transcripts into a single meeting transcript.

### Step 4: Meeting Intelligence

Generate:

* Title
* Summary
* Action Items
* Key Decisions
* Open Questions

### Step 5: Vector Database

* Split transcript into chunks.
* Generate embeddings using all-MiniLM-L6-v2.
* Store vectors in ChromaDB.

### Step 6: Retrieval-Augmented Generation

* Retrieve relevant transcript chunks.
* Pass retrieved context to Mistral LLM.
* Generate grounded answers.

---

# 🎯 Example Use Cases

### Corporate Meetings

* Meeting minutes generation
* Action item tracking

### Online Lectures

* Generate lecture notes
* Ask questions about lectures

### YouTube Podcasts

* Summarize long discussions
* Extract important insights

### Team Standups

* Track decisions and follow-ups

---

# 📸 Screenshots

Add screenshots here:

```text
screenshots/home.png
screenshots/summary.png
screenshots/chat.png
```

---

# 🔮 Future Improvements

* Speaker Diarization
* Multi-language Support
* PDF Export
* Meeting Analytics Dashboard
* Cloud Deployment
* Real-time Meeting Transcription
* Email Action Item Delivery
* Calendar Integration

---

# 🎓 Interview Highlights

This project demonstrates:

* Generative AI
* Retrieval-Augmented Generation (RAG)
* Vector Databases
* Embeddings
* LangChain LCEL Pipelines
* Prompt Engineering
* Speech-to-Text Systems
* LLM Application Development
* End-to-End AI Product Development

---

# 👨‍💻 Author

Parth Sharma

B.Tech CSE (AI)

GL Bajaj Institute of Technology & Management
