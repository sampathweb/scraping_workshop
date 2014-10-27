Scrapy Workshop Demo Spiders
============================

This repo contains Scrapy spiders demo-ed in Radius Intelligence's workshop "Data Collection with Scrapy: Build & Manage Production Web Scraping Pipelines".

####[Presentation materials available here](https://docs.google.com/a/radius.com/presentation/d/1QUbdzaI7fRwY1lspgCPnZ5as-NAZzBjYEsuyKrOIBlM/view)

####[Meetup Description](http://www.meetup.com/Women-in-Data-Science-San-Francisco/events/210430882/)

The spiders collect data about the wine products from a wine website and are broken out into levels that build new concepts on top of each other. To run these spiders enter into your command line:

```sh
cd scraping_workshop/wine_example/spiders
scrapy runspider wine_example/spiders/L3_wine_pagination.py.py
```

or to write to a json file:
```sh
scrapy runspider wine_example/spiders/L3_wine_pagination.py.py -o wine_data.json
```
More instructions related to these exercises in the presentation (section Demo Part 1)

* __L0 (wine_example/spiders/L0_barespider.py)__
    * set up basic spider to fetch from wine&#x2E;com url
    * Shows how to create an Item with a field that stores all the raw html


* __L1 (wine_example/spiders/L1_wine.py)__
    * Create a spider that returns an item type named 'WineItem' containing the following fields: 1) the specific product page link, 2) product name, and 3) the current sell price. Only do this for the first page of products listed (containing just the first 25 wine products)


* __L2 (wine_example/spiders/L2_wine_meta.py)__
    * Add to the Wine item the following fields: 1) wine type and 2) region. The region is only available in the single product-specific links. This will require another callback with the first callback parsing for the link to the page for the specific product and using meta to pass information between callbacks.
    * For the wine type, you'll use the icon of the wine glass that is yellow for white wine, red for red wine. If you right click on it and select 'Inspect Element', you'll see that the attributes indicate the type of wine.
    * For the region, note the helpful JSON object towards the top of the html that starts with 'var utag_data' (right click on the page and select 'View Source'). This is where you get the region from and will require regex-ing out the JSON and json loading it into a dictionary and referencing the region key.


* __L3 (wine_example/spiders/L3_wine_pagination.py)__
    * Teach your spider to crawl through all product pages to gather all 5000+ products. There are several ways to do this, but one way is the check if the href for the 'Next' page hyperlink towards the bottom of the page exists and create a new Request object for that url if it does.


* __Wine_login.py (wine_example/spiders/wine_login.py)__
    * Create a login authentication aware spider



#####Take-Home Challenge:
* __L4 (wine_example/spiders/L4_wine_reviews.py)__
    * Complete this part on your own. Teach your spider to crawl one more page level deep to scrape all ratings and reviews for each product. You will need to scrape for the href in the hyperlink 'View all reviews' and create another Request object specifying another callback. Good luck and have fun!



Development Environment Setup Instructions
------------------------------------------

* For those who do not have pip installed:
```sh
curl -O https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py # writes to system Python
```

* Install & activate virtualenv
```sh
sudo pip install virtualenv # writes to system Python
virtualenv scrapy_learn # isolated from system Python
source scrapy_learn/bin/activate
```

* Install Scrapy & Dependencies
```
pip install wheel
pip install scrapy
```

* You will also need Chrome

Additional Resources
--------------------

* Scrapy Documentation
    * http://doc.scrapy.org/en/0.24/
* CSS Selectors
    * http://www.w3.org/TR/CSS2/selector.html
    * http://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048
* XPath
    * http://zvon.org/comp/r/tut-XPath_1.html
* Regex
    * https://docs.python.org/2/library/re.html
* Beautiful Soup
    * http://www.crummy.com/software/BeautifulSoup/bs4/doc
