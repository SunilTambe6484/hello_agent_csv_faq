# Hello Agent — CSV FAQ Agent

A Week 0 mini-project implementation based on the supplied assignment PDF.

## What it does

- Upload one or multiple CSV files.
- Preview the first eight rows of each file.
- Ask questions in natural language.
- Use Pandas + a LangChain DataFrame agent + OpenAI GPT-4o mini.
- Follow a data-only prompt: when the answer is not present, the expected response is:
  `I could not find this information in the uploaded files.`

## Technology

- Python 3.11+
- Streamlit
- Pandas
- LangChain
- `langchain-experimental` Pandas DataFrame agent
- `langchain-openai`
- OpenAI GPT-4o mini

## Project structure

```text
hello_agent_csv_faq/
├── app.py
├── requirements.txt
├── README.md
├── .env.example
└── sample_data/
    ├── ecommerce_faqs.csv
    ├── credit_card_terms.csv
    ├── hospital_policy.csv
    └── saas_docs.csv
```

## Run on Windows (PowerShell)

1. Install Python 3.11 or newer.
2. Extract the ZIP and open the `hello_agent_csv_faq` folder in VS Code.
3. Create and activate a virtual environment:

```powershell
py -3.11 -m venv .venv
.\.venv\Scripts\Activate.ps1
```

4. Install dependencies:

```powershell
python -m pip install --upgrade pip
pip install -r requirements.txt
```

5. Start the app:

```powershell
streamlit run app.py
```

6. Open the local URL printed by Streamlit (usually `http://localhost:8501`).
7. Enter your OpenAI API key in the sidebar.
8. Upload one or more CSV files from `sample_data`.
9. Ask one of the example questions.

## Suggested test questions

- What is the return policy for electronics?
- What does the extended warranty cover?
- What are the hospital visiting hours?
- What is the API rate limit for the free plan?
- What is the annual fee for the Gold card?
- What is the hospital parking policy?

Also test a question that is not covered by the uploaded files. The agent should reply:
`I could not find this information in the uploaded files.`

## API key

The app accepts the key through a password field in the sidebar. It is not written to a file by this application. Never commit API keys to GitHub. You need an OpenAI API account with API access and available billing/credits; a ChatGPT subscription is not the same as API billing.

You may alternatively configure `OPENAI_API_KEY` in your local environment, but this starter app intentionally uses the sidebar input.

## Important security note

The assignment specifically asks for a LangChain Pandas DataFrame agent. This agent uses a Python REPL tool and therefore can execute generated Python code. `allow_dangerous_code=True` is required by LangChain for this feature.

This project is intended as a local learning exercise. Do not deploy it as a public multi-user service or upload confidential/untrusted data without isolating the Python execution in a properly restricted sandbox, applying authentication and resource limits, and conducting a security review. The prompt is a behavior instruction, not a security boundary; no LLM prompt can guarantee zero hallucinations or fully prevent prompt injection.

## Notes

The sample CSVs are illustrative demo data created for testing. They are not official terms, medical policies, or legal advice. Replace them with the CSV files supplied by your course if available.
