Dropbox APIs
Notes on Drobbox

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

#1 High-Level architecture

Client will have workspace in their device.

We need Cloud Storage -> to keep file information
Metadata storage -> Files, Folders, file size, directory

Servers to upload/download content
Servers to update metadata.
Synchronization server -> to update other clients


file_namespace 
blockList
journal_id


User -> client_id_list
User -> file_namespace_list
