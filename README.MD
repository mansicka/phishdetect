# Phish detect 


## Tool description
This tool demonstrates a very simple method for detecting possible potential phishing sites from a set of URLs.
The tool mimics *some* detection methods for possible phishing sites described in the papers linked in the home assignment, but does it in a very simple way. 


The tool works as follows:  

1. It fetches potential phishing urls from phishtank.com. This is done by fetching a url listing page and parsing the url data out of html using BeautifulSoup4. The user can configure how many pages are parsed through - one page has 20 urls, of which ~10 are usually usable. These are collected into a list, and duplicates are removed. 
    Alternatively, a local csv file is used instead of scraping.

2. The tool checks for URL age in days for all urls in the list.

3. The tool processes and grades urls in the list. External css, image and script links add up one point for each link. All urls below one point and/or with no age information are discarded. A new object list is generated containing url, points and age in days. This takes time as some urls are slow.

4. Some urls are discarded based on several properties:   
    -Url's points are too much below average (possible good/not a phishing url)  
    -Url's age is above average (possible good/not a phishing url)  

5. Results are plotted using matplotlib. 

## Usage instructions:
The tool can be run with either processed data, or with raw url data. See the end of code block for options.

*Consider this when running the phishtank scraper option and/or the url data scraping option: all operations run on a single thread, hence the process is slow.   Setting the pages scraped amount anything over 10-ish tends to result in long processing times. This might also get your ip blocked by Phishtank for a while.*  

For demonstration purposes I've provided two csv files to speed up processing:  
urls.csv: Contains a set of 1900-ish urls scaped from Phistank (on 25th of Feb 2021)  
out.csv: Contains processed data from urls.csv - this is the demo material.