import websocket
import json
import pprint

SOCKET = "wss://stream.binance.com:9443/ws/ethusdt@kline_1m"

count = 0

def on_message(ws, message):
    
    
    
   

    print('receive message')
    
    
    json_message = json.loads(message)
    pprint.pprint(json_message)

    candle = json_message['k']
    is_candle_close = candle['x']

    if is_candle_close:

        count = count + 1
        print(count) 
        
    




        

    
ws = websocket.WebSocketApp(SOCKET,  on_message=on_message)
ws.run_forever()
