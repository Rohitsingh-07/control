# 1. Text Extraction and Cleanup:

```
import re
from bs4 import BeautifulSoup

def clean_text_column(df, column_name="Text"):
    """
    Clean raw text data from a specified column in a pandas DataFrame.
    
    Steps:
    1. Remove HTML tags using BeautifulSoup.
    2. Remove special characters, numbers, and punctuation (keep only letters).
    3. Strip extra whitespace.

    Parameters:
    ----------
    df : pandas.DataFrame
        Input DataFrame containing the raw text.
    column_name : str, optional (default="Text")
        Column name containing text to be cleaned.

    Returns:
    -------
    pandas.Series
        A cleaned pandas Series with processed text.
    """

    def _clean(text):
        # 1. Remove HTML tags
        text = BeautifulSoup(text, "html.parser").get_text()
        # 2. Keep only letters (remove numbers & special characters)
        text = re.sub(r"[^a-zA-Z\s]", "", text)
        # 3. Convert to lowercase
        text = text.lower()  # Take this off
        # 4. Remove extra whitespace
        text = re.sub(r"\s+", " ", text).strip()
        return text

    return df[column_name].astype(str).apply(_clean)
```

- `import re` is module in python is all about regular expressions (regex), which are patterns we use to search, match, and manipulate text.
- `re.match(pattern, string)` Match only at the **beginning** of the string.
- `re.search(pattern, string)` Looks for the first occurrence of the pattern anywhere in the string.
- `re.findall(pattern, string)` Returns a list of all non-overlapping matches in the string.
- `re.finditer(pattern, string)` Like findall, but returns an iterator of match objects (gives positions too).
- `re.sub(pattern, repl, string)` Replaces all matches of the pattern with something else.
- `re.split(pattern, string)` Splits a string wherever the pattern matches.
- `re.compile(pattern)` Compiles a regex into a reusable object (faster for repeated use).

Why Use re?
- Clean messy text (remove unwanted characters, extract useful parts).
- Validate input (emails, phone numbers, passwords).
- Transform data (replace or split text with flexible rules).
- Super useful in data cleaning, NLP, and web scraping.

More info - https://chatgpt.com/s/t_68bc46e512b0819180d34f8eedb539fd
---

- `from bs4 import BeautifulSoup` bs4 is the Beautiful soup library, used for parsing and cleaning HTML or XML data
- BeautifulSoup is the class inside bs4, it takes raw HTML and parses it into a structured format that we can easily search, clean and manipulate, basically a structured version of the messy HTML text
- Once text is parsed, you can search, navigate, or clean it easily.

Major Functions / Uses of BeautifulSoup
- Remove HTML tags
- Parse HTML into a tree
- Find elements
- Find all elements
- Modify or clean HTML

Why Use Beautiful Soup?
- To Parse and Extract Text from HTML / XML
- To Navigate Webpage Structure Easily
- To Clean Messy Data
- Works with Web Scraping Tools
  - requests → to fetch the webpage.
  - pandas → to put extracted data into DataFrames.
  - selenium → to scrape dynamic pages.

---

- We create a function clean_text_column that will clean the text inside one column of a pandas dataframe
- We create a helper function _clean that processes one single text string at a time.
- Uses BeautifulSoup to remove any HTML tags.
- Removes everything except letters (a–z, A–Z) and spaces.
- Gets rid of numbers, punctuation, emojis, and special characters.
- replaces multiple spaces, tabs, or newlines with a single space.
- removes any leading/trailing spaces.
- Returns the cleaned text string.
- Takes the DataFrame column (df[column_name]).
- Converts everything in it to strings (astype(str)), so it doesn’t break on numbers/NaN.


