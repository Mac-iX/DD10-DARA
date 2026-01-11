# Quick Start Guide

## Test the Agent Locally (Without API Key)

If you want to test the structure without making API calls:

1. Install dependencies:
```bash
npm install
```

2. Review the code structure:
```bash
ls -R core/ interface/ docs/
```

3. Check the prompt templates:
```bash
cat docs/DARA.md | head -50
```

## Test with OpenAI API

### Step 1: Set up your environment

```bash
cp .env.example .env
nano .env  # Add your OPENAI_API_KEY
```

### Step 2: Run the CLI

```bash
npm start
```

### Step 3: Try DARA Mode

When prompted:
- Select: "Run DARA Mode"
- Topic: "Electric vehicle adoption"
- Region: "California"

The agent will execute all 5 DARA modules and generate a complete research report.

### Step 4: Check the output

```bash
ls -lh logs/
cat logs/report_*.md
```

## Understanding the Flow

1. **CLI** (`interface/cli.js`) - User interaction
2. **Router** (`core/agent_router.js`) - Determines mode and validates input
3. **Prompt Engine** (`core/prompt_engine.js`) - Loads and assembles prompts from docs
4. **Executor** (`core/executor.js`) - Sends prompts to OpenAI and gets responses
5. **Parser** (`core/response_parser.js`) - Formats and saves results

## Troubleshooting

### "Cannot find module"
Run `npm install` to install all dependencies.

### "API key not found"
Make sure you created `.env` and added your `OPENAI_API_KEY`.

### "Module prompt not found"
The prompt engine looks for specific headers in the docs. Make sure `docs/DARA.md` and `docs/DeepSpec_Prompt_Library.md` are present.

## Next Steps

- Review test cases in `tests/agent_test_cases.md`
- Customize prompts in `docs/` folder
- Modify the CLI interface in `interface/cli.js`
- Add new modules by extending the router and prompt engine
