# LangChain Output Parsers

A hands-on learning project exploring the different output parsers available in LangChain. Each script demonstrates a specific parser type using real LLM providers (HuggingFace and OpenAI).

## What are Output Parsers?

Output parsers in LangChain take raw LLM text responses and convert them into structured, usable Python objects — strings, dicts, JSON, or typed Pydantic models.

## Project Structure

| File | Parser | Description |
|------|--------|-------------|
| `str_output_parser.py` | None (baseline) | Two-step chaining without a parser — manual prompt chaining |
| `str_output_parser1.py` | `StrOutputParser` | Same two-step chain refactored using `StrOutputParser` and `RunnableLambda` |
| `jsonOutputparser.py` | `JsonOutputParser` | Generates a fictional person's details as a parsed JSON dict |
| `structuredoutputparser.py` | `StructuredOutputParser` | Extracts 3 structured facts about a topic using `ResponseSchema` |
| `pydanticoutputparser.py` | `PydanticOutputParser` | Returns a validated `Person` Pydantic model with name, age, and city |

## Key Concepts Covered

- **`StrOutputParser`** — Strips the raw `AIMessage` wrapper and returns plain text. Used to connect chained prompts cleanly.
- **`JsonOutputParser`** — Instructs the LLM to respond in JSON and parses the output into a Python dict.
- **`StructuredOutputParser`** — Defines an explicit response schema using `ResponseSchema` objects; good for fixed multi-field outputs.
- **`PydanticOutputParser`** — Parses LLM output into a typed Pydantic model with field validation (e.g., `age > 18`).

## LLM Providers Used

- **HuggingFace** (`TinyLlama/TinyLlama-1.1B-Chat-v1.0` via Featherless AI) — used in most examples
- **OpenAI** (`ChatOpenAI`) — used in the Pydantic parser example

## Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/langchain-output-parsers.git
   cd langchain-output-parsers
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file with your API keys:
   ```
   HUGGINGFACEHUB_API_TOKEN=your_huggingface_token
   OPENAI_API_KEY=your_openai_key
   ```

## Running the Examples

```bash
python str_output_parser.py       # Baseline: manual chaining
python str_output_parser1.py      # StrOutputParser with LCEL chain
python jsonOutputparser.py        # JsonOutputParser
python structuredoutputparser.py  # StructuredOutputParser
python pydanticoutputparser.py    # PydanticOutputParser
```

## Learning Path

If you're new to LangChain output parsers, go through the files in this order:

1. `str_output_parser.py` — understand the problem (raw model output)
2. `str_output_parser1.py` — see how `StrOutputParser` cleans it up in a chain
3. `jsonOutputparser.py` — structured output as a dict
4. `structuredoutputparser.py` — schema-defined structured output
5. `pydanticoutputparser.py` — fully typed and validated output
