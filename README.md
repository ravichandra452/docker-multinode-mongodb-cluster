This sets up a 3-node docker mongodb cluster. Replace hostname1, hostname2, and hostname3 with the actual server hostnames in the docker-compose.yaml file.

Run docker stack deploy -c docker-compose.yaml --with-registry-auth mongo to set up the cluster.

login to one of the mongodb container and execute below command to initiate the mongodb cluster and do rs.status() to check the cluster status

rs.initiate(
   {
      _id: "rs6",
      version: 1,
      members: [
         { _id: 0, host : "mongo-0:27017" },
         { _id: 1, host : "mongo-1:27017" },
         { _id: 2, host : "mongo-2:27017" }
      ]
   }
)

The config will be automatically persisted to disk as we exposed host volume to /data/db of mongodb directory
