# Request Ray

a batch based request package with retry stratgy that enables you to send X requests concurrently at rate of Y requests/execution with max retries for each N

## Setup

```shell
pip install request_ray
```

## How to use

```python
from request_ray import rray

requests = [{
    'method': 'POST',
    'url': 'https://google.com',
    'kwargs': {'data': json.dumps({'hello': 'world'}), 'headers': {'alpha': 'beta'}}
}, {
    'method': 'GET',
    'url': 'https://facebook.com',
    'kwargs': {}
}]

batch_size = 2 # max no of requests to send at a time
retry_policy = 3 # how many times to retry failed requests

responses rray.send_requests(requests, batch_size, retry_policy)
print(responses) # array of expected responses with structure in each element: {'index': 0, 'response': standard_response_object}
```
