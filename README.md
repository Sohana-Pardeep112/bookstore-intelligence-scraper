# Bookstore Intelligence Scraper

Turns a competitor's online catalogue ([books.toscrape.com](https://books.toscrape.com/), a sandbox site built for scraping practice) into a clean business dataset, then uses it to answer pricing and range questions.

## How it works
1. **Download**: `requests` fetches each catalogue page.
2. **Parse**: `BeautifulSoup` finds every `<article class="product_pod">` card and extracts title, price, star rating, availability and product URL.
3. **Scale**: a loop follows the site's **next** button, so the same code scrapes 3, 5 or all 50 pages (`MAX_PAGES` setting).
4. **Clean**: £ symbol stripped and price converted to a number, rating words (One–Five) mapped to 1–5, whitespace and duplicates removed.
5. **Analyse**: pandas answers the business questions; a knapsack optimiser picks the books that maximise total stars within a £100 budget.

## Run it
pip install requests beautifulsoup4 pandas numpy matplotlib

Open `bookstore_scraper.ipynb` in VS Code, Jupyter or Google Colab and run all cells.

## Outputs
| File | What it is |
|---|---|
| `competitor_books.csv` | Scraped dataset: Title, Price, Rating, Availability, Product_URL |
| `rating_counts.png` | Bar chart of books per star rating |

## Tech
Python · requests · BeautifulSoup · pandas · NumPy · Matplotlib
