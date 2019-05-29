## HTTP Long Polling 
Client requests information from the server with the expectation that server will not immediately respond. Server will wait for updates on its side for *new* information to be available to respond to the client or for the timeout to occur. Server will only respond if there are any updates.
On receiving a response cilent immediately sends another request to restart the process again. Although it has a TTL, it is the responsiblity of the client to reconnect if connection is closed due to timeouts.

Issues:
1) Network issues may prevent messages from successfully being received. Unless some sort of message receipt confirmation is implemented, following calls to the server may result in missed responses. [ My take: May use kafka or some other messaging queues. They have commit offset where clients maintain offset information.]
2) One client sends confirmation on receiving response and server mistakenly believes that the message has been send. Other clients may miss that message.
3) Problems in scaling effectively. Subsequent requests from the client should be routed from the same server which received the initial request. Websockets are better for large scale applications. 

References:
1) https://blog.baasil.io/why-you-shouldnt-use-long-polling-fallbacks-for-websockets-c1fff32a064a
2) https://www.ably.io/concepts/long-polling
