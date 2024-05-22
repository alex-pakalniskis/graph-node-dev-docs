# Running a local Graph Node for subgraph development

### Prerequisites

* Install [Docker](https://docs.docker.com/get-docker/)

### Getting started

```bash
# Download docker-compose.yml for Graph Node & dependencies
git clone https://github.com/graphprotocol/graph-node.git

# Modify docker-compose.yml with your JSON RPC endpoint(s) for your network(s) of interest and save the changes
nano docker/docker-compose.yml
 
# Start IPFS, PostgreSQL, and Graph Node
docker-compose up
```



***

Existing content

* [https://github.com/graphprotocol/graph-node/blob/master/README.md#running-a-local-graph-node](https://github.com/graphprotocol/graph-node/blob/master/README.md#running-a-local-graph-node)
* [https://github.com/graphprotocol/graph-node/blob/master/docker/README.md](https://github.com/graphprotocol/graph-node/blob/master/docker/README.md)
* [https://github.com/graphprotocol/graph-node/blob/master/docs/getting-started.md](https://github.com/graphprotocol/graph-node/blob/master/docs/getting-started.md)
* [https://github.com/graphprotocol/graph-node/blob/master/docs/config.md](https://github.com/graphprotocol/graph-node/blob/master/docs/config.md)
