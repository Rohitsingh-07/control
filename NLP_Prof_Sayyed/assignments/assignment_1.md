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


