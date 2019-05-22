## Reverse Proxy

#### Proxy
Proxy is a web server which hides client identity whenever we try to access the server(example google.com).
Client makes the request, but server doesn't who is the client. Server essentially knows the proxy and sends the response to the proxy.
Proxy knows the client and route the content back to the client who requested it.

Benefits:
- Anonymity -> Server doesn't know who is the client.
- Caching -> Proxy can cache the static files from server. Problems : syncing.
- Blocking unwanted sites ->  example. block unwanted sites
- GeoFencing -> Clients can access certain servers. People from a particular area are not allowed to access server.

#### Reverse Proxy
Reverse proxy is a web server that centralizes internal servers and provides single interface to the client. Request will be routed to the available server. 

<img src="../assets/reverse_proxy.png" width="480"/>

Benefits:
- Load Balancing is a special case of reverse proxy. It has to have two or more servers to balance the load. 
- Caching
- Isolating Internal Traffic
- Logging
- Canary Releases
- SSL termination - Decrypt incoming requests and encrypt server responses so backend servers do not have to perform these potentially expensive operations
