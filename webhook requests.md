Links: [[PROGRAMMING]] - [[TECHNOLOGY]] - [[PYTHON]]

--- 
sample.py
```py
from flask import Flask, request
import json

app = Flask(__name__)

@app.route('/',methods=['POST'])
def foo():
	# print(request.data)
	data = json.loads(request.data)
	print("New computer: {}".format(data['computer']['general']['name']))

	return "OK"

if __name__ == '__main__':
	app.run()
```

httpreq.py
```py
import requests
import os
import json

with open('{}/Desktop/542.json'.format(os.getenv("HOME")), 'rb') as j:
	j = json.load(j)
	req = requests.post('http://127.0.0.1:5000/', data=json.dumps(j))
	print(req.text)
```

testteams.py
```py
import requests
url = 'https://outlook.office.com/webhook/d8057ea7-7282-48f4-a063-9846f02a5874@2d83fad4-ff2b-4f41-9c09-5cf43012a50f/IncomingWebhook/900a5b01683d4a41867613b149b302ae/3b17c056-b1b7-4328-96af-0d6549acedfd'

requests.post(url=url, json={'text': 'hello world'})
```


--- 

[[ python ]]