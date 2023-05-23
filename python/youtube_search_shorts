from selenium import webdriver
from bs4 import BeautifulSoup
import re
import argparse

def search_youtube_shorts(query):
    # Define the path to the WebDriver (ChromeDriver in the example)
    webdriver_path = "C:\Chrome\chromedriver.exe"

    # Instance from the browser using the WebDriver
    driver = webdriver.Chrome(webdriver_path)

    # url from the search results page of YouTube for "Google"
    query = query.replace(" ", "+")
    url = f"https://www.youtube.com/results?search_query={query}"

    #open the url    
    driver.get(url)

    # get the content of the page
    html_content = driver.page_source

    # close the browser
    driver.quit()

    # analyze the content of the page
    soup = BeautifulSoup(html_content, 'html.parser')

    # find all the shorts URLs
    pattern = r'"url":"/shorts/([^"]+)"'
    matches = re.findall(pattern, html_content)
    shorts_urls = matches if matches else []
    
    shorts_urls = [f"youtube.com/shorts/{url}" for url in shorts_urls]


    return shorts_urls

if __name__ == "__main__":
    parser = argparse.ArgumentParser()
    parser.add_argument("--q", help="Search term", default="Google")
    args = parser.parse_args()

    query = args.q
    shorts_urls = search_youtube_shorts(query)

    print('URLs dos shorts:')
    for url in shorts_urls:
        print(url)
