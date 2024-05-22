# Running a local Graph Node and Hardhat node for subgraph development

### Installation prerequisites

* [Docker](https://docs.docker.com/get-docker/)
* [Node.js](https://nodejs.org/en/download/package-manager)
* [Graph CLI](https://www.npmjs.com/package/@graphprotocol/graph-cli)
* [Hardhat](https://hardhat.org/hardhat-network/docs/overview#running-stand-alone-in-order-to-support-wallets-and-other-software)

### Getting started

```bash
# Clone the Graph Node repository
git clone https://github.com/graphprotocol/graph-node.git

# Run Hardhat in standalone mode
npx hardhat node
 
# Start IPFS, PostgreSQL, and Graph Node
cd graph-node
docker-compose up

# Create a subgraph. 
# Replace <CONTRACT_ADDRESS> with the address of the smart contract you want to index
# Replace <GITHUB_USERNAME>/<SUBGRAPH_NAME> with your GitHub username and subgraph name.
graph init --from-contract <CONTRACT_ADDRESS> --network mainnet <GITHUB_USERNAME>/<SUBGRAPH_NAME>

# Define your subgraph manifest, GraphQL schema, and AssemblyScript mappings

# Deploy subgraph locally
graph deploy <GITHUB_USERNAME>/<SUBGRAPH_NAME> --node http://127.0.0.1:8020 --ipfs http://127.0.0.1:5001
```
