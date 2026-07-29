
# Retrieval-Augmented QA & Summarization over Public Domain Books

A Retrieval-Augmented Generation (RAG) pipeline that downloads public-domain
books (e.g. agricultural texts) from Project Gutenberg, indexes them for
semantic search, and answers questions / generates summaries using
transformer models — with an interactive Gradio demo.

## Pipeline

1. **Data collection** — download plain-text books from Project Gutenberg and
   split them into paragraphs (`preprocessed_books.json`).
2. **Indexing** — embed paragraphs with a `sentence-transformers` model
   (`all-MiniLM-L6-v2` / `multi-qa-mpnet-base-dot-v1`) and build a FAISS
   index for fast nearest-neighbor retrieval.
3. **Retrieval** — given a query, retrieve the top-k most relevant
   paragraphs from the FAISS index.
4. **QA & Summarization** — use `bert-large-uncased-whole-word-masking-finetuned-squad`
   for extractive question answering and `facebook/bart-large-cnn` (or a
   fine-tuned BART) for summarization of the retrieved context.
5. **Fine-tuning (optional)** — notebook cells for fine-tuning BART
   (summarization) and BERT (QA) on synthetic/derived datasets built from
   the book paragraphs.
6. **Demo** — a Gradio app that ties retrieval + QA/summarization together
   into an interactive interface.

## Project structure

```
.
├── notebook.ipynb      # Main notebook: full pipeline end to end
├── requirements.txt    # Python dependencies
└── README.md
```

## Setup

```bash
git clone <your-repo-url>
cd <repo-name>
python -m venv venv
source venv/bin/activate   # on Windows: venv\Scripts\activate
pip install -r requirements.txt
```

## Usage

Open and run `notebook.ipynb` top to bottom in Jupyter or VS Code:

```bash
jupyter notebook notebook.ipynb
```

The notebook will:
- Download the source books and build `preprocessed_books.json`
- Compute paragraph embeddings and a FAISS index
- Load the QA/summarization models
- Launch a Gradio interface for interactive querying

> Note: downloaded books, embeddings, and the FAISS index are treated as
> generated artifacts and are not tracked in version control (see
> `.gitignore`). Re-run the early notebook cells to regenerate them.

## Models used

| Task | Model |
|---|---|
| Embedding / retrieval | `sentence-transformers/all-MiniLM-L6-v2`, `multi-qa-mpnet-base-dot-v1` |
| Question answering | `bert-large-uncased-whole-word-masking-finetuned-squad` |
| Summarization | BART (`facebook/bart-large-cnn` base, fine-tunable) |
| Vector search | FAISS (`IndexFlatL2`) |

## Features

- Retrieval-Augmented Generation (RAG)
- Semantic search using Sentence Transformers
- FAISS vector indexing
- Extractive Question Answering with BERT
- Abstractive Summarization with BART
- Interactive Gradio interface
- Optional fine-tuning for QA and summarization

## Example Query

Question:
> What are the main causes of soil erosion?

Retrieved Context:
> ...

Generated Answer:
> Soil erosion is mainly caused by...

Summary:
> Soil erosion results from...

## Future Improvements

- Support multiple document collections
- Hybrid BM25 + Dense Retrieval
- GPU acceleration
- Docker deployment
- Evaluation with RAGAS
