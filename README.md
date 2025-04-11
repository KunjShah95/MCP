# MCP Gemini Search

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)](#)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
[![Python Version](https://img.shields.io/badge/python-3.7%2B-yellow)](#)

## 🚀 Project Overview

This project demonstrates how to use **Google's Gemini 2.5 Pro** with function-calling capabilities to interact with the `mcp-flight-search` tool via **Model Context Protocol (MCP)**. It enables natural language flight search through the following:

- Connection to a local MCP server process (`mcp-flight-search`) using stdio communication.
- Automatic parameter extraction from natural language input using Gemini's function-calling capabilities.
- Execution of flight searches via the MCP tool.
- Display of formatted results from the search.

---

## 📖 Table of Contents

1. [Features](#features)
2. [Prerequisites](#prerequisites)
3. [Setup](#setup)
4. [Architecture](#architecture)
5. [Usage](#usage)
6. [Error Handling](#error-handling)
7. [Related Projects](#related-projects)
8. [License](#license)

---

## ✨ Features

- **Natural Language Flight Search**  
  Easily search for flights using queries like:  
  `"Find flights from Atlanta to Las Vegas on 2025-05-05."`

- **Automatic Parameter Extraction**  
  Leverages Gemini's function-calling capabilities for seamless conversion of natural language into structured parameters.

- **Integration with MCP Flight Search Tool**  
  Communicates with the `mcp-flight-search` tool via stdio for flight data retrieval.

- **Formatted Results**  
  Outputs well-structured JSON responses for easy readability.

---

## 🛠️ Prerequisites

Before running this client, ensure you have the following:

1. **Python 3.7+**  
   [Download Python](https://www.python.org/downloads/)

2. **API Keys**  
   - **Gemini API Key:** Get this from [Google AI Studio](https://ai.google/).
   - **SerpAPI Key:** Obtain from [SerpApi](https://serpapi.com/).

3. **MCP Flight Search Tool**  
   Install the `mcp-flight-search` package.

---

## ⚙️ Setup

### Clone the Repository

```
git clone https://github.com/arjunprabhulal/mcp-gemini-search.git
cd mcp-gemini-search
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Install the MCP Flight Search Tool

```bash
pip install mcp-flight-search
```

### Set Environment Variables

```bash
export GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
export SERP_API_KEY="YOUR_SERPAPI_API_KEY"
```

Replace the placeholders with your actual API keys.

---

## 🏗️ Architecture

This project integrates multiple components to enable natural language flight search. Below is how the system works:

### 🔗 Component Interactions

**User to Client**

- User provides a natural language query, e.g.,
  `"Find flights from Atlanta to Las Vegas tomorrow."`
- The client script (`client.py`) processes the input.

**Client to MCP Server**

- Starts the MCP server process (`mcp-flight-search`).
- Establishes a stdio communication channel.
- Retrieves available tools and their descriptions.

**Client to Gemini 2.5 Pro**

- Sends the user's query to Gemini.
- Provides tool descriptions for function calling.
- Receives structured function calls with extracted parameters.

**Client to MCP Tool**

- Takes the parameters from Gemini.
- Calls the appropriate MCP tool.
- Handles response processing.

**MCP Server to SerpAPI**

- Sends requests to SerpAPI for flight data.
- Processes and formats flight information.

### 📊 Data Flow

**Input Processing**

User Query → Natural Language Text → Gemini 2.5 Pro → Structured Parameters

**Flight Search**

Parameters → MCP Tool → SerpAPI → Flight Data → JSON Response

**Result Handling**

JSON Response → Parse → Format → Display to User

### 🛡️ Communication Protocols

**Client ↔ MCP Server**

Stdio communication, asynchronous operations, MCP-compliant tool registration.

**MCP Server ↔ SerpAPI**

HTTPS requests, JSON data exchange, API key authentication.

**Client ↔ Gemini 2.5 Pro**

HTTPS requests, function-calling protocol, API key authentication.

---

## ▶️ Usage

Run the client:

```bash
python client.py
```

**What Happens:**

1. The script starts the MCP flight search server process.
2. Sends your flight search query to Gemini 2.5 Pro.
3. Uses Gemini's function calling to extract search parameters.
4. Executes the search via the MCP tool.
5. Displays the formatted results.

---

## 🔧 Error Handling

This integration includes error handling at multiple levels:

- Input validation
- API communication errors
- Tool execution failures
- Response parsing issues
- Data formatting problems

---

## 🔗 Related Projects

This client uses the `mcp-flight-search` tool, which is available at:

- GitHub: [arjunprabhulal/mcp-flight-search](https://github.com/arjunprabhulal/mcp-flight-search)
- PyPI: [mcp-flight-search](https://pypi.org/project/mcp-flight-search/)

---

## 📜 License

This project is licensed under the MIT License.
