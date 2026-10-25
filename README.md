# BrowseMe-Agent

A small practice project for learning how to build a LangChain agent with Gemini, web search, and a custom weather tool.

## Requirements

- Python 3.10+
- A Google Gemini API key
- A Weatherstack API key
- Internet connection
- Jupyter Notebook or VS Code with the Jupyter extension

Install the dependencies:

```powershell
python -m pip install -r requirements.txt
```

Copy [.env.example](./.env.example) to `.env` and add your API keys:

```env
GOOGLE_API_KEY=your_google_api_key
WEATHER_STACK_API=your_weatherstack_api_key
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
      +----------------------+
      |                      |
      v                      v
DuckDuckGo search      Weather tool
      |
      v
Results
      |
      v
Final answer
```

1. The user asks a question.
2. Gemini understands the question through the LangChain agent.
3. The agent decides whether to search the web or check the weather.
4. `DuckDuckGoSearchRun` or the custom weather tool runs.
5. The agent uses the result to create an answer.
6. `AgentExecutor` manages this process and returns the final output.

## Main components

- **Gemini (`llm`)**: Understands the question and writes the answer.
- **DuckDuckGo (`search_tool`)**: Searches the web.
- **Weather tool (`get_weather_data`)**: Gets current weather for a city from Weatherstack.
- **ReAct prompt (`prompt`)**: Tells the agent how to reason and use tools.
- **Agent (`agent`)**: Decides which action to take.
- **AgentExecutor**: Runs the agent and tool-calling loop.

This project uses the classic LangChain agent pattern, so call the executor:

