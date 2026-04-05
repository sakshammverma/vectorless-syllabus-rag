# Vectorless Syllabus RAG 

This is a quick proof-of-concept for a "vectorless" RAG pipeline. It's built to chat with a complex B.Tech syllabus without having to set up a traditional vector database or deal with messy text chunking. 

### How it works
Instead of using embeddings and cosine similarity, this relies on the actual document structure:
1. **Parse:** Uses `pageindex` to turn the PDF into a hierarchical tree (essentially a smart Table of Contents).
2. **Route:** Feeds the compressed tree and the user's query to Gemini 2.5 Flash. The LLM thinks step-by-step, and picks the exact node IDs that contain the answer.
3. **Retrieve:** Grabs the specific text from those selected nodes.
4. **Generate:** Passes that specific text context back to the LLM alongside the original query to generate the final answer.

### Setup
Just install the basics and set up your `.env` file:
Get your Gemini API key from here [Google AI Studio](https://aistudio.google.com/app/api-keys?project=gen-lang-client-0870781791)
Get your PageIndex API Key from here [PageIndex API](https://dash.pageindex.ai/api-keys)

` ` `bash
pip install -U pageindex google-genai python-dotenv
` ` `

### Current Status
This project is currently an experimental **Proof of Concept (PoC)**.
