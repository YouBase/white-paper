# DHT

Distributed Hash tables are a decentralized, distributed system for storing key/value pairs where any node in the network can efficiently retrieve a value given a certain key. Ability to mapy keys to values is distributed among the nodes, such that changes to participating nodes is minimally disruptive.

From Wikipedia: 

"The structure of a DHT can be decomposed into several main components.[8][9] The foundation is an abstract **keyspace**, such as the set of 160-bit strings. A **keyspace partitioning scheme** splits ownership of this keyspace among the participating nodes. **An overlay network** then connects the nodes, allowing them to find the owner of any given key in the keyspace.

Once these components are in place, a typical use of the DHT for storage and retrieval might proceed as follows. Suppose the keyspace is the set of 160-bit strings. To store a file with given filename and data in the DHT, the SHA-1 hash of filename is generated, producing a 160-bit key k, and a message put(k, data) is sent to any node participating in the DHT. The message is forwarded from node to node through the overlay network until it reaches the single node responsible for key k as specified by the keyspace partitioning. That node then stores the key and the data. Any other client can then retrieve the contents of the file by again hashing filename to produce k and asking any DHT node to find the data associated with k with a message get(k). The message will again be routed through the overlay to the node responsible for k, which will reply with the stored data."