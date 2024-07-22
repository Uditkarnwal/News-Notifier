# News-Notifier


### Introduction
This project involves developing a desktop application that delivers pop-up notifications of current news. To achieve this, we use web scraping techniques in Python to extract news articles from a website.

### Web Scraping Using Python
Web scraping is the process of extracting and processing data from websites. Python is particularly suited for this task due to its rich set of libraries and ease of use. In this project, we utilize the following libraries:

- **Requests**: To fetch HTML content from websites.
- **Beautiful Soup (bs4)**: To parse HTML and extract relevant data.

### Getting Started
To begin scraping news articles, follow these steps:

1. **Install Required Libraries**:
   Make sure you have the necessary libraries installed. You can install them using pip:
   ```
   pip install requests
   pip install beautifulsoup4
   ```

2. **Import Libraries**:
   In your Python script, import the required libraries:
   ```python
   from bs4 import BeautifulSoup
   import requests
   ```

3. **Fetch Website Content**:
   Use `requests` to fetch the HTML content of the website you want to scrape:
   ```python
   source = requests.get('http://coreyms.com').text
   ```

4. **Parse HTML**:
   Use `BeautifulSoup` to parse the HTML content:
   ```python
   soup = BeautifulSoup(source, 'lxml')
   ```

5. **Extract Data**:
   Identify the structure of the webpage (using browser developer tools or inspecting HTML):
   ```python
   for article in soup.find_all('article'):
       headline = article.h2.a.text
       print('Headline:', headline)
       
       summary = article.find('div', class_='entry-content').p.text
       print('Summary:', summary)
       
       vid_src = article.find('iframe', class_='youtube-player')['src']
       vid_id = vid_src.split('/')[4]
       vid_id = vid_id.split('?')[0]
       youtube_link = f'http://youtube.com/watch?v={vid_id}'
       print('YouTube Link:', youtube_link)
   ```

6. **Notification Integration**:
   Implement pop-up notifications in your desktop application to display fetched news articles.

### Conclusion
By following these steps, you can create a desktop application that notifies users of current news using web scraping techniques in Python. Ensure to handle errors gracefully, consider the website's terms of service, and keep your scraping scripts ethical and respectful of server load.

---

This revised README provides a structured approach to using Python for web scraping, focusing on clarity and correct usage of libraries like `requests` and `BeautifulSoup`. It also hints at the integration of notification features, which is crucial for your desktop app. Adjust and expand this document based on additional features or specifics of your project.
