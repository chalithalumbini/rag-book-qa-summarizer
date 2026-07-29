# 📚 Retrieval-Augmented QA & Summarization over Public Domain Books

A **Retrieval-Augmented Generation (RAG)** pipeline that downloads public-domain books from **Project Gutenberg**, indexes them using **Sentence Transformers** and **FAISS**, and performs **semantic search**, **question answering**, and **text summarization** using Transformer models.

The project also includes an interactive **Gradio** web application.

---

## ✨ Features

- 📖 Download books from Project Gutenberg
- 🧹 Preprocess and clean text
- 🔍 Semantic search using Sentence Transformers
- ⚡ Fast vector retrieval with FAISS
- ❓ Question Answering using BERT
- 📝 Text Summarization using BART
- 🌐 Interactive Gradio interface
- 🎯 Optional model fine-tuning

---

## 🏗️ Pipeline

```
Project Gutenberg Books
            │
            ▼
     Text Preprocessing
            │
            ▼
 Paragraph Segmentation
            │
            ▼
 Sentence Embeddings
            │
            ▼
      FAISS Index
            │
            ▼
 User Question
            │
            ▼
 Semantic Retrieval
            │
            ▼
 ┌───────────────┬───────────────┐
 │               │               │
 ▼               ▼               ▼
Question      Summary       Retrieved
Answer        Generation      Context
```

---

## 📂 Project Structure

```text
rag-book-qa-summarizer/
│── notebook.ipynb
│── README.md
│── requirements.txt
│── .gitignore
│── LICENSE
│── images/
└── sample_data/
```

---

# 🚀 Getting Started

## 1. Clone the Repository

```bash
git clone https://github.com/<your-github-username>/rag-book-qa-summarizer.git
cd rag-book-qa-summarizer
```

---

## 2. Create a Virtual Environment

### Windows (PowerShell)

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks activation:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
```

### Linux / macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
```

---

## 3. Install Dependencies

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

---

## 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

or

```bash
jupyter lab
```

Open **`notebook.ipynb`** and run all cells.

---

## 📋 Requirements

- Python 3.10+
- Git
- Jupyter Notebook or JupyterLab

---

## 🤖 Models Used

| Task | Model |
|------|-------|
| Embedding | sentence-transformers/all-MiniLM-L6-v2 |
| Alternative Embedding | sentence-transformers/multi-qa-mpnet-base-dot-v1 |
| Question Answering | bert-large-uncased-whole-word-masking-finetuned-squad |
| Summarization | facebook/bart-large-cnn |
| Vector Search | FAISS (IndexFlatL2) |

---

## 💡 Example

### Question

> What are the main causes of soil erosion?

### Generated Answer

> Soil erosion is primarily caused by water, wind, and unsustainable agricultural practices.

### Summary

> Soil erosion results from natural forces and poor land management.

---

## 📌 Future Improvements

- Hybrid Retrieval (BM25 + Dense Retrieval)
- Multi-document Retrieval
- Docker Support
- FastAPI REST API
- GPU Acceleration
- Multi-language Support
- RAGAS Evaluation

---

## 📷 Demo

Add screenshots of the Gradio interface here.

```text
images/demo.png
```

Example:

```markdown
![Demo](images/demo.png)
```

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Push to your branch.
5. Open a Pull Request.

---

## 📄 License

This project is licensed under the **MIT License**.

---

## 🙏 Acknowledgements

This project makes use of the following open-source projects:

- Hugging Face Transformers
- Sentence Transformers
- FAISS
- Gradio
- Project Gutenberg
