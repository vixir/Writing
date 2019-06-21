Notes on Drobbox

Requirements:
1) Upload and download files.
2) Sync client folders.

To handle file transfer efficiently, divide them into blocks. 
At dropbox each file is divided into chunks/blocks of 4mb each with final block having less size than the others. These blocks are hashed with SHA256 and stored. File contents can be identified by using list of hashes or 'blocklist'.

------------------------------------------------------
                    video.avi (14 mb)
------------------------------------------------------
|     4 mb    |     4 mb    |     4 mb    |   2 mb   |
------------------------------------------------------
      h1             h2           h3           h4

Dropbox server types
Block data server: Maintains a key-value store of hash to encrypted contents. No knowledge of users/files/how those blocks fit together.
Metadata server : Maintains database of users, file metadata, chunk info
Synchronization server : Sync files across different client systems

Client design
What metadata client needs?
file_info
----------
file_namespace
namespace_relative_path
block_list
file_version

Sync service will call metadata server to update metadata database when it syncs across different devices.

Google infracture and use them.
Can't start with final solution.
Users can change files and access it anywhere.
10s of millions users per day.
100 millions sync per day.

Client

Challenges:
Everyone's computer has a complete copy of entire dropbox. Multi PBytes cache in front of service.
1) Write volume?
Read to write ratio is 1:1.
2) ACIDity requirements.
 Deleted file should be deleted for all.
 Video can't be half than that which is stored.

What is dropbox?

Examples : How dropbox evolved?

We need Cloud Storage -> to keep file information
Metadata storage -> Files, Folders, file size, directory

Servers to upload/download content
Servers to update metadata.
Synchronization server -> to update other clients

Suppose we have downloaded dropbox in a new client machine, say android phone. How will it sync data?
user                user_namespace_mapping
----                --------                         
userId               parent_namespace
email                child_namespace(file/folder_namespace)
user_namespace

file_info
----------
file_namespace
namespace_relative_path
block_list
file_version

