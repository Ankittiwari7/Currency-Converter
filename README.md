# currency_converter_basic.py

def convert_currency(amount, from_currency, to_currency):
    # Currency exchange rates relative to 1 USD
    rates = {
        'USD': 1.0,
        'INR': 83.2,
        'EUR': 0.92,
        'GBP': 0.78,
        'JPY': 151.5
    }

    # Check if currency codes are valid
    if from_currency not in rates or to_currency not in rates:
        return "Unsupported currency."

    # Convert source currency → USD → target currency
    usd_amount = amount / rates[from_currency]
    converted_amount = usd_amount * rates[to_currency]

    return round(converted_amount, 2)


print("Welcome to Currency Converter")
print("Available currencies: USD, INR, EUR, GBP, JPY")

# Taking safe user input
from_curr = input("From currency: ").strip().upper()
to_curr = input("To currency: ").strip().upper()

try:
    amount = float(input("Amount: "))
except ValueError:
    print("Invalid amount! Please enter a numeric value.")
    exit()

result = convert_currency(amount, from_curr, to_curr)

print(f"\n{amount} {from_curr} = {result} {to_curr}")