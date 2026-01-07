# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Google Maps scraper built with Playwright that extracts business listings from Google Maps. It gathers contact details, addresses, ratings, and other business information for educational purposes.

## Architecture

The project consists of a single main file (`main.py`) with the following key components:
- `Business` dataclass: Represents a business with fields like name, address, website, phone, ratings, etc.
- `BusinessList` dataclass: Manages a list of Business objects with duplicate detection and export capabilities
- Main scraping logic: Uses Playwright to interact with Google Maps, search for businesses, and extract data
- Batch processing: Can process multiple searches from input.txt or single searches via command line

## Development Commands

### Setup
```bash
# Create virtual environment (recommended)
virtualenv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows

# Install dependencies
pip install -r requirements.txt
playwright install chromium
```

### Running the Scraper
```bash
# Single search
python3 main.py -s="coffee shops in Seattle" -t=50

# Batch search from input.txt
python3 main.py -t=30
```

### Input File Format
- Create `input.txt` with one search query per line
- Format: "business type in location" (e.g., "dentists in Boston, MA")

## Key Features

- Data extraction: Business name, address, website, phone, ratings, coordinates
- Duplicate detection: Prevents duplicate entries based on name and contact info
- Export formats: Saves data to CSV format only
- Output directory: Creates timestamped folders in "GMaps Data"
- Batch processing: Supports multiple searches from input.txt file

## Important Notes

- This project is for educational purposes only
- Always respect Google's Terms of Service and scraping policies
- The scraper uses headless=False by default (browser window will appear)
- Google Maps limits visible results (~120 per search), so use granular queries
- The script creates a "GMaps Data" directory with subdirectories by date