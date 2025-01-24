
## Getting Set Up

If you have never used the platform, the first step is to get in touch with the administrator. Currently, Northwestern's instance of the platform is maintained by Benjamin Spinrad. 
BenjaminSpinrad2025@u.northwestern.edu

Here are the basic components needed to make a request to the system using python:

```
import requests
import json

url = 'http://caitlyn.cs.northwestern.edu/ripeline/schedule'



headers = { 'Content-Type': 'application/json' } 

addresses_and_probes = [{"address": '142.250.217.78', "probes": [55,19,252]}, {"address": '142.251.33.69', "probes": [77, 6745]}]

headers = {

	'Content-Type': 'application/json'

}

data = { 'type': 'traceroute', 'addresses_and_probes': addresses_and_probes, 'description': 'some comments', 'userid': '*YOUR-USERID-HERE*' }

response = requests.post(url, data=json.dumps(data), headers=headers)
print('Status code:', response.status_code)
print('Response body:', response.json())
```

Currently the only types supported are ping and traceroute.