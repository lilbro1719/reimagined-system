from urllib.request import urlopen as uReq
from bs4 import BeautifulSoup as soup

for x in range(1,51):
    url = f'https://books.toscrape.com/catalogue/page-{x}.html'

    page_html = uReq(url).read()
    page_soup = soup(page_html, "html.parser")

    book_store = page_soup.findAll('li', class_ = 'col-xs-6 col-sm-4 col-md-3 col-lg-3')

    filename = ("Bookscrap2.csv")
    f = open(filename, "a")

    headers = "Book title, Price (in GBP), Availability\n"
    f.write(headers)

    for book in book_store:
        book_title = book.h3.a["title"].replace(',','')
        book_price = book.findAll('p', class_ = 'price_color')
        price = book_price[0].text[2:]
        in_stock = book.findAll('p', class_ = 'instock availability')
        stock = in_stock[0].text.strip()
        if stock == 'In stock':
            stock = "Yes"
        else:
            stock = "No"

        print(f"Book title : {book_title}")
        print(f"Price : {price}")
        print(f"Availability: {stock}")


        f.write(f"{book_title}, {price}, {stock}\n")

    f.close()
