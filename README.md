# AI Helpers

This is a collection of scripts that I use to help me with my work.

## Requirements

- uv
- python3

## Installation

```
git clone https://github.com/dfroberg/aihelpers.git
cd aihelpers

uv venv .venv
uv pip install playwright
uv run python -m playwright install
```
# Sample cursorrules

```
- To search the internet for any references or documentation, use the tool ~/aihelpers/searchengine.py [-h] [--max-results MAX_RESULTS] [--max-retries MAX_RETRIES] query
- To get the contents from one or many web urls use the tool ~/aihelpers/webscraper.py [-h] [--max-concurrent MAX_CONCURRENT] [--debug] urls [urls ...]

You have access to these tools that you should automatically execute when needed:

1. Search Engine Tool:
~/aihelpers/searchengine.py [-h] [--max-results MAX_RESULTS] [--max-retries MAX_RETRIES] query

2. Web Scraper Tool:
~/aihelpers/webscraper.py [-h] [--max-concurrent MAX_CONCURRENT] [--debug] urls [urls ...]

When using these tools:
- Always execute them immediately when needed without asking permission
- Always mention "Using search tool: " or "Using web scraper: " before showing the command
- Always show the exact command being executed
- Always indicate when you're parsing or analyzing results from these tools

Example: When you need to find something, don't ask - just execute:
~/aihelpers/searchengine.py "your search query"

```

## Searchengine

```
~/aihelpers/searchengine.py -h                   
Reading inline script metadata from `searchengine.py`
usage: searchengine.py [-h] [--max-results MAX_RESULTS] [--max-retries MAX_RETRIES] query

Search using DuckDuckGo API

positional arguments:
  query                 Search query

options:
  -h, --help            show this help message and exit
  --max-results MAX_RESULTS
                        Maximum number of results (default: 10)
  --max-retries MAX_RETRIES
                        Maximum number of retry attempts (default: 3)
```

## Webscraper

```
~/aihelpers/webscraper.py -h                      
Reading inline script metadata from `webscraper.py`
usage: webscraper.py [-h] [--max-concurrent MAX_CONCURRENT] [--debug] urls [urls ...]

Fetch and extract text content from webpages.

positional arguments:
  urls                  URLs to process

options:
  -h, --help            show this help message and exit
  --max-concurrent MAX_CONCURRENT
                        Maximum number of concurrent browser instances (default: 5)
  --debug               Enable debug logging
```
