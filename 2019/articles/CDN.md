## CDN
CDN is a highly distributed network of servers that delivers content of the website based on user's location.
It acts as an intermediary between the content network, known as origin and the user.
Ususally the site's data is stored in host's web server, the one where site is installed. If the traffic is more, then origin will be overloaded and websites/content users will experience latency while using the website.
CDNs also communicates with the main host server to update any content that has not been previously cached.

Initially, CDNs were just used for static website content(JS, CSS, HTML) and you had to push content to then as you have created it.
Many CDNs now cache website's "last alive" state, so that if orgin goes down, the CDN cache can still serve website's content.
Variety of contents can be served by CDN : videos, voice, e-commerce transactions, software downloads such as apps, OS updates, binaries.
Additional benifits include DDoS mitigation, uptime monitoring, security by using knowledge crowdsourced from it's clients. CDNs servers are quick to respond to a vulnerability, as they yhave most to lose (their customers).

When to use : 
 * Website is traffic heavy site.
 * Site Uses a lots of media items like images, audio and videos 
 * Visitors from all over the world
 * Issues with site performance

Reference:
  * https://www.akamai.com/us/en/cdn/what-is-a-cdn.jsp#what-is-a-cdn
  * https://www.sitepoint.com/what-is-a-cdn-and-how-does-it-work/
  * https://www.sitepoint.com/what-is-a-cdn-and-how-does-it-work/
