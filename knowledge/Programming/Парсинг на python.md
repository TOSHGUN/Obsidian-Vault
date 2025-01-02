примерный код парсера
```python
from bs4 import BeautidulSoup
import requests

url = "https://www.dns-shop.ru/catalog/17a8a01d16404e77/smartfony/"
request = requests.get(url)
soup = BeautifulSoup(request.text, "html.parser")
products = soup.find_all("td", class_="catalog-products")
for product in products:
	product = products.find("a", {'class':'storylink'})
	if product is not None:
		sublink = product.get('href')
		print(sublink)
```