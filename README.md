# MCP Flight Search

A flight search application using Google's Gemini API and MCP (Model Completion Protocol) for finding flights between destinations.

## Setup

1. Clone the repository
2. Install dependencies: `pip install google-generativeai mcp python-dotenv`
3. Create a `.env` file with your API keys:
   ```
   GEMINI_API_KEY=your_gemini_api_key
   SERP_API_KEY=your_serp_api_key
   ```
4. Run the application: `python client.py`

## Features

- Search for flights using natural language queries
- Integration with Google's Gemini API for intelligent search
- MCP protocol for structured data handling

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## License

MIT