## Domain Name System (DNS)

A DNS(Domain Name System) maps domain name such as www.google.com to an IP address.

DNS data is distributed, it's potential size is unlimited and performance is not degraded when more servers are added.
Server follows hierarchical architecture.

Whenever we try to access a website from browser, it tries to resolve IP address from the Local Cache (Browser Cache/OS cache/ISP cache).
Cache's expiry time is determined by time to live (TTL).

If it can't be resolved by using local cache, then a request is sent to Root Server from the resolver.
Resolver uses DNS Domain Namespace, which is the structure of domain that combines to form a complete domain name.
We all know that Domain name consists of individual labels separated by dots (www.github.com).

Root server sends the request to Domain Server which uses Top level Domain Namespace(com, edu, in, org) to delegate request to Authoritative Server which resolves the ip address and sends it back to the browser.
Cloudflare and Amazon's Route 53 provides managed DNS services that allows users to manage their DNS traffic.  

![Alt](assets/DNS.drawio)
#### Recursive and Iterative resolution.
  * In recursive resolution once a request is sent to the root server, root server in turns sends the request till it reaches authoritative server and response is reverted back to the browser.
  * In Iterative resolution browser receives a response from root server and then browser in turn uses the response and sends a request to authoritative server which returns a response to the browser. 
  
  
Reference:
* https://github.com/donnemartin/system-design-primer#domain-name-system
* https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd197427(v=ws.10)
* https://www.youtube.com/watch?v=vhfRArT11jc
* https://www.youtube.com/watch?v=BZISxpdl4lQ
    