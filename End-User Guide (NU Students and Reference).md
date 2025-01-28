
## Getting Set Up

If you have never used the platform, the first step is to get in touch with the administrator. Currently, Northwestern's instance of the platform is maintained by Benjamin Spinrad. 
BenjaminSpinrad2025@u.northwestern.edu

Below are the basic components needed to make a request to the system using python.
Please note that all measurements in a job must have at least 3 probes (5 is recommended).

```
import requests
import json

url = 'http://caitlyn.cs.northwestern.edu/ripeline/schedule'



headers = { 'Content-Type': 'application/json' } 

addresses_and_probes = [{"address": '142.250.217.78', "probes": [55,19,252,77, 6745]}, {"address": '142.251.33.69', "probes": [55,19,252,77,6745]}]

headers = {

	'Content-Type': 'application/json'

}

data = { 'type': 'traceroute', 'addresses_and_probes': addresses_and_probes, 'description': 'some comments', 'userid': '*YOUR-USERID-HERE*' }

response = requests.post(url, data=json.dumps(data), headers=headers)
print('Status code:', response.status_code)
print('Response body:', response.json())
```

Currently the only types supported are ping and traceroute. If your job is scheduled successfully, the results will be returned to you by email. They will come in the following file structure: job_id/country_code/asn/probe_id.json. Each line in a json file is the result for one ping/traceroute from the probe with probe_id matching the file name, to the specified destination address. If you are missing a line, there are two possibilities:
- The probe for that ping/traceroute was unavailable
- The ping/traceroute did not reach its target.