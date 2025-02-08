# AI Helpers

![Python Version](https://img.shields.io/badge/python-3.x-blue.svg)

A collection of Python scripts for efficient web scraping and searching, designed to work both as standalone tools and as helper tools for the [Cursor Editor](https://www.cursor.com/) - an AI-first code editor.  
Cursor helper tools are custom scripts that can be integrated into the editor to extend its capabilities with additional AI-powered functionalities.

This toolkit provides two main utilities:
- A [DuckDuckGo](https://duckduckgo.com/)-powered search engine tool ([searchengine.py](searchengine.py))
- A concurrent web scraper using [Playwright](https://playwright.dev/python/) ([webscraper.py](webscraper.py))

## Quick Start

```bash
# Search for something
./searchengine.py "latest aws news" --max-results 5

# Scrape content from multiple websites
./webscraper.py https://thenewstack.io/ https://aws-news.com/ https://news.ycombinator.com/
```

## Prerequisites

- [uv](https://github.com/astral-sh/uv) - Modern Python package manager (faster alternative to pip)
- Python 3.8 or higher

## Installation

```bash
# Clone the repository
git clone https://github.com/dfroberg/aihelpers.git
cd aihelpers

# Install uv
# macOS
brew install uv

# Windows (requires pip)
pip install uv

# Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Create and activate virtual environment using uv
uv venv .venv
source .venv/bin/activate  # On Unix systems
# or
.venv\Scripts\activate     # On Windows

# Install dependencies
uv pip install playwright duckduckgo-search html5lib
uv run python -m playwright install
```

## Tools

### Search Engine

A DuckDuckGo-powered search tool that returns formatted results with URLs, titles, and snippets.

```bash
./searchengine.py [-h] [--max-results MAX_RESULTS] [--max-retries MAX_RETRIES] "your search query"
```

Options:
- `--max-results`: Maximum number of results to return (default: 10)
- `--max-retries`: Maximum number of retry attempts (default: 3)

Example:
```bash
./searchengine.py --max-results 5 "Python web scraping best practices"
```

Output format:
```
=== Result 1 ===
URL: https://example.com
Title: Example Title
Snippet: Example content snippet...
```

Note: Debug and error messages are written to stderr, while search results are written to stdout. This allows for easy output redirection:
```bash
./searchengine.py "query" > results.txt
```

### Web Scraper

An asynchronous web scraper that can process multiple URLs concurrently and extract their content.

```bash
./webscraper.py [-h] [--max-concurrent MAX_CONCURRENT] [--debug] urls [urls ...]
```

Options:
- `--max-concurrent`: Maximum number of concurrent browser instances (default: 5)
- `--debug`: Enable debug logging

Example:
```bash
./webscraper.py --max-concurrent 3 https://example.com https://example2.com
```

Output format:
```
=== Content from https://example.com ===
[Extracted text content in markdown format]
=====================================
```

## Features

- **Search Engine Tool**:
  - DuckDuckGo API integration
  - Configurable results count
  - Automatic retry mechanism
  - Formatted output with URLs and snippets
  - Safe search enabled by default

- **Web Scraper Tool**:
  - Concurrent URL processing
  - Playwright-powered browser automation
  - Smart content extraction
  - Markdown-formatted output
  - Built-in noise filtering (scripts, styles, analytics)

## Dependencies

- [playwright](https://playwright.dev/python/) - Modern browser automation
- [duckduckgo-search](https://pypi.org/project/duckduckgo-search/) - DuckDuckGo API wrapper
- [html5lib](https://github.com/html5lib/html5lib-python) - HTML parser

## Usage as Cursor Rules

These tools can be integrated into Cursor as helper tools. Add these rules to your Cursor configuration:

```yaml
- To search the internet: ~/aihelpers/searchengine.py [-h] [--max-results MAX_RESULTS] [--max-retries MAX_RETRIES] query
- To scrape web content: ~/aihelpers/webscraper.py [-h] [--max-concurrent MAX_CONCURRENT] [--debug] urls [urls ...]
```

## Credits

- Original inspiration: [devin.cursorrules](https://github.com/grapeot/devin.cursorrules/tree/master)

## License

This project is open source and available under the MIT License.