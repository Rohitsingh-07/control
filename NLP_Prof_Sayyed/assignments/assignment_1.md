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

---
