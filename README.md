# CoinGecko-API      
This script uses the CoinGecko API to fetch information about a specific cryptocurrency
import requests

def get_crypto_info(crypto_id):
    url = f'https://api.coingecko.com/api/v3/coins/{crypto_id}'
    response = requests.get(url)
    data = response.json()
    if 'id' in data:
        return data
    return None

# Example usage
crypto_id = 'bitcoin'

crypto_info = get_crypto_info(crypto_id)
if crypto_info:
    print(f"Information about {crypto_info['name']} ({crypto_info['symbol']}):")
    print(f"Current price: ${crypto_info['market_data']['current_price']['usd']}")
    print(f"Market cap rank: {crypto_info['market_cap_rank']}")
    print(f"Total supply: {crypto_info['market_data']['total_supply']}")
    # Add more information as needed
else:
    print(f"Failed to retrieve information for {crypto_id}")
