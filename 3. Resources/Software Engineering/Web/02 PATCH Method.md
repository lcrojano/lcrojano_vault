
- The PATCH method is used to apply partial modifications to a resource.
- Instead of sending the full representation of the resource, you send only the changes you want to apply.
- PATCH is particularly useful when you want to update a resource without sending the entire payload, which can be more efficient.
- Like PUT, PATCH is idempotent.

``` javascript
import requests
import json

url = 'https://api.example.com/resource/123'
data = {'key': 'new_value'}

response = requests.patch(url, data=json.dumps(data), headers={'Content-Type': 'application/json'})

print(response.status_code)
```



In summary, use [[01 PUT Method]] when you want to update a resource by providing the full representation, and use [[02 PATCH Method]] when you want to apply partial modifications to a resource. The choice between them depends on the use case and the level of granularity you need in your updates.