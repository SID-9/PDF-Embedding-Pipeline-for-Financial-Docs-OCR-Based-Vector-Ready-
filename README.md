# PDF-Embedding-Pipeline-for-Financial-Docs (OCR-Based, FastAPI + Streamlit)

An AI-powered document processing pipeline that extracts text and OCR data from PDFs, generates embeddings using the BAAI `bge-base-en` model, and lets users interact with the backend via a clean Streamlit frontend. Perfect for RAG, financial QA, or search use cases.

---

# 🚀 Features

* 📄 Upload and extract text from PDF documents via Streamlit UI
* 🖼️ Automatically runs OCR on embedded images in PDFs
* 🧠 Converts all text into semantic embeddings with `bge-base-en`
* 🧾 Saves metadata-rich output in `.pkl` files for reuse
* 🔁 Seamless FastAPI ↔ Streamlit communication
* ⚡ Fully modular to integrate into vector databases like FAISS/Chroma
* 🌐 CORS enabled for safe frontend-backend interaction
* 🐳 (Optional) Easily containerized with Docker

---

| Layer            | Technology          |
| ---------------- | ------------------- |
| Frontend         | Streamlit           |
| Backend          | FastAPI             |
| PDF Parser       | PyMuPDF (`fitz`)    |
| OCR Engine       | `pytesseract`       |
| Embedding Model  | BAAI `bge-base-en`  |
| Image Handling   | `PIL`               |
| Vector Support   | FAISS, Chroma-ready |
| Containerization | Docker (optional)   |

---
# 🗂️ Project Structure

```
financial-chatbot/
│
├── data/
│   ├── pdfs/                 # ← Input PDFs
│   ├── processed_texts.pkl   # ← Extracted text with metadata
│   └── embeddings.pkl        # ← Final vector embeddings
├── scripts/
│   ├── create_embeddings.py  # ← Embeds the extracted text
│   └── extract_text.py       # ← Extracts paragraph and OCR text
│
├── app/
│   ├── app.py
│   └── main.py

---

# ▶️ How to Run

### 🖥️ Terminal 1 — Start FastAPI Backend

```bash
uvicorn main:app --reload
```

* Visit the API Docs: [http://localhost:8000/docs](http://localhost:8000/docs)

### 🧑‍💻 Terminal 2 — Start Streamlit Frontend

```bash
streamlit run app.py
```

* Visit the UI: [http://localhost:8501](http://localhost:8501)

---

# 🧠 Model Used

* **BAAI/bge-base-en**

  * HuggingFace sentence embedding model
  * Optimized for document similarity, search, and RAG pipelines
  * [🔗 Model Card](https://huggingface.co/BAAI/bge-base-en)

---

# 📌 Flow Summary

1. 📤 Upload PDF via Streamlit UI
2. ⚙️ FastAPI receives and processes:

   * Paragraph text from PDF
   * OCR from images
3. 🧠 `create_embeddings.py` converts extracted text into vector embeddings
4. 🗂️ Results stored in `.pkl` files
5. 🔍 Embeddings can now be queried, searched, or plugged into RAG pipelines

---

# 🧩 Add New PDFs Later

To extend the project with new files:

1. Add PDFs into `data/pdfs/`
2. Re-run:

```bash
python extract_text.py
python create_embeddings.py
```

---

# 🔐 API / Security

* Uses CORS middleware to allow interaction between Streamlit and FastAPI

---
