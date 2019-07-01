Tinder System Design
TINDER ARCHITECTURE

1) Store Profiles (Images) 5 images per user.
2) Add photos, bio, location.
3) Note Matches. Swipe data.
4) Direct Messaging.
5) Recommend matches based on distance range.

Don't take too many features.

How are you going to store images?
BLOB vs File System
x) Mutability
x) Transaction properties
x) Indexes
x) Access control

File System
1)Cheaper
1)Quality
1)CDN can be built on that
1)File Url

Distributed file system is going to handle image storing.
proflie_id | image_id || image_id |image_url

User logs in
Profile Service Stores in database
Update profile -> add photos
How do you make sure the person who is updating the profile is the right person to do so?
Use a Token

Image storage in separate service

XMPP way of talking between to machines
Messages should be pushed to client.
Peer to peer protocol.

Session Service
Store connection information.

Matcher service
UserId<->UserId

Recommendation
Filter -> Age, Gender, Interest (indexes), Location

I would suggest geo partition