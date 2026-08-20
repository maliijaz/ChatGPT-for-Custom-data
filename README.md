# ChatGPT-for-Custom-data

A small command-line script that lets you ask questions about your own PDF/text documents using ChatGPT, via LangChain's document loaders and a vector index.

## How it works

`chatgpt.py`:
1. Loads a document with LangChain's `PyPDFLoader` (a `TextLoader` import is also available for plain text files).
2. Builds a searchable vector index over the document with `VectorstoreIndexCreator`.
3. Takes a query from the command line and runs it against the index using `ChatOpenAI` as the answering LLM, printing the response.

## Project structure

- `chatgpt.py` — main script: loads the document, builds the index, and answers a query.
- `constants.py` — holds the `APIKEY` variable used to set the `OPENAI_API_KEY` environment variable.
- `requirements.txt` — Python dependencies.

## Requirements

```
langchain
openai
chromadb
tiktoken
unstructured
pypdf
```

## Setup

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Open `constants.py` and replace the placeholder with your own OpenAI API key:
   ```python
   APIKEY = "your-openai-api-key"
   ```
3. In `chatgpt.py`, update the hardcoded file path passed to `PyPDFLoader(...)` to point at your own PDF.

## Usage

```bash
python chatgpt.py "Your question about the document"
```

The script prints the model's answer, generated from content retrieved out of the indexed document.

## Notes

- The document path and API key are currently hardcoded for local/demo use — update them before running on a different machine.
- This is a minimal example; no error handling or CLI argument parsing beyond `sys.argv[1]` is included.
