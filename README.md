This project implements a Retrieval-Augmented Generation (RAG) system that combines document retrieval and language model-based generation to provide answers to user queries based on the context of uploaded documents.

Workflow
1) Document Loading:
The system loads a PDF document (e.g., constitution.pdf) using the UnstructuredPDFLoader to extract text content.

2) Text Preprocessing:
The extracted text is split into smaller chunks using the RecursiveCharacterTextSplitter to optimize document retrieval and vector embedding.

3) Embedding Creation:
Each text chunk is converted into vector embeddings using the Ollama Embeddings model (nomic-embed-text). These embeddings are stored in a Chroma vector store for efficient search and retrieval.

4) Query Retrieval:
When a user submits a query, the MultiQueryRetriever generates multiple variations of the question. This ensures better search results by overcoming the limitations of keyword-based searches. The retriever fetches the most relevant chunks from the vector store.

5) Answer Generation:
The retrieved context is passed to the Mistral language model to generate a contextual answer. The answer is generated based on the specific content from the document, ensuring an accurate and relevant response.

6) Final Answer:
The system outputs a response based solely on the document’s content, providing a contextually grounded answer to the user’s question.
