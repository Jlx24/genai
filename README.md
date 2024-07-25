# GENAI

## 1. Understanding Embeddings

### 1.1 How to Do Embeddings (Embedding_hf)
- Embedding with all-MiniLM-L6-v2 (Hugging Face pipeline)

### 1.2 Host Embeddings for Free on the Hugging Face Hub (1_Embedding_hf)

### 1.3 Get the Most Similar Frequently Asked Questions to a Query

## 2. Advanced Embeddings

### 2.1 Word Embeddings with Transformers

### 2.2 Sentence Embeddings

### 2.3 Sentence Transformers
- Using the transformers library
- Using the sentence-transformers library
- Embedding dimensions
- Sequence length

#### DEMO 1: Finding the Most Similar Quora Duplicate

### 2.4 Distance Between Embeddings
- Cosine similarity
- Dot product
- Euclidean distance
- Picking a score function

### 2.5 Scaling Up
In practice, you might have to deal with millions of embeddings, and we cannot always compute the distance to all of them (this is called brute-force search).

#### DEMO 2: Paraphrase Mining

### 2.6 Selecting and Evaluating Models

## 3. Advanced RAG

### 3.1 Retriever - Embeddings

### 3.2 Building the Vector Database
- Nearest neighbor search algorithm
- Distances

### 3.3 Reader Model LLM
The choice of a reader model is important in a few aspects:
- The reader model's `max_seq_length` must accommodate our prompt, which includes the context output by the retriever call: the context consists of 5 documents of 512 tokens each, so we aim for a context length of 4k tokens at least.
- The reader model

#### Prompt
The RAG prompt template below is what we will feed to the Reader LLM: it is important to have it formatted in the Reader LLM's chat template.
We give it our context and the user's question.

#### Reranking
A good option for RAG is to retrieve more documents than you want in the end, then rerank the results with a more powerful retrieval model before keeping only the `top_k`.
