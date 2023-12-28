# Bitcoin core containerization

## Install

- clone the repo

```shell
git clone https://github.com/oneforalone/bitcoin-core-docker.git
cd bitcoin-core-docker
```

- Generate rpcauth via rpcauth.py

```shell
./rpcauth.py <username> <password>
```

append the `rpcauth=<username>:<token>` line to `bitcoin/bitcoin.conf` file.

On Unix like system, using pipeline:

```shell
./rpcauth.py <username> <password> | grep "^rpcauth" | tee -a bitcoin/bitcoin.conf
```

- start

```shell
docker compose up -d # or `docker-compose up -d` if you're not using Docker Desktop
```

## Building new version

```shell
docker buildx build --tag oneforalonee/bitcoind:v26.0 --build-arg="BITCOIN_VERSION=<version_number>" .
```

Ensure the version is downloadable from https://bitcoincore.org/en/download/
