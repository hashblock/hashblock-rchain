# Dockerfiles

There dockerfiles simplify deployment to Kubernetes.

- testnet/Dockerfile for building a RChain testnet node.
- bootstrap/Dockerfile for building a RChain bootstrap node.

## Build

Build from repo root directory.

- `docker build -f Dockerfile -t hashblock/rchain-testnet-node:latest .`
- `docker build -f Dockerfile -t hashblock/rchain-bootstrap-node:latest .`

## Environment Variables

- `private_key` = Private key from Node [Test Session Sheet](https://docs.google.com/spreadsheets/d/18merD3OzaDk7nmxQ78SUZBzWLbxA-aOnmcdxpXrp_U0/edit#gid=0)
- `public_key` = Public key from Node [Test Session Sheet](https://docs.google.com/spreadsheets/d/18merD3OzaDk7nmxQ78SUZBzWLbxA-aOnmcdxpXrp_U0/edit#gid=0)
- `bootstrap_address` = Bootstrap address from the [Rchain Wiki](https://rchain.atlassian.net/wiki/spaces/CORE/pages/501842019/RNode+bootstrap+addresses)
- `standalone` = True or False (default is False)
- `port` = Adjust default communication port (default 40400)
- `http_port` = Adjust HTTP port (default 40402)
- `metrics_port` = Adjust metrics port (default 40403)
- `grpc_host` = Adjust gRPC host (default localhost)
- `grpc_port` = Adjust gRPC port (default 40401)

## Docker Quick Start

Replace the -e items with the appropriate environment variables listed above.

`sudo docker run -it -p 40400:40400 -e private_key=REPLACE -e public_key=REPLACE -e bootstrap_address=REPLACE blockgencorp/rnode:latest`

## Kubernetes Tips & Trick

Your pod security policy should allow Hosts Port 40400 at a minimum.

You need to add a HostPort for 40400 on the specific workload otherwise you'll get a connection interrupted or timeout error from RNode's java application. RNode's upnp setting will not help you here, just setup the HostPort.

If you are looking to run multiple RNodes then wouldn't want to run more than 1 container per priv/pub key pair.