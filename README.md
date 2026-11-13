# StatBuddy — Streamlit app

A Streamlit version of your SPSS Statistical Test Selector chatbot.

## 1. Requirements

- Python 3.9 or newer
- A Groq API key with access to `openai/gpt-oss-120b`

## 2. Install

Unzip the package, open a terminal in the `StatBuddy_Streamlit` folder, then run:

```bash
python -m venv .venv

# macOS / Linux
source .venv/bin/activate

# Windows PowerShell
# .venv\\Scripts\\Activate.ps1

pip install -r requirements.txt
```

## 3. Configure the API key

Open `.streamlit/secrets.toml` and replace the placeholder:

```toml
GROQ_API_KEY = "YOUR_GROQ_API_KEY_HERE"
```

with your actual Groq API key. Get one at https://console.groq.com/keys.

**Keep this file private. Do not upload it to GitHub or share it.** The included `.gitignore` excludes it from Git.

## 4. Run the app

```bash
streamlit run app.py
```

Streamlit will open StatBuddy in your browser.

## Notes

- The app uses the Groq Python SDK because the original code calls the Groq-compatible `client.chat.completions.create()` interface and specifies the `openai/gpt-oss-120b` model. The original `google.genai` import was therefore mismatched and has been replaced.
- The chatbot answers only from the SPSS manual embedded in `app.py`.
- Conversation history is stored in Streamlit session state and limited to the last 12 messages.
- Use **Clear chat** in the sidebar to reset the conversation.
- The API key is loaded from `.streamlit/secrets.toml`; it is not hard-coded in `app.py`.
