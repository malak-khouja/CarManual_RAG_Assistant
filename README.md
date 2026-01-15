# CarManual_RAG_Assistant

A proof-of-concept implementation of a Retrieval Augmented Generation (RAG) chatbot designed to provide context-aware answers about car warning messages from technical manuals.

## Overview

This project demonstrates how to integrate Large Language Models (LLMs) with car manual documentation to create an intelligent assistant that can answer driver questions about warning messages. The system uses RAG to ensure accurate, context-grounded responses that could be integrated with text-to-speech systems for in-vehicle use.

## Features

- 🚗 **Domain-Specific Knowledge**: Trained on MG ZS automobile warning messages
- 🔍 **Semantic Search**: Uses vector embeddings for intelligent document retrieval
- 💬 **Concise Responses**: Provides clear, actionable answers in 3 sentences or less
- 🎯 **Context-Aware**: Only answers based on retrieved manual content

## Technical Stack

- **LLM**: OpenAI GPT-4o-mini
- **Embeddings**: OpenAI text-embedding-3-small
- **Vector Database**: ChromaDB
- **Framework**: LangChain
- **Document Processing**: UnstructuredHTMLLoader

## Project Structure

```
.
├── notebook.ipynb                      # Main implementation notebook
├── data/
│   └── mg-zs-warning-messages.html    # Car manual source data
├── images/
│   └── dashboard.jpg                   # Project assets
└── README.md                           # This file
```

## Installation

1. Install required packages:

```python
pip install langchain-core==0.3.72
pip install langchain-openai==0.3.28
pip install langchain-community==0.3.27
pip install unstructured==0.18.11
pip install langchain-chroma==0.2.5
pip install langchain-text-splitters==0.3.9
pip install pydantic==2.11.9
```

2. Set up your OpenAI API key:

```python
import os
os.environ["OPENAI_API_KEY"] = "your-api-key-here"
```

## Usage

Open `notebook.ipynb` and run the cells sequentially to:

1. Load the car manual HTML file
2. Initialize the LLM and embedding models
3. Split the document into chunks
4. Create a vector store for semantic search
5. Build the RAG pipeline
6. Query the chatbot with questions

Example query:
```python
answer = rag_chain.invoke("The Gasoline Particular Filter Full warning has appeared. What does this mean and what should I do about it?")
print(answer.content)
```

## How It Works

1. **Document Loading**: The HTML car manual is loaded and parsed
2. **Text Splitting**: Content is split into 1000-character chunks with 200-character overlap
3. **Embedding**: Chunks are converted to vector embeddings and stored in ChromaDB
4. **Retrieval**: User questions trigger semantic search for relevant chunks
5. **Generation**: The LLM generates answers using only the retrieved context

## RAG Pipeline

```
User Question → Retriever → Relevant Context → Prompt Template → LLM → Answer
```

## Future Enhancements

- Integration with text-to-speech for voice responses
- Support for multiple vehicle models and manuals
- Real-time warning message detection
- Multi-language support
- Voice input for hands-free operation

## License

This is a demonstration project for educational purposes.

## Acknowledgments

- Car manual data from MG ZS automobile documentation
- Built with LangChain and OpenAI APIs
