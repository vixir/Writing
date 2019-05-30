Users can share photos and videos with other users.
Follow other users.
Timeline (sorted order). Timeline should contain stories shares by followed users.
Shared content should be visible on followers' timeline.



Upload Photos
Download/View Photos (Client)
If user is not able to see photos shared for a while it should be okay. Availability is important.

500M users 
3M daily users

1M new photos every day.
assuming 300 kb per pic
3M*1M = 4GB
5 Years ~ 730 TB


High Level Design:

We need different servers for upload and download. Uploading takes more time. If uploading and downloading are together, uploading will consume bandwidth required by server. Limited connections by an application. We can scale these servers separately. Separate db for storing metadata and images.


Upload<------Upload Image---------->[Upload Server]<------------------>Image Server
													\__________________/___________\
													 \				  /	      		\
Download<----Download Image---------->[Image hosting Download Server]<-------------> Metadata Server

DB schema 	SQL/NO-SQL (Since I know Instagram uses Postgre SQL, I'll try to justify it :)....)

Photos    			Users 				Followers				Following
PhotoId [PK]		UserId [PK]			user_id (FK)			user_id
photo_url			email				follower_id				following_id
photo_location		age
upload_date			password
					email
					twitter_id
					facebook_id
					profile_pic_url

If we are using cassandra https://www.datastax.com/dev/blog/we-shall-have-order will help in ordering. Partition Key(user_id, year) and clustering key timestamp DESC. Clustering columns determine the on-disk sort order within each partition.

Data Size Per Day:
Based on schema you came up with.
Total space required by all tables, etc.

Services, db can failover to a healthy copy.


Most Important : My opinion

1) Data Sharding
2) Timeline


