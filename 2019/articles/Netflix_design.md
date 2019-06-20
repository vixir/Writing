Netflix stack

Streaming service


Design Netflix

Functionalities :

1) Soeone should be able to upload content
2) Users can search for movies.
3) Should be able to select from a list of results.
4) Users can stream videos. Server side.
5) Service should support multiple devices.

Non-Functional Requirements :
1) Content search should be fast.
2) Streaming video should not lag.
3) Several users should be able to access the content at the same time.

Capacity Assumptions : 
1) 1 Billion total users
   60 millions would be accessing daily
   2 videos per day 
   (120 000 000/ 86400 sec) => 1.2K videos streaming/sec <- active connections
   
   Upload 100 videos uploading/sec

   1 sec of video takes about 100 mb
   3000000 MB/s
   3000 GB/s

Video sotrage required : 3000 * 86400 = 300 PB

   Dowloading/Streaming
   60000 GB/s
   60 TB/s

1 min of video needs 50 MB

46000

Ignoring different codecs/resolution/compression/replication

Service APIs :

We should be exposing APIs so that our client applications would be calling them.

Used by client application for Operator to upload a video (Operator will be our client):
(video_title, video_description, tags[], category_id, default_language, recording_details, video_contents)

returns HTTP 202 (request accepted).

A media stream from the given offset.
