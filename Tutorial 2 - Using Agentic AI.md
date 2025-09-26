# TUTORIAL 2 - USING AGENTIC AI

1. Create a new project folder.
2. Open VS Code and open Terminal.
3. Open Gemini CLI by typing:

```
gemini
```

4. Check your MCP servers by typing:

```
/mcp
```

* You should see a result similar to this example:

```
ℹ Configured MCP servers:
 
  🟢 context7 - Ready (2 tools)
    - resolve-library-id
    - get-library-docs

  🟢 sequential-thinking - Ready (1 tools)
    - sequentialthinking

  🟢 zen - Ready (16 tools)
    - chat
    - thinkdeep
    - planner
    - consensus
    - codereview
    - precommit
    - debug
    - secaudit
    - docgen
    - analyze
    - refactor
    - tracer
    - testgen
    - challenge
    - listmodels
    - version

```
5. Check your LLM configuration by typing:

```
/listmodels
```

* You should see a result similar to this example:

```
✦ Available AI Models

  Google Gemini ❌
  Status: Not configured (set GEMINI_API_KEY)

  OpenAI ❌
  Status: Not configured (set OPENAI_API_KEY)

  X.AI (Grok) ❌
  Status: Not configured (set XAI_API_KEY)

  AI DIAL ❌
  Status: Not configured (set DIAL_API_KEY)

  OpenRouter ✅
  Status: Configured and available
  Description: Access to multiple cloud AI providers via unified API

  Available Models:

  Anthropic:
   - anthropic/claude-opus-4 → anthropic/claude-opus-4 (200K context)
   - anthropic/claude-sonnet-4 → anthropic/claude-sonnet-4 (200K context)
   - anthropic/claude-3.5-haiku → anthropic/claude-3.5-haiku (200K context)

  Deepseek:
   - deepseek/deepseek-r1-0528 → deepseek/deepseek-r1-0528 (65K context)

  Google:
   - google/gemini-2.5-pro → google/gemini-2.5-pro (1048K context)
   - google/gemini-2.5-flash → google/gemini-2.5-flash (1048K context)

  Meta-Llama:
   - meta-llama/llama-3-70b → meta-llama/llama-3-70b (8K context)

  Mistralai:
   - mistralai/mistral-large-2411 → mistralai/mistral-large-2411 (128K context)

  Openai:
   - openai/o3 → openai/o3 (200K context)
   - openai/o3-mini → openai/o3-mini (200K context)
   - openai/o3-mini-high → openai/o3-mini-high (200K context)
   - openai/o3-pro → openai/o3-pro (200K context)
   - openai/o4-mini → openai/o4-mini (200K context)

  Other:
   - llama3.2 → llama3.2 (128K context)

  Perplexity:
   - perplexity/llama-3-sonar-large-32k-online → perplexity/llama-3-sonar-large-32k-online (32K context)

  Custom/Local API ✅
  Status: Configured and available
  Endpoint: https://openrouter.ai/api/v1
  Description: Local models via Ollama, vLLM, LM Studio, etc.

  Custom Models:
   - local-llama → llama3.2 (128K context)
     - Local Llama 3.2 model via custom endpoint (Ollama/vLLM) - 128K context window (text-only)
   - local → llama3.2 (128K context)
     - Local Llama 3.2 model via custom endpoint (Ollama/vLLM) - 128K context window (text-only)
   - llama3.2 → llama3.2 (128K context)
     - Local Llama 3.2 model via custom endpoint (Ollama/vLLM) - 128K context window (text-only)
   - ollama-llama → llama3.2 (128K context)
     - Local Llama 3.2 model via custom endpoint (Ollama/vLLM) - 128K context window (text-only)

  Summary
  Configured Providers: 2
  Total Available Models: 18

  Usage Tips:
   - Use model aliases (e.g., 'flash', 'gpt5', 'opus') for convenience
   - In auto mode, the CLI Agent will select the best model for each task
   - Custom models are only available when CUSTOM_API_URL is set
   - OpenRouter provides access to many cloud models with one API key

╭────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╮
│ You are running Gemini CLI in your home directory. It is recommended to run in a project-specific directory.                                                                               │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
```