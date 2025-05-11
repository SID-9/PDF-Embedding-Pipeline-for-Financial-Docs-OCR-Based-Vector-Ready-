# PDF-Embedding-Pipeline-for-Financial-Docs (OCR-Based, Vector-Ready)

A powerful backend pipeline to extract both text and image content from PDF files (using OCR), and convert them into semantic vector embeddings using the BAAI `bge-base-en` model. Ideal for building AI-powered financial document search or QA systems.

---

# 🚀 Features

* 📄 Extracts paragraph text directly from PDF pages
* 🖼️ Runs OCR on embedded PDF images using Tesseract
* 🧠 Generates high-quality sentence embeddings with `bge-base-en`
* 🗂️ Saves all extracted data and metadata into a `.pkl` file
* 🧾 Embedding output is vector-db ready for search and retrieval
* 💾 Modular structure to plug into FAISS, Chroma, or RAG apps

---

| Layer           | Technology              |
| --------------- | ----------------------- |
| PDF Parser      | PyMuPDF (`fitz`)        |
| OCR Engine      | `pytesseract`           |
| Image Handling  | `PIL`                   |
| Embedding Model | BAAI `bge-base-en`      |
| Data Handling   | `pandas`, `pickle`      |
| Vector Ready    | Any FAISS / Chroma etc. |
| Runtime         | Python                  |

---

# 🔧 Local Setup

### 1. Clone the repo

```bash
git clone https://github.com/your-username/pdf-embedding-pipeline.git
cd pdf-embedding-pipeline
```

### 2. Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

# 🗂️ Project Structure

```
financial-chatbot/
│
├── data/
│   ├── pdfs/                 # ← Input PDFs
│   ├── processed_texts.pkl   # ← Extracted text with metadata
│   └── embeddings.pkl        # ← Final vector embeddings
│
├── extract_text.py           # ← OCR & paragraph extractor
├── create_embeddings.py      # ← Embedding generator
├── requirements.txt
└── README.md
```

---

# 🧠 Model Used

* **BAAI/bge-base-en**

  * HuggingFace sentence embedding model
  * Great for document similarity, RAG, search, and QA tasks
  * [🔗 Model Link](https://huggingface.co/BAAI/bge-base-en)

---

# 📌 Flow Summary

1. 🗂️ Drop PDFs into the `data/pdfs/` folder
2. 🧾 Run `extract_text.py` to get all paragraph + OCR text
3. 🧠 Run `create_embeddings.py` to convert extracted data into embeddings
4. 📦 Use `embeddings.pkl` to load into a vector DB (FAISS, Pinecone, Chroma, etc.)

---

# 📌 To Extend With New PDFs

Just add your new `.pdf` files into `data/pdfs/` and re-run:

```bash
python extract_text.py
python create_embeddings.py
```

This will regenerate the `.pkl` files with **all PDFs processed**, including the newly added ones.

---

# 📜 License

MIT License

---

Would you like me to push this to a GitHub Gist or generate a Markdown file for direct use?
