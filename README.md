# PyScript-and-Splunk-API-interaction
import requests
import json

# Splunk API endpoint
splunk_url = "https://<your_splunk_instance>:8089/services/search/jobs/export"

# Splunk search query
splunk_query = "search index=main | head 10"

# Splunk API parameters
splunk_params = {
    "search": splunk_query,
    "output_mode": "json"
}

# Splunk API authentication
splunk_auth = ("your_splunk_username", "your_splunk_password")

# Send API request to Splunk
response = requests.get(splunk_url, params=splunk_params, auth=splunk_auth, verify=False)

# Print API response
if response.status_code == 200:
    results = json.loads(response.content)
    print(results)
else:
    print("Error: Failed to get data from Splunk API")
