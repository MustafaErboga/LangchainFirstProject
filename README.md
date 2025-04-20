# Simple LangChain Translation API

A basic web API for text translation using LangChain, FastAPI, LangServe, and an OpenAI model.

## Features

*   Translates text to a specified language.
*   Uses a LangChain `Runnable` chain (Prompt | Model | Parser).
*   Served via FastAPI and LangServe.
*   Securely loads API keys with `python-dotenv`.

## Prerequisites

*   Python 3.8+
*   OpenAI API Key

## Quick Start

1.  **Clone the repository:**
    ```bash
    git clone <your_github_repo_url>
    cd <your_project_directory_name>
    ```
    *(Replace with your actual URL and directory name)*

2.  **Setup Environment & Install Dependencies:**
    ```bash
    python -m venv .venv
    # Activate virtual environment (see full setup for OS-specific commands)
    # On Windows: .\.venv\Scripts\activate
    # On macOS/Linux: source .venv/bin/activate
    pip install -r requirements.txt
    ```

3.  **Configure API Key:**
    *   Copy `.env.example` to `.env`.
    *   Add your OpenAI API key to the `.env` file:
        ```dotenv
        OPENAI_API_KEY="your-openai-api-key"
        ```

4.  **Run the Server:**
    ```bash
    python serve.py
    ```
    The API will be available at `http://localhost:8000`.

## API Usage

*   **Docs:** `http://localhost:8000/docs` (Swagger UI)
*   **Invoke Translation:** Send a POST request to `/chain/invoke`:
    ```bash
    curl -X POST http://localhost:8000/chain/invoke \
    -H "Content-Type: application/json" \
    -d '{
      "input": {
        "language": "german",
        "text": "hello world"
      }
    }'
    ```

## Key Files

*   `serve.py`: Main application script (FastAPI, LangServe, LangChain chain).
*   `requirements.txt`: Project dependencies.
*   `.env`: Stores your OpenAI API key (created locally, **not committed to Git**).
*   `.env.example`: Template for the `.env` file.
*   `.gitignore`: Specifies files Git should ignore (like `.env`, `.venv/`).
