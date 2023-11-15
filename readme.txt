Scraping demo book website

## Scrapy Commands Cheat Sheet

### Generating a Spider
- `scrapy genspider spider_name domain.com`: Generate a new spider for your Scrapy project. Replace `spider_name` with your chosen spider name and `domain.com` with the target website.

### Running a Spider
- `scrapy crawl spider_name`: Start crawling with the specified spider. Replace `spider_name` with the actual name of your spider.
- `scrapy crawl spider_name -O bookdata.json`: save result to a file .csv or .json 
` -O new file -o appends to existing name file `

If a feeds is indicated in settings you can run without assigning the name file:
`scrapy crawl spider_name`: will generate bookdata.json
```FEEDS = {
   'booksdata.json': {'format': 'json'}
}```

Creating a custom_settings with the feed inside your spider will overwrite any feed or setting in settings.py
```
    custom_settings = {
        FEEDS: {
            'booksdata.json': {'format': 'json', 'overwrite': True}
        }
    }
```

### Basic Scrapy Commands
- `scrapy startproject project_name`: Create a new Scrapy project with the specified project name.
- `scrapy list`: List all available spiders in your project.
- `scrapy shell url`: Open an interactive shell for testing and debugging.
- `scrapy check project_name`: Check your Scrapy project for potential issues and suggestions.
- `scrapy version`: Display the installed Scrapy version.


Make sure to replace `project_name`, `spider_name`, and `domain.com` with your actual project and spider names, and the target domain you want to scrape. 

## Web Scraping with Scrapy: A Step-by-Step Guide

### Step 1: Make a Request

To initiate a web scraping operation, you need to make a request to the target URL using the 
`fetch()` method. Replace `'https://example.com'` with your desired URL:
```
fetch('https://example.com')
```
### Step 2: Accessing the Response

After making the request, you'll receive a response from the server. You can access this response using the response object.

### Step 3: Using response.css()

To extract data from the response content, you can use the response.css() method. It allows you to select HTML elements based on CSS selectors.

### Step 4: Extracting Data with get()

Use get() to extract the content of the first matching element based on your CSS selector. For example, to get the text of the first `<h1>` element:
```
h1_text = response.css('h1::text').get()
```
##Step 5: Extracting Data with getall()

Use getall() to extract data from all matching elements based on your CSS selector. For example, to get the text of all <p> elements:

```
p_texts = response.css('p::text').getall()
```




