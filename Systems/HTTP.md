# HTTP

This table contains functions that allow you to make HTTP requests.

* [HTTP.Get](https://hake.me/docs/systems/http#http-get-url-header-body)
* [HTTP.Post](https://hake.me/docs/systems/http#http-post-url-header-body)
* [HTTP.IsHostWhitelisted](https://hake.me/docs/systems/http#http-ishostwhitelisted-url)
* [HTTP.NewConnection](https://hake.me/docs/systems/http#http-newconnection-url)

  * [conn:Request](https://hake.me/docs/systems/http#conn-request-method-path-header-body)
  * [conn:AsyncRequest](https://hake.me/docs/systems/http#conn-asyncrequest-method-path-header-body)

    * [future:Wait](https://hake.me/docs/systems/http#future-wait)
    * [future:Get](https://hake.me/docs/systems/http#future-get)
    * [future:IsResolved](https://hake.me/docs/systems/http#future-isresolved)
    * [future:IsValid](https://hake.me/docs/systems/http#future-isvalid)
  * [conn:IsValid](https://hake.me/docs/systems/http#conn-isvalid)
  * [conn:Hostname](https://hake.me/docs/systems/http#conn-hostname)
  * [conn:Path](https://hake.me/docs/systems/http#conn-path)
  * [conn:Port](https://hake.me/docs/systems/http#conn-port)
  * [conn:Scheme](https://hake.me/docs/systems/http#conn-scheme)

---

## `HTTP.Get(url, header, body)`​

### Arguments

* ​`url`​ - The url (string) to perform the GET request on
* ​`header`​ - *optional* The headers to set on the request
* ​`body`​ - *optional* The body to set on the request

### Returns

A body (string), header (string), status (integer) representing the body, headers and status of the response.

### Remarks

This funciton executes syncronously and will pause the game until the response has been recieved.

---

## `HTTP.Post(url, header, body)`​

### Arguments

* ​`url`​ - The url (string) to perform the POST request on
* ​`header`​ - *optional* The headers to set on the request
* ​`body`​ - *optional* The body to set on the request

### Returns

A body (string), header (string), status (integer) representing the body, headers and status of the response.

### Remarks

This funciton executes syncronously and will pause the game until the response has been recieved.

---

## `HTTP.IsHostWhitelisted(url)`​

### Arguments

* ​`url`​ - The url (string) to test

### Returns

True if the url has been whitelisted (it's listed on its own line in `whitelisted_hosts.txt`​), false otherwise.

---

## `HTTP.NewConnection(url)`​

### Arguments

* ​`url`​ - The url (string) to create a connection for

### Returns

A connection object.

---

## `conn:Request(method, path, header, body)`​

### Arguments

* ​`method`​ - The http method to use for the request
* ​`path`​ - *optional* The path (string) to request
* ​`header`​ - *optional* The headers to set for the request
* ​`body`​ - *optional* The body to set for the request

### Returns

A body (string), header (string), status (integer) representing the body, headers and status of the response.

### Remarks

This function executes syncronously and will pause the game until the response has been received.

---

## `conn:AsyncRequest(method, path, header, body)`​

### Arguments

* ​`method`​ - The http method to use for the request
* ​`path`​ - *optional* The path (string) to request
* ​`header`​ - *optional* The headers to set for the request
* ​`body`​ - *optional* The body to set for the request

### Returns

A future object representing the response of the request.

### Remarks

This function executes asyncronously and will **not** pause the game until the response has been received. Instead you must query (or wait on) the future object that is returned to get the response.

---

## `conn:IsValid()`​

### Returns

True if the connection was successful and is valid

---

## `conn:Hostname()`​

### Returns

The hostname portion of the url provided to `HTTP.NewConnection`​.

---

## `conn:Path()`​

### Returns

The path portion of the url provided to `HTTP.NewConnection`​.

---

## `conn:Port()`​

### Returns

The port portion of the url provided to `HTTP.NewConnection`​.

---

## `conn:Scheme()`​

### Returns

The scheme portion of the url provided to `HTTP.NewConnection`​.

---

## `future:Wait()`​

### Remarks

Causes the future to pause (the game) until the response has been recieved.

---

## `future:Get()`​

### Returns

A body (string), header (string), status (integer) representing the body, headers and status of the response.

### Remarks

This function will cause the future to wait (similarly to `future:Wait()`​) until the response is recieved, but will do no waiting if the response is already recieved.

---

## `future:IsResolved()`​

### Returns

True if the future is valid and resolved (the response has been recieved).

---

## `future:IsValid()`​

### Returns

True if the future is valid.
