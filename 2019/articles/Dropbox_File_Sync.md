Dropbox supports multiple clients, mobile, desktop, tablets, etc.

Possible ways:
1) Upload and commit files in database completely and sync across clients.
2) Stream sync, start syncing across clients while uploading in in progress.

How file is stored at Dropbox in it's file system : 
Each user has a root namespace, also every shared folder is also a namespace which is mounted with in root namespace.
Note that folders can be shared across multiple users.
Path will look like this in dropbox folder : user_namespace/shared_folder_namespace/file_name

File format:
Each file is partitioned to 4 mb blocks. These blocks are hashed with SHA-256 and stored. So, each file is a list of SHA-256 hashes known as 'blocklist'

Server File Journal Database:
Metadata server contains blocklist.
key columns :
1) NameSpace Id
2) Relative path
3) Blocklist
4) Journal ID (increasing within a namespace)
Two servers:
1) Metadata server : users, namespaces and Journal database
2) Block data server : key-value of hash -> file contents

Whenever a client wants to uploa

* Idle clients maintain a longpoll connection to a notification server.
<img src="https://dropboxtechblog.files.wordpress.com/2014/07/protocol61.png?w=492&zoom=2" width="480"/>
1) Upload and commit then sync.
a) File appears in block server.
b) Uploading client calls metaserver to check blocklist, if blocks are missing locally, we will get "need blocks"(nb) response
c) Uploading Client calls block server for the file contents.
d) After all the blocks are uploaded in system, metaserver replies with ok response and the lastest journalId. Now client knows that updates area available.
e) Now downloading client checks local system if these updates are already there. If not, client will download directly from block server.
<img src="https://dropboxtechblog.files.wordpress.com/2014/07/streamingsyncprotocol1.png?w=505&zoom=2" width="480"/>
2) Stream sync

References:
1) https://blogs.dropbox.com/tech/2014/07/streaming-file-synchronization/
2) An excellent talk is here: https://www.youtube.com/watch?v=PE4gwstWhmc
3) https://www.dropbox.com/developers/reference/namespace-guide
