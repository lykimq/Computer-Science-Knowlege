# AI Engineer

## Core LLM Elements

![Core LLM Elements](pics/Mastering_Large_Language_Model_Parameters.png)


### Tokens
A token is the smallest unit of text an LLM processes. A token can be a full word, part of a word (subword), or a single character.
Because the model predicts the next token in a sequence, tokens directly affect:
- API cost (usually calculated from input and output tokens)
- Processing speed
- Context window limits (the maximum number of tokens the model can read at once)

### Context
Context is all information the model can see before it generates a response.
Context commonly includes:
- The current user query
- System instructions or prompt
- Previous conversation turns
- Supporting materials (RAG content, attached files, related data)

The clearer and more relevant the context is, the more accurate and coherent the response tends to be.

### Sampling Parameters
Sampling parameters are settings that control how the model chooses the next token.
They influence the balance between:
- Stability and creativity
- Safety and risk-taking
- Consistency and diversity

### Temperature
Temperature controls how random text generation is.
- Low temperature (for example, 0.1-0.3): stable output with less deviation, useful for tasks that require high accuracy
- Medium temperature (0.4-0.8): a balance between accuracy and natural variation
- High temperature (0.9+): more creative output, but more likely to drift and become less consistent

Practical tip: if you need safer and more predictable answers, lower temperature before tuning other parameters.

### Top-K
Top-K allows the model to choose the next token only from the K most likely options.
- Smaller K: more conservative choices, fewer surprises
- Larger K: more options, more diverse responses

Examples:
- K = 1 is similar to greedy decoding (always picks the highest-probability token)
- K = 40 often produces more natural results than K = 1

### Top-P (Nucleus Sampling)
Top-P does not use a fixed number of tokens like Top-K.
Instead, the model selects the smallest set of tokens whose cumulative probability is at least P.
- Low P (for example, 0.3-0.5): narrow token set, focused and stable output
- Medium P (0.8-0.9): good balance for many use cases
- High P (0.95-0.99): wider token set, more creativity, but potentially lower accuracy

Key difference:
- Top-K limits by a fixed number of tokens
- Top-P limits by cumulative probability, so it adapts more flexibly to each context

### Repetition Penalties
Repetition penalties help reduce repeated words or phrases during generation.

Two common types:
- Frequency penalty: the more often a token appears, the stronger the penalty
- Presence penalty: once a token has appeared, it gets penalized regardless of how many times it appears

Effects:
- Reduces repeated ideas
- Increases language diversity
- Can make text sound unnatural if penalties are too strong

## Common Terminology

![Common Terminology](pics/Building_Blocks_of_Modern_AI.png)

### Embeddings
Embeddings are dense, continuous vector representations of data, such as words, sentences, or images, in a lower-dimensional space. 

They capture the semantic relationships and patterns in the data, where similar items are placed closer together in the vector space. 

In machine learning, embeddings are used to convert complex data into a numerical form that models can process more easily. 

For example, word embeddings represent words based on their meanings and contexts, allowing models to understand relationships like synonyms or analogies. 

Embeddings are widely used in tasks like natural language processing, recommendation systems, and image recognition to improve model performance and efficiency.

### Vector DB

Vector databases are specialized systems designed to store, index, and retrieve high-dimensional vectors, often used as embeddings that represent data like text, images, or audio. 

Unlike traditional databases that handle structured data, vector databases excel at managing unstructured data by enabling fast similarity searches, where vectors are compared to find those that are most similar to a query. 

This makes them essential for tasks like semantic search, recommendation systems, and content discovery, where understanding relationships between items is crucial. 

Vector databases use indexing techniques such as approximate nearest neighbor (ANN) search to efficiently handle large datasets, ensuring quick and accurate retrieval even at scale.

### RAG

Retrieval-Augmented Generation (RAG) is an AI approach that combines information retrieval with language generation to create more accurate, contextually relevant outputs. 

It works by first retrieving relevant data from a knowledge base or external source, then using a language model to generate a response based on that information. T

his method enhances the accuracy of generative models by grounding their outputs in real-world data, making RAG ideal for tasks like question answering, summarization, and chatbots that require reliable, up-to-date information.

![Embeddings-VectorDB-RAG](pics/Building_Blocks_of_Semantic_Intelligence.png)

### Inference

In AI, inference refers to the process by which a trained machine learning model makes predictions or draws conclusions from new, unseen data. 

Unlike training, inference involves the model applying what it has learned to make decisions without needing examples of the exact result. 

In essence, inference is the AI model actively functioning. 

For example, a self-driving car recognizing a stop sign on a road it has never encountered before demonstrates inference. The model identifies the stop sign in a new setting, using its learned knowledge to make a decision in real-time.


### Fine-tuning
Fine-tuning involves taking a pre-trained LLM and further training it on a smaller, task-specific dataset. 

This adapts the LLM to perform better on a particular task or domain. 

However, fine-tuning can be resource-intensive and may not always be the most efficient approach. 

Prompt engineering, retrieval-augmented generation (RAG), or using smaller, specialized models can sometimes achieve comparable or even better results with less computational overhead and data requirements.

## Use Cases For Embeddings

![Use Cases For Embeddings](pics/Core_Applications_of_Vector_Embeddings.png)

### Semantic Search
Embeddings are used for semantic search by converting text, such as queries and documents, into high-dimensional vectors that capture the underlying meaning and context, rather than just exact words. 

These embeddings represent the semantic relationships between words or phrases, allowing the system to understand the query’s intent and retrieve relevant information, even if the exact terms don’t match.

### Data Classification

Once data is embedded, a classification algorithm, such as a neural network or a logistic regression model, can be trained on these embeddings to classify the data into different categories. 

The advantage of using embeddings is that they capture underlying relationships and similarities between data points, even if the raw data is complex or high-dimensional, improving classification accuracy in tasks like text classification, image categorization, and recommendation systems.

### Recommendation Systems

In the context of embeddings, recommendation systems use vector representations to capture similarities between items, such as products or content. 

By converting items and user preferences into embeddings, these systems can measure how closely related different items are based on vector proximity, allowing them to recommend similar products or content based on a user's past interactions. 

This approach improves recommendation accuracy and efficiency by enabling meaningful, scalable comparisons of complex data.

### Anomally Detection
Anomaly detection with embeddings works by transforming data, such as text, images, or time-series data, into vector representations that capture their patterns and relationships. 

In this high-dimensional space, similar data points are positioned close together, while anomalies stand out as those that deviate significantly from the typical distribution. 

This approach is highly effective for detecting outliers in tasks like fraud detection, network security, and quality control.

## Embedding Models

### Proprietary Models
- Open AI Embeddings API
- Gemini Embedding
- Cohere

### Open Source Models
- Sentence Transformers
- Models on Hugging Face
- Jina

## Vector Databases

Purpose and Functionality

### Popular Vector DBs
- Chroma
- Pinecone
- Weaviate
- FAISS
- LanceDB
- Qdrant
- Supabase
- MongoDB Atlas

### Implementing Vector Search
- Indexing Embeddings
- Performaing Similarity Search

## RAG

### Implementing RAG
1. Chunking
2. Embedding
3. Vector DB
4. Retrieval Process 
5. Generation

### Ways of Implementing RAG
1. Using SDKs Directly
2. LangChain
3. Llama Index
4. Haystack
5/ RAGFlow
