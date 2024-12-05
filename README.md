# Conversational RAG for Real Estate Queries

## Overview
This repository contains a Jupyter notebook implementation of a specialized conversational agent for handling real estate queries in Israel. The agent uses LangChain with Google's Gemini Pro model to provide contextual responses while maintaining user-specific memory management.

## Features
- **Selective Memory**: Remembers user information only when explicitly requested
- **Context-Aware Responses**: Uses chat history to provide more accurate and contextual answers
- **Domain-Specific**: Specialized in answering questions about apartments for sale in Israel
- **User Privacy**: Maintains separate conversation histories for different users
- **Document Retrieval**: Utilizes ChromaDB for efficient document storage and retrieval

## Prerequisites
- Python 3.x
- Google API Key (for Gemini Pro access)

## Required Packages
```bash
pip install langchain_google_genai langchain-community langchain_chroma pypdf
```

## Project Structure
The notebook is organized into several key sections:
1. Installation and Imports
2. Retriever Construction
3. Question Contextualization
4. Answer Generation
5. Chat History Management
6. Testing and Examples

## Key Components
- **SelectiveChatMessageHistory**: Custom class that only stores messages containing the "remember" keyword
- **Retrieval Chain**: Combines document retrieval with conversation history
- **Session Management**: Maintains separate conversation histories for different users

## Usage Example
```python
# Initialize the chain with a user session
response = conversational_rag_chain.invoke(
    {"input": "My name is John and I live in Tel Aviv, please remember that."},
    config={"configurable": {"session_id": "user123"}}
)

# Make queries
response = conversational_rag_chain.invoke(
    {"input": "What is my city?"},
    config={"configurable": {"session_id": "user123"}}
)
```

## Features and Limitations
### Features
- Maintains user privacy by separating conversation histories
- Only remembers information when explicitly requested
- Focuses exclusively on real estate queries in Israel
- Provides concise, three-sentence maximum responses

### Limitations
- Requires explicit "remember" keyword for memory retention
- Only handles queries related to Israeli real estate
- Requires valid Google API key for operation

