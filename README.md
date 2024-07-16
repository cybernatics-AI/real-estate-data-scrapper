# Real Estate Web Scraper

This Python script scrapes real estate listings from a specified website, extracting key information about properties such as house type, address, listing date, price, and description.

## Features

- Scrapes real estate listings from a given URL
- Extracts detailed information for each property listing
- Handles different date formats (including "Today" and "Yesterday")
- Normalizes Unicode characters in addresses
- Compiles the scraped data into a pandas DataFrame

## Prerequisites

Before running this script, make sure you have the following libraries installed:

- requests
- beautifulsoup4
- pandas
- lxml

You can install these dependencies using pip:

pip install requests beautifulsoup4 pandas lxml

## Usage

1. Import the necessary modules and the `scrape_real_estate` function into your Python script.

2. Call the function with the required parameters:

```python
today = "2024-07-16"  # Replace with the current date
yesterday = "2024-07-15"  # Replace with yesterday's date
url = "https://example-real-estate-website.com/listings"  # Replace with the target website URL

scraped_data = scrape_real_estate(today, yesterday, url)
```
3. The function returns a dictionary containing lists of scraped data. You can then convert this to a pandas DataFrame:

```python
df = pd.DataFrame()
for item in scraped_data:
    df = pd.concat([df, pd.DataFrame(item)], axis=0)
```

## Function Details
The scrape_real_estate function does the following:

1. Sends a GET request to the specified URL with custom headers to mimic a browser request.
2. Parses the HTML content using BeautifulSoup.
3. Finds all property listings on the page.
4. For each listing, extracts:

- House type
- Address
- Date listed
- Price
- Description


5. Handles special cases like recently added listings (Today/Yesterday).
6. Normalizes Unicode characters in addresses.

### Note
This script is designed for educational purposes and should be used responsibly. Always respect the website's terms of service and robots.txt file. Consider implementing rate limiting and error handling for production use.