# Trove newspaper front pages

This repository demonstrates how to harvest information about the contents of newspaper front pages from Trove. It then uses the harvested data to explore how the contents of front pages have changed over time.

## Notebooks

- [`large-harvest-example.ipynb`](large-harvest-example.ipynb) – uses the Trove Newspaper Harvester as a library to download information about all articles published on the front pages of newspapers (about 19 million articles)
- [`convert-front-pages-harvest.ipynb`](convert-front-pages-harvest.ipynb) – converts the large `ndjson` file created by the Trove Newspaper Harvester into parquet formatted datasets
- [`explore-front-pages.ipynb`](explore-front-pages.ipynb) – uses the parquet datasets to visualise changes in front pages over time

## Datasets

### `front_pages.parquet`

Contains summary information about articles published on the front pages of newspapers. There are 16,398,514 rows of data (274.4mb). Includes the following columns:

| Column | Description |
|--------|-------------|
`article_id`| Trove numeric identifier for article|
`title` | title of the article
`newspaper_id` | Trove numeric identifier for the newspaper in which the article was published
`date` | date the article was published
`category` | category of the article, eg: 'Article', 'Advertising'
`word_count` | number of words in the article
`page_id` | Trove numeric identifier for the page on which the article was published

### `front_pages_totals.parquet`

Derived from `front_pages.parquet` by adding together the word counts for articles within each category, giving us the total words per category for each front page. There are 4,351,009 rows of data (35.1mb). Includes the following columns:

| Column | Description |
|--------|-------------|
`date` | date the page was published
`page_id` | Trove numeric identifier for the page
`newspaper_id` | Trove numeric identifier for the newspaper 
`category` | article category eg: 'Article', 'Advertising'
`total` | number of words in this category on this page

----

Created by [Tim Sherratt](https://timsherratt.org), August 2023


