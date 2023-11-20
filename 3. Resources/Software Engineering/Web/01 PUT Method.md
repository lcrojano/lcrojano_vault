
- The PUT method is used to update a resource or create a new resource if it doesn't exist at the specified URL.
- When you use PUT to update a resource, you typically send the full representation of the resource in the request.
- If the resource already exists, the entire resource is replaced with the new representation provided in the request.
- If the resource does not exist, a new resource is created with the specified representation at the given URL.
- PUT is idempotent, meaning that if the same request is made multiple times, it has the same effect as making it once.
``` javascript
import requests
import json

url = 'https://api.example.com/resource/123'
data = {'key': 'new_value'}

response = requests.put(url, data=json.dumps(data), headers={'Content-Type': 'application/json'})

print(response.status_code)
```


another option is [[02 PATCH Method]]
