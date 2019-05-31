## Consistent Hashing

#### Distributed Hashing: 

In distributed hash function, keys and nodes map to same id space.

Nodes have ids and keys also have ids on the same space.

Hash functions assigns id.
Node : hash(ip)
key  : hash(key)

Let's assume we have a 6-bit id space. Total 64 ids.

How to map node Ids to key Ids. Which nodes are responsible for storing which key. Let's assume keyIds are stored in the next greater nodeId (anti-clockwise).
In our example keyId corresponding to id 60 will be assigned to node with id 1.


- If node B is removed, all the ids between 1 and 32 will be assigned to C, which is almost half of the ids. This results in increase in load for one node.

- If a node E is added between D and A, previously assigned ids to A will be assigned to E. Every ids between 39 and 53 will be assigned to node E. This will result in one node being rehashed/modified. Other nodes are not effected  by it. Repair time will be more, since in actual systems is will take significant amount of time to rehash a range of ids to a different nodes.
Node will have a downtime to update all the id mappings.

Some nodes my become hot and some may become idle.

#### Consistent Hashing:

With Consistent hashing, all nodes receive roughly the same number of keys. When a node joins or leaves a network only a fraction of keys need to be moved to a different location.

In consistent hashing each server will be hashed by multiple hashing functions, 
For node A
h1(A)%M=A1
h1(B)%M=A2
h1(C)%M=A3
h1(D)%M=A4

Instead of mapping each node to a single point on ring, we can map nodes to multiple points. 

So the likelihood of one server getting a lot of ids is much much lesser.
