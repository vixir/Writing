## Load Balancer
What is it?
In a distributed system in order to distribute traffic across different available servers to improve responsiveness and availability of applications, databases.
Load Balancing can be done between users and websites, applications and database servers, applications and cache servers.

Why do we need it?
Faster, high availability 
Flexibility to scale servers independently.
Shifting DDoS attack traffic from corporate server to cloud server using off-loading function.
Dynamic application startup on more loads.

How to we do it?
Pre Configured Algorithms
- Least connection method : Server with least active connections gets priority.
- Least Response Time Method : Directs request to servers with least response time.
- Round Robin Method : Rotates requests among available servers.
- IP hash : Directs request based on hash of IP address.
- Weighted Round Robin : 

Load Balancer should only forward request to "healthy" servers. If a server is not "healthy" it should be removed from consideration.
Load balancers have different capabilities, which include:
L4 — directs traffic based on data from network and transport layer protocols, such as IP address and TCP port.
L7 — adds content switching to load balancing. This allows routing decisions based on attributes like HTTP header, uniform resource identifier, SSL session ID and HTML form data.

Cons:
Single point of failure. 
Solution:
Clustering of load balancers.Each Load Balancer monitors health of other.

References :
https://avinetworks.com/what-is-load-balancing/