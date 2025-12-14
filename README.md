# MCP Agent with Gemini Integration

## Overview

This project implements a Multi-Client Protocol (MCP) server that exposes various utility functions as "tools," and an intelligent client that uses the Google Gemini Large Language Model (LLM) to interact with these tools. The goal is to demonstrate an agent's ability to reason about a task and execute actions through an external server.

The server, `example_mcp_server.py`, provides capabilities such as mathematical calculations, image manipulation, and web browser control. The client, `talk2mcp.py`, connects to this server, discovers its tools, and uses the Gemini LLM to process user queries by intelligently calling the appropriate server-side tools.

## Features

The MCP server (`example_mcp_server.py`) exposes the following functionalities:

### Tools
*   **Mathematical Operations**: `add`, `subtract`, `multiply`, `divide`, `power`, `sqrt`, `cbrt`, `factorial`, `log`, `remainder`, `sin`, `cos`, `tan`, `mine`.
*   **Image Processing**:
    *   `create_thumbnail(image_path: str) -> Image`: Creates a 100x100 thumbnail from a given image path.
    *   `draw_rectangle_and_write_text_on_image(...)`: (If implemented) Creates an image, draws a rectangle, and writes text on it, saving the result to a specified path.
*   **String Manipulation**: `strings_to_chars_to_int(string: str) -> list[int]`: Converts a string into a list of ASCII integer values.
*   **List Processing**: `int_list_to_exponential_sum(int_list: list) -> float`: Calculates the sum of exponentials of numbers in a list.
*   **Sequence Generation**: `fibonacci_numbers(n: int) -> list`: Returns the first 'n' Fibonacci numbers.
*   **Web Browser Control**: `open_browser_to_google()`: Opens the default web browser to `www.google.com`.

### Resources
*   **`greeting://{name}`**: `get_greeting(name: str) -> str`: Provides a personalized greeting.

### Prompts
*   **`review_code(code: str) -> str`**: A prompt template for code review.
*   **`debug_error(error: str) -> list[base.Message]`**: A prompt template for debugging errors.

## Setup

### Prerequisites

Before you begin, ensure you have the following installed on your macOS system:

1.  **Python 3.10+**: This project uses modern Python features.
2.  **uv**: A fast Python package installer and manager. If not installed, use the standalone installer:
    
    curl -LsSf https://astral.sh/uv/install.sh | sh
        Or via Homebrew:
    brew install uv
    3.  **Node.js and npm (with npx)**: Required for certain MCP server functionalities.
    
    brew install node
    4.  **FFmpeg**: A multimedia framework. Required for `pydub` (if used in other parts of your broader project, not directly in `example_mcp_server.py`'s current state, but good to have if audio processing is intended).
    
    brew install ffmpeg
    5.  **Google Gemini API Key**:
    *   Obtain an API key from [Google AI Studio](https://ai.google.dev/).
    *   Create a `.env` file in the `where `talk2mcp.py` resides and add your API key:
        
