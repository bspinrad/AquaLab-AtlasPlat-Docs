
## Getting Set Up

If you have never used the platform, the first step is to get in touch with the administrator. Currently, Northwestern's instance of the platform is maintained by Benjamin Spinrad. Please send an email to 

>BenjaminSpinrad2025@u.northwestern.edu

with a userid of your choosing (please make it unique). Remember this userid, as you will use it in every job request you make. Here is the basic components needed to make a request to the system using python:

```
import requests
import json

url = 'http://lisa.cs.northwestern.edu:5000/handle'

headers = {

	'Content-Type': 'application/json'

}

addresses_and_probes = [{"address": '142.250.217.78', "probes": [55,19,252]}, {"address": '142.251.33.69', "probes": [77, 6745]}]

data = {

    "type": "ping",

    "addresses_and_probes": addresses_and_probes,

    "option_param_array": {"param1": "value1", "param2": "value2"},

    "description": "Student testing",

    "userid": "*YOUR-USERID-HERE*"

}

response = requests.post(url, data=json.dumps(data), headers=headers)
```

Currently the only types supported are ping and traceroute. The optional_param_array currently has no effect. It will eventually support the modification of fields "af", "resolve_on_probe", "skip_dns_check", and "is_public". See [this link](https://atlas.ripe.net/docs/apis/rest-api-manual/measurements/types/base_attributes.html) for reference.