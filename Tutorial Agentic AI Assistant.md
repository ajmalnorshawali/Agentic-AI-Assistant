[[_TOC_]]

# Latihan - Agentic AI Assistant

## What is Agentic AI?

1. Agentic AI is an AI that acts **autonomously** to achieve goals.

2. Key Characteristics:

- **Autonomy**: Makes decisions independently.
- **Goal-Driven**: Sets, plans, and pursues complex objectives.
- **Adaptability**: Learns and refines strategies over time.
- **Tool Utilization**: Leverages LLMs for reasoning; interacts with external tools (APIs, databases).
- **Orchestration**: Manages multi-step, end-to-end workflows.

3. Think of it this way: If generative AI creates, agentic AI does.

## Prerequisites

To get started, you'll need the following:

1. **Visual Studio Code (VS Code)**: Ensure you have the latest version installed on your machine.

2. **LLM Models**:
- **Ollama**: A powerful tool for running large language models locally on your machine.
  - **Model**: Use the `qwen3` LLM model.
  - **Installation**: See the [Local LLM using Ollama guide](https://code.cloud-connect.asia/researchproject/ai/applied-ai/-/blob/main/Latihan%20-%20Local%20LLM.md#local-llm-using-ollama). 

  _or_

- **Openrouter.AI subscription** 
  - **Subscription**: See the [OpenRouter.ai configuration guide](https://code.cloud-connect.asia/researchproject/ai/applied-ai/-/blob/main/Latihan%20Konfigurasi%20Roo%20Code.md#step-21-register-and-configure-openrouter-llm-provider).

3. **Gemini CLI**: 
- **Installation**: See the [Gemini CLI guide](https://code.cloud-connect.asia/researchproject/ai/applied-ai/-/blob/main/Latihan%20-%20Gemini%20CLI.md). 


# Environment Readiness

## Install uvx

1. Go to the [official uvx installation website](https://docs.astral.sh/uv/getting-started/installation/).
2. Follow the instructions to install it on your machine.

## Configure Context7 MCP and Zen MCP

* **Context7 MCP**: https://context7.com/
* **Zen MCP**: https://github.com/BeehiveInnovations/zen-mcp-server.git

1. Open the **.gemini** folder in your project's root directory.
2. Edit the **settings.json** file and add the following configuration for `mcpServers`.

### **Configure LLM Ollama in Gemini CLI**

* **settings.json** file for **Linux**:
```
"mcpServers": {
    "context7": {
      "command": "npx",
      "args": [
        "-y",
        "@upstash/context7-mcp"
      ]
    },
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-sequential-thinking"
      ]
    },
    "zen": {
      "command": "sh",
      "args": [
        "-c",
        "exec $(which uvx || echo uvx) --from git+https://github.com/BeehiveInnovations/zen-mcp-server.git zen-mcp-server"
      ],
      "env": {
        "PATH": "/usr/local/bin:/usr/bin:/bin:/opt/homebrew/bin:~/.local/bin",
        "DEFAULT_MODEL": "llama3.2:3b",
        "CUSTOM_API_URL": "http://127.0.0.1:11434/v1",
        "CUSTOM_API_KEY": "",
        "CUSTOM_MODEL_NAME": "llama3.2:3b"
      }
    }
  },
```

* **settings.json** file for **Windows**:
```
"mcpServers": {
    "context7": {
      "command": "npx",
      "args": [
        "-y",
        "@upstash/context7-mcp"
      ]
    },
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-sequential-thinking"
      ]
    },
    "zen": {
      "command": "cmd",
      "args": [
        "/c",
        "uvx --from git+https://github.com/BeehiveInnovations/zen-mcp-server.git zen-mcp-server"
      ],
      "env": {
        "DEFAULT_MODEL": "llama3.2:3b",
        "CUSTOM_API_URL": "http://127.0.0.1:11434/v1",
        "CUSTOM_API_KEY": "",
        "CUSTOM_MODEL_NAME": "llama3.2:3b"
      }
    }
  },
"preferredEditor": "vscode"
```

### **Configure OpenRouter.ai Subscription in Gemini CLI**

#### Step 1: Create an API key in OpenRouter

1. **Sign up** for an **OpenRouter account**. Register at [openrouter.ai](openrouter.ai).
2. Once registered, at the OpenRouter dashboard, click your **avatar** icon, and select **Setting** from the dropdown menu.
3. Select **API Keys** from the left menu.
4. Click **Create API Key**, enter i.e., **AI code** for Name, and click **Create**.
5. **Copy** the **API key** and save it for future use.

_Note: See the [OpenRouter.ai configuration guide](https://code.cloud-connect.asia/researchproject/ai/applied-ai/-/blob/main/Latihan%20Konfigurasi%20Roo%20Code.md#step-21-register-and-configure-openrouter-llm-provider) for more details._

#### Step 2: Configure the API key in local environment variables

**For Linux/macOS:**

1. Open your terminal.
2. Add the following line to your shell's profile file (e.g., `~/.bashrc`, `~/.zshrc`, or `~/.profile`).

```
export OPENROUTER_API_KEY="sk-or-v1-apikey"
```

3. **Source the file** or **restart your terminal** for the changes to take effect.

```
source ~/.zshrc # or whatever file you edited
```

**For Windows:**

1. Open the **Start** menu and search for **"Edit the system environment variables"**.
2. Click on **"Environment Variables..."**.
3. In the **"User variables for [Your Username]"** section, click **"New..."**.
4. For **"Variable name"**, enter OPENROUTER_API_KEY.
5. For **"Variable value"**, paste your actual OpenRouter API key (sk-or-v1-apikey).
6. Click **"OK"** on all windows to save the changes.
7. **Important:** Restart your command prompt or terminal for the new environment variable to take effect.

#### Step 3: Configure the API key in `setting.json`

* **settings.json** file for **Linux/macOS**:
```
"mcpServers": {
    "context7": {
      "command": "npx",
      "args": [
        "-y",
        "@upstash/context7-mcp"
      ]
    },
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-sequential-thinking"
      ]
    },
    "openrouter": {
      "command": "sh",
      "args": [
        "-c",
        "exec $(which uvx || echo uvx) --from git+https://github.com/BeehiveInnovations/zen-mcp-server.git zen-mcp-server"
      ],
      "env": {
        "OPENROUTER_API_KEY": "YOUR_OPENROUTER_API_KEY_HERE",
        "CUSTOM_API_URL": "https://openrouter.ai/api/v1",
        "CUSTOM_API_KEY": "YOUR_OPENROUTER_API_KEY_HERE",
        "DEFAULT_MODEL": "openai/o3"
      }
    }
  },
```

* **settings.json** file for **Windows**:

```
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": [
        "-y",
        "@upstash/context7-mcp"
      ]
    },
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-sequential-thinking"
      ]
    },
    "openrouter": {
      "command": "cmd",
      "args": [
        "/c",
        "uvx --from git+https://github.com/BeehiveInnovations/zen-mcp-server.git zen-mcp-server"
      ],
      "env": {
        "OPENROUTER_API_KEY": "YOUR_OPENROUTER_API_KEY_HERE",
        "CUSTOM_API_URL": "https://openrouter.ai/api/v1",
        "CUSTOM_API_KEY": "YOUR_OPENROUTER_API_KEY_HERE",
        "DEFAULT_MODEL": "openai/o3"
      }
    }
  },
  "preferredEditor": "vscode"
}
```

_Note: Providing API keys in environment variables and `settings.json` seems redundant but is a safe way to ensure the key is passed correctly._

# Using MCP Servers & LLM/OpenRouter

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
5. Check your LLM/OpenRouter configuration by typing:

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

