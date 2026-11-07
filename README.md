# Semantic Search with Gemini Embeddings + ChromaDB

A small, self-contained project exploring how vector embeddings and vector
databases enable **semantic search** — finding results by meaning rather
than exact keyword matches.

Built while working through vector database fundamentals: vector math,
embedding models, and how indexing (IVF/HNSW) works under the hood, then
applying it end-to-end with Google's Gemini embedding model and ChromaDB.

## What this project does

- Generates sentence embeddings using Google's `gemini-embedding-001` model
- Computes a cosine similarity matrix to compare sentence meanings
- Reduces high-dimensional embeddings to 3D using PCA for visualization
- Stores embeddings in a local ChromaDB collection
- Runs semantic search queries that match by meaning, not keyword overlap
  (e.g. querying `"jungle"` returns smartphone-related sentences with
  zero literal word overlap)

## Tech stack

- Python
- [Google Gemini API](https://ai.google.dev/) (`gemini-embedding-001`)
- [ChromaDB](https://www.trychroma.com/) — local vector store
- scikit-learn (cosine similarity, PCA)
- pandas, numpy, plotly

## How it works

1. **Embed** — A set of sample sentences is sent to the Gemini embedding
   model, returning a 768-dimensional vector per sentence.
2. **Compare** — A cosine similarity matrix shows which sentences the model
   considers close in meaning.
3. **Visualize** — PCA compresses the 768-dimensional vectors down to 3D so
   the embedding space can be plotted and inspected visually.
4. **Store** — Vectors are written to a ChromaDB collection, each tied back
   to its original sentence.
5. **Query** — A new query string is embedded on the fly and used to
   retrieve the nearest sentences from the collection by vector distance.

## Setup

You'll need a Google API key with access to the Gemini API. If running in
Colab, add it via **Secrets → GOOGLE_API_KEY**. Locally, set it as an
environment variable and adjust the notebook's key-loading cell accordingly.

## Running it

Open `Semantic_Search_Gemini_ChromaDB.ipynb` and run the cells top to bottom.
Each section is documented inline — embedding generation, similarity
comparison, PCA visualization, and the ChromaDB store/query steps.

## Key takeaway

Keyword search breaks down when the query doesn't share exact words with
the target content. Embedding-based semantic search solves this by
representing meaning as vectors — things that are conceptually similar end
up close together in vector space, regardless of exact wording.

## Credits

Built while learning from the *Vector Databases Full Course for Beginners*
by freeCodeCamp.org (course by codeEdx). Code adapted and restructured as a
standalone, documented project.
