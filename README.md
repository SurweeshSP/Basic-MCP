### 🧠 What is **MCP** (Modular Command Protocol)?

**MCP** stands for **Modular Command Protocol**, and it's a lightweight, Python-based server framework designed to **build composable, tool-integrated AI agent backends** using simple decorators like `@tool`, `@resource`, and `@agent`.

---

### 🧩 Why use MCP?

MCP is useful when you're:

* 🔧 Building **tool-augmented LLM applications**
* 📦 Want to **expose functions** as callable tools (e.g., for agents like OpenAI Assistants, LangChain, etc.)
* 🧠 Integrating AI tools in a modular way
* 🌐 Need an **HTTP-based API backend** to serve LLM tools

---

### 🛠️ What does your code do?

```python
from mcp.server.fastmcp import FastMCP

mcp = FastMCP("Demo")

@mcp.tool()
def add(a: int, b: int) -> int:
    return a + b

@mcp.resource("greeting://{name}")
def get_greeting(name: str) -> str:
    return f"Hello {name}"
```

* `FastMCP("Demo")`: Initializes the MCP server.
* `@mcp.tool()`: Marks a Python function as a **tool** (e.g., usable by AI agents).
* `@mcp.resource(...)`: Exposes a dynamic HTTP **resource** (e.g., `GET /greeting://John` returns `"Hello John"`).

---

### 💻 How to install **MCP**

If it's the [MCP by OpenDevin](https://github.com/OpenDevin/mcp), install it with:

```bash
pip install mcp
```

Or if it’s from source:

```bash
git clone https://github.com/OpenDevin/mcp.git
cd mcp
pip install -e .
```

---

### 🚀 Run Your MCP Server

After creating the tools/resources:

```bash
python your_script.py
```

It will start a local API server that can be used by AI agents to call your tools.

---

### 🤖 Including AI with MCP

You can integrate LLMs like OpenAI, HuggingFace, or local models with your tools like this:

```python
@mcp.tool()
def generate_response(prompt: str) -> str:
    from openai import OpenAI
    client = OpenAI()
    return client.chat.completions.create(model="gpt-4", messages=[{"role": "user", "content": prompt}]).choices[0].message.content
```

Or integrate LangChain, Semantic Kernel, or your custom model logic.

---

### 🧠 Summary

| Feature        | Description                                |
| -------------- | ------------------------------------------ |
| `FastMCP`      | FastAPI-powered server for LLM tools       |
| `@tool()`      | Exposes Python functions to AI models      |
| `@resource()`  | Creates dynamic REST-like endpoints        |
| Easy to extend | Add LLMs, vector DBs, tools, agents        |
| Use Cases      | LLM backends, AI assistants, custom agents |


