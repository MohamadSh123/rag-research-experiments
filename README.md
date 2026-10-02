# Research RAG: Chunking, Retrieval and LLM Comparison

An experimental retrieval-augmented generation (RAG) setup over a corpus of 11 public AI papers and reports (532 pages). It compares three axes of a RAG pipeline:

- **Chunking:** small chunks (500 characters, 3,376 chunks) against large chunks (1,500 characters, 1,259 chunks).
- **Generation:** a local model (`google/flan-t5-large`) against an external API (`llama-3.3-70b-versatile` via Groq).
- **Retrieval:** dense vector search against a hybrid retriever (BM25 + vectors, equal weights).

## Stack

LangChain, ChromaDB, `sentence-transformers/all-MiniLM-L6-v2` embeddings, BM25, Hugging Face Transformers, Groq API, PyMuPDF.

## Corpus

The PDFs are not included in this repository. The corpus consists of public papers and reports, including:

- Attention Is All You Need (Vaswani et al., 2017)
- Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks (Lewis et al., 2020)
- Chain-of-Thought Prompting Elicits Reasoning in Large Language Models (Wei et al., 2022)
- The Gemini technical report, the GPT-4.5 system card, a Llama 3 paper and a YOLOv8 paper
- UNESCO Recommendation on the Ethics of Artificial Intelligence
- An introduction to large language models, and a prompt engineering guide

## Running the notebook

The notebook is designed for Google Colab with a GPU runtime.

1. Put the PDFs in a Google Drive folder named `Data` (under My Drive).
2. Add a Colab secret named `GROQ_API_KEY` and enable notebook access. The key is never stored in the code.
3. Run the first cell. It installs the pinned libraries and restarts the runtime once.
4. Run all cells.

## Current limitations

The current evaluation is qualitative: answers are printed side by side, and the plot compares top-1 retrieval distance between chunk sizes. Distances from different chunkings are not directly comparable, so the experiment does not yet say which configuration is better. The roadmap below addresses this.

## Roadmap

- [ ] Build an evaluation set of about 30 questions with reference answers and source pages.
- [ ] Measure retrieval with Hit@k and MRR, and answer quality with a correctness score.
- [ ] Report a results table for every configuration (chunking × retriever × LLM).
- [ ] Refactor the single experiment cell into functions with proper error handling.

## About

Developed as a team project for the Information Retrieval course in the B.Sc. in Information Systems, University of Haifa, 2026.
