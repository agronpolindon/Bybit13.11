# Bybit13.11
pip install pybit
api_key = "SUJL2AkgWhYjpFfQ6GPDtqrLMhmHjLhwY31fO"
api_secret = "SUJL2AkgWhYjpFfQ6GPDtqrLMhmHjLhwY31f"


client = bybit.Client(api_key, api_secret)


def create_order(symbol, side, quantity, price):
    order = client.create_order(
        symbol=symbol,
        side=side,
        type=binance.OrderType.LIMIT,
        timeInForce=binance.constants.TimeInForce.GTC,
        quantity=quantity,
        price=price
    )
    return order


while True:
    
    price = float(client.get_symbol_ticker(symbol="TONUSDT")['price'])

    
    buy_price = price + 0.01
    sell_price = price - 0.01
    buy_stop_loss = price
    sell_stop_loss = price
    buy_take_profit = buy_price + 0.06
    sell_take_profit = sell_price - 0.06

   
    create_order("TONUSDT", binance.constants.Side.BUY, quantity, buy_price)
    create_order("TONUSDT", binance.constants.Side.SELL, quantity, sell_price)

   
    time.sleep(60)
