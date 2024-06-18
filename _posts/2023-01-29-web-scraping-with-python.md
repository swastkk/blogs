---
title: Web Scraping with Python
author: swastik
date: 2023-01-29 20:55:00 +0800
categories: [webscraping, python]
tags: [python]
image:
  path: /assets/images/webscrap.webp
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt:
---

**Web scraping** is a automatic method to obtain large amounts of data from the websites. Suppose we have to obtain some information from a website, usually what we did, is to start copy paste the data from the website to our file, but if we practically think, this method is quite cumbersome. And suppose if you are into data analysis, big data, machine learning or even AI projects, chances are you are required to collect data from various websites and there comes the concept of web scraping.

## Why Python?

Python is very commonly used in manipulating and working with data due to its **stability**, **extensive statistical libraries** and **simplicity.**

## Prerequisites

Before we begin , please set up Python environment on your machine. Head over to their [official page](https://www.python.org/downloads/) to install if you have not done so.

We will also be installing _[Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)_ and _[Request](https://pypi.org/project/requests/)_ modules.

## Getting Started

Firstly make sure you have installed the python packages which are required for the scraper to work.

```python
pip install beautifulsoup4
```

```python
pip install requests
```

After the installations, import these to the python file by running-

```python
import requests
from bs4 import BeautifulSoup
```

Now we need to create a variable of the URL of the website we are trying to scrape off the data

```python
URL= "-----url to be pasted-----" #Created variable with name 'URL'
```

Create the get method to requests module

```python
req= requests.get(URL)
```

After that create a instance of the BeautifulSoup as

```python
soup= BeautifulSoup(req.______, 'type of parser')
```

In the above line of code, we have to mention the stuff that we want to scrape from the website ie

1. **_req.content_** can be used to get the raw html content.
2. **_req.text_** can be used to get all text of the page.
3. **_req.headers_** can be used for the header in that page.

And the **_type of parser_** , that can be used are-

- _html.parser_
- _htmlparser2_
- _html5lib_
- _lxml_

and many more.

Install any of above listed HTML parser by running-

```python
pip install '______' # HTML Parser name
```

Now you can print the content you parsed by using print function

```python
print(soup.prettify()) #This prettify() method will turn a Beautiful Soup parse tree into a nicely formatted Unicode string.
```

Tadda, you have successfully scraped the data from the website you want. Now, we can use any useful data from the HTML content. The soup object contains all the data in the nested structure which could be programmatically extracted.

[This](https://github.com/swastkk/web-scraper) contains the code if you need and a beautiful example of Web scraping, have a look and don’t forget to star this repo :P

## Future Article

1. On the further more advanced features in web scraping like Automatic scraping, Compile the huge data into readable formats like PDF’s, DOC’s, Tables, Lists etc.

2. Web Scraping with **Go language** because of its speed.

If anyone finds these useful, feel free to share this, and comment down the issues you are facing.

Happy Hacking :)

Originally posted on Medium [here](https://medium.com/coderbyte/web-scraping-with-python-48ae39656bbb)

<div style="text-align: center;">
  <p style="margin-bottom: 1px;">Visitor Count</p>
  <img src="https://profile-counter.glitch.me/swastkk-web-scraping/count.svg" alt="visitor count" />
</div>