# Bitcoin price

Get bitcoin price in Python (https://pythonbasics.org)[learn python].

```python
import requests
import json
from forex_python.converter import CurrencyRates
import os

c = CurrencyRates()
rate = c.get_rate('USD', 'EUR') 
print(rate)

bitcoin_api_url = 'https://api.coinmarketcap.com/v1/ticker/bitcoin/'
response = requests.get(bitcoin_api_url)
response_json = response.json()
print(response_json)

for coin in response.json():
    price = coin.get("price_usd", "U$S Price not provided")
    btc_price = float(("{0:.2f}").format(float(price)))
    print("$ " + str(btc_price))

    btc_price_eur = float(("{0:.2f}").format(float(price)*rate))   
    print("\u20ac " + str(btc_price_eur))

    if btc_price_eur > 9000:
       os.system("notify-send trade btc")       
```
See https://codesharedot.github.io/bitcoin-price/
