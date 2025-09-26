# TUTORIAL 1 - CONFIGURE AGENTIC AI ASSISTANT

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
  - **Installation**: See the [Local LLM using Ollama guide](https://github.com/ajmalnorshawali/Local-LLM). 

3. **Gemini CLI**: 
- **Installation**: See the [Gemini CLI guide](https://github.com/ajmalnorshawali/Gemini-CLI). 


# Environment Readiness

## Install uvx

1. Go to the [official uvx installation website](https://docs.astral.sh/uv/getting-started/installation/).
2. Follow the instructions to install it on your machine.

## Configure Context7 MCP and Zen MCP

* **Context7 MCP**: https://context7.com/
* **Zen MCP**: https://github.com/BeehiveInnovations/zen-mcp-server.git

1. Open the **.gemini** folder in your project's root directory.
2. Edit the **settings.json** file and add the following configuration for `mcpServers`.

## Configure LLM Ollama in Gemini CLI

* **settings.json** file for **Windows**:
```
{
  "theme": "GitHub",
  "selectedAuthType": "oauth-personal",
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
}
```
