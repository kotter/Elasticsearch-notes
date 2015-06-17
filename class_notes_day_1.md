Ports:

* HTTP:  the HTTP transport by default on ports 9200-9300 will automatically try and fine a free port within the range.
* Transport:  The internal node to node transport communication, by default on ports 9200-9400 (automatically try and find a free port
within the range).

Plugin Management:

Install: 
* from direct URL or file system path: bin/plugin install elasticsearch/marvel/latest
* from github: bin/plugin -install elasticsearch-marvel
* also from maven repo and download.elastic.co

Remove
* bin/plugin remove

2 types of plugins:
* site plugins: elasticsearch acting as a web-interface and serving up content
* code: as libraries that automatically get included under the main plugin directory

index: logical grouping of documents.  acts as a namespace which maps to one or more primary shards (primary lucine index) and can have zero or more replica shards.

shard: a shard is a single Apache Lucine instnace.  It is a low-level "worker" unit which is managed automatically.

Primary shard: An index can have one or more primary shards (defaults ro 5) and it is not possible to change this number after index creation.  when you index a document, it is first indexed on the primary shard, then on all replicas of this shard.

Replica shard: Each primary shard can have zero or more replicas (defaults to 1). Areplica is a copy of the primary shard, and serves two purposes:

  * Increase high availability - a replica is another copy of the data and will be promoted to a primary shard if the primary fails
  * Increase read throughput - get and search requestes can be handled by primary or replica shards.
