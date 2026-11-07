# ResumeGuru

A small Streamlit app that reads a text-based resume PDF and runs a one-question-at-a-time mock interview with Google Gemini.

## 1. Install Python

Use Python 3.10 or newer. Open a terminal in this folder and create a virtual environment:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

If PowerShell blocks activation, run `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` in that terminal, then activate again.

## 2. Get a Gemini API key

Create one Gemini API key in Google AI Studio. You do not need to create a new key each time you use the app. Paste it into the password field in the sidebar and click **Save key on this device**. ResumeGuru stores it locally in `.streamlit/secrets.toml` and loads it the next time you open the app. That secrets file is ignored by Git and must never be committed or shared.

Alternatively, set `GEMINI_API_KEY` in your environment before starting the app. If a key has been exposed in a chat, screenshot, or public repository, revoke it in Google Cloud and save a new key locally.

## 3. Start the app

```powershell
streamlit run app.py
```

Upload a selectable-text PDF, choose Technical, HR, or DSA mode and a difficulty, then select **Start interview**. Answer each question to see a score, feedback, an example stronger answer, and the next question.

## Notes

- Scanned/image-only PDFs need OCR; this starter app reports when no selectable text is found.
- Resume text is sent to Gemini when a question is generated or an answer is reviewed. Do not upload sensitive information.
- The model's score and feedback are practice guidance, not an objective hiring assessment.
