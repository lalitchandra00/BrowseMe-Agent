# BrowseMe-Agent

A small practice project for learning how to build a web-search agent with LangChain, Gemini, and DuckDuckGo.

## Requirements

- Python 3.10+
- A Google Gemini API key
- Internet connection
- Jupyter Notebook or VS Code with the Jupyter extension

Install the dependencies:

```powershell
python -m pip install -r requirements.txt
```

Create a `.env` file in the project folder:

```env
GOOGLE_API_KEY=your_google_api_key
```

## Workflow

```text
User question
      |
      v
AgentExecutor
      |
      v
LangChain agent + Gemini
      |
      v
DuckDuckGo search tool
      |
      v
Search results
      |
      v
Final answer
```

1. The user asks a question.
2. Gemini understands the question through the LangChain agent.
3. The agent decides whether web search is needed.
4. `DuckDuckGoSearchRun` searches the web.
5. The agent uses the results to create an answer.
6. `AgentExecutor` manages this process and returns the final output.

## Main components

- **Gemini (`llm`)**: Understands the question and writes the answer.
- **DuckDuckGo (`search_tool`)**: Searches the web.
- **ReAct prompt (`prompt`)**: Tells the agent how to reason and use tools.
- **Agent (`agent`)**: Decides which action to take.
- **AgentExecutor**: Runs the agent and tool-calling loop.

This project uses the classic LangChain agent pattern, so call the executor:


