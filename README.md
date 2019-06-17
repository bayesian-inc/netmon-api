# netmon-api
API specs for NetMon service

### Technical info
JSON is used for both request and response.

#### Parameters explanation
`cnt`: Number of results to return for the given query/stats. Positive integers apprechiated.  
`start`: Gives the start date for the query. Should follow python's datetime fomat. [here](https://docs.python.org/3/library/datetime.html#datetime.datetime.fromisoformat)  
`end`: Gives the end date for the query. Format should be the same as `start`  
`key`: If you have an API key, it can increase the lookup time window and the amount of results returned  
  
### Statistics
#### Unique IP observed per county

Endpoint: `https://api.bayesian.io/v1/stats/countries`  
Parameters: `cnt`, `start`, `end`, `key`  
Example:  
```
curl -d '{"start":"2019-06-11", "end":"2019-06-20","cnt":"10"}' -H "Content-Type: application/json" -X POST https://api.bayesian.io/v1/stats/countries
```

#### Unique IP observed per TCP port

Endpoint: `https://api.bayesian.io/v1/stats/ports`  
Parameters: `cnt`, `start`, `end`, `key`  
Example:  
```
curl -d '{"start":"2019-06-11", "end":"2019-06-20"}' -H "Content-Type: application/json" -X POST https://api.bayesian.io/v1/stats/ports
```

### Queries
#### Get info on IP address

Endpoint: `https://api.bayesian.io/v1/query/ip`  
Parameters: `country`, `start`, `end`, `key`   
Example:  
```
curl -d '{"ip":"113.161.160.2","start":"2019-06-11", "end":"2019-06-20"}' -H "Content-Type: application/json" -X POST https://api.bayesian.io/v1/query/ip
```


#### Get observed IP addresses for a given country

Endpoint: `https://api.bayesian.io/v1/query/country`  
Parameters: `country`, `start`, `end`, `key`  
Example:  
```
curl -d '{"country":"VN","start":"2019-06-11", "end":"2019-06-20"}' -H "Content-Type: application/json" -X POST https://api.bayesian.io/v1/query/country
```

#### Get observed IP addresses for a given tag

Endpoint: `https://api.bayesian.io/v1/query/tag`  
Parameters: `cnt`, `start`, `end`, `key`  
Example:  
```
curl -d '{"tag":"VNC_BRUTEFORCER_HIGH","start":"2019-06-11", "end":"2019-06-20"}' -H "Content-Type: application/json" -X POST https://api.bayesian.io/v1/query/tag
```
