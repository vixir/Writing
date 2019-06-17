## Consistent Hashing

#### Distributed Hashing: 

In distributed hash function, keys and nodes map to same id space.

Hash functions assigns id.
Node : hash(ip)
key  : hash(key)

Let's assume we have a 6-bit id space. Total 64 ids.

How to map node Ids to key Ids? 
Use hash of ip.

Which nodes are responsible for storing which key?
Let's assume keyIds are stored in the next greater nodeId (anti-clockwise).

Example,
In our example keyId corresponding to id 60 will be assigned to node with id 1.
<img src="../assets/consistent_hashingA.svg" width="480"/>
- If node B is removed, all the ids between 1 and 32 will be assigned to C, which is almost half of the ids. This results in increase in load for one node.

- If a node E is added between D and A, previously assigned ids to A will be assigned to E. Every ids between 39 and 53 will be assigned to node E. This will result in one node being rehashed/modified. Repair time will be more, since in actual systems is will take significant amount of time to rehash a range of ids to a different nodes. Node will have a downtime to update all the id mappings.
Some nodes may become hot and some may become idle.

#### Consistent Hashing:

With Consistent hashing, all nodes receive roughly the same number of keys. When a node joins or leaves a network only a fraction of keys need to be moved to a different location. It allows us to distribute data across a cluster in such a way that will minimize reorganization when nodes are added or removed. Hence, the system will be easier to scale up or scale down.

In consistent hashing each server will be hashed by multiple hashing functions, 
For node A</br>
h1(A)%M=A1</br>
h1(A)%M=A2</br>
h1(A)%M=A3</br>
h1(A)%M=A4</br>
Similarly there will be virtual nodes(replicas) B1, B2, B3, B4, C1, C2, C3, C4, D1, D2, D3, D4 and E1, E2, E3, E4
Instead of mapping each node to a single point on ring, we have mapped nodes to multiple points.
So the likelihood of one server getting a lot of ids is much much lesser. When a node is added or removed only a fraction of ids need to be rehashed, reducing the downtime for id remappings.
