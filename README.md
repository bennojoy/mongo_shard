mongo_shard
-----------

This roles helps to enable sharding in a mongodb cluster. 

In addition to this role if combined with other roles like mongo_mongod, mongo_mongos, mongo_mongoc this can used to 
build a production grade mongodb cluster with multi replication master and shards.
  

Requirements
------------

This role requires ansible 1.4 or higher and platform requirements are listed in the metadata file.

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows:

    mongo_shard_list:           # A list of hostname/port/repl_setname to enable sharding.
     - replset_name: foo
       hostname: bar
       port: 2801
    mongos_port: 2900           # The port where the monogos daemon is running.
    mongoc_admin_pass: foobar   # The mongoc admin password


Examples
--------

1) Eg: Enable Sharding on three replica set hosts


    - hosts: all
      roles:
        - role: bennojoy.mongo_shard
          mongo_shard_list:
          - replset_name: rs0
            hostname: ubuntu13
            port: 2701
          - replset_name: rs1
            hostname: ubuntu14
            port: 2701
          - replset_name: rs2
            hostname: ubuntu15
            port: 2701
          mongos_port: 2900
          mongoc_admin_pass: foobar


2) Eg: Enable Sharding on three hosts which is not replicated


    - hosts: all
      roles:
        - role: bennojoy.mongo_shard
          mongo_shard_list:
           - hostname: ubuntu13
             port: 2701
           - hostname: ubuntu14
             port: 2701
           - hostname: ubuntu15
             port: 2701
          mongos_port: 2900
          mongoc_admin_pass: foobar


Dependencies
------------

None

License
-------

BSD

Author Information
------------------

Benno Joy
 

