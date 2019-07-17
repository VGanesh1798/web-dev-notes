# HTTP and HTTPS
HTTP stands for **H**yper**t**ext **T**ransfer **P**rotocol and is the primary method of fetching resources on the Web. HTTPS is a **S**ecure form of HTTP.

## Overview
HTTP is a client-server protocol where the client sends a request to the server, which sends back a response.

User-agent is another term for client and is almost always the Web browser. Servers **never** initiate an HTTP request. Between the two, there are numerous other computers to relay the HTTP messages, and some of these computers are proxies which do things like caching or filtering.

A request consists of a method, a path, the HTTP version, headers, and optionally a body.

A response consists of the HTTP version, a status code, a status message, headers, and again an optional body.

## Methods
```
GET       # Retrieve response from resource
HEAD      # Retrieve response without the body
POST      # Submit entity to resource
PUT       # Replace target resource with request payload
DELETE    # Delete specified resource
CONNECT   # Establish a tunnel to server identified by resource
OPTIONS   # Describe communication options for resource
TRACE     # Message loop-back test along path to target
PATCH     # Partially modify a resource
```

## Common Status Codes
```
100 Continue
200 OK
202 Accepted
300 Multiple Choice
400 Bad Request
404 Not Found
500 Internal Server Error
503 Service Unavailable
```

## CORS
**C**ross-**O**rigin **R**esource **S**haring uses additional HTTP headers to allow an application on one domain to access resources from another domain. It is especially useful when making a SPA with a REST API. Cross-origin requests are restricted by the browser for security reasons.