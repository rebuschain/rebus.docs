---
description: 🖥🛠
icon: codespaces
order: 1000
---

# Rebusd Local Dev Setup

{% hint style="info" %}
These settings are only for development use of Rebus on a local machine.
{% endhint %}

Want to use `rebusd` locally for development, or to work with smart contracts? You're in the right place. Running locally is a much easier solution than interacting with a testnet.

This guide focusses on running the chain. If you want to build the binary or develop in go, then check out:

{% content-ref url="../validators/getting-setup.md" %}
[getting-setup.md](../validators/getting-setup.md)
{% endcontent-ref %}

## Using the Seed User

Rebus ships with an unsafe seed user in dev mode when you run the prebuilt docker container below, or one of the options that uses `docker-compose`. You can import this user into the CLI by using the mnemonic from the Rebus repo, i.e.:

```bash
rebusd keys add <unsafe-test-key-name> --recover
```

When prompted, add the mnemonic:

```
clip hire initial neck maid actor venue client foam budget lock catalog sweet steak waste crater broccoli pipe steak sister coyote moment obvious choose
```

You will then be returned an address to use: `rebus16g2rahf5846rxzp3fwlswy08fz8ccuwk03k57y`

## Run Rebus

There is a prebuilt docker image [for you to use](https://github.com/rebuschain/rebus.core/pkgs/container/rebus). This will start a container with a seeded user. The address and mnemonic used here can be found in the `docker/` directory of the repo. When you're done, you can use `ctrl+c` to stop the container running.

Always pick a tagged version to run, ideally one that matches mainnet. The example below may be outdated as Rebus releases frequently - you should check the [Rebus GitHub repository](https://github.com/rebuschain/rebus.core/releases) to see which is current for you.

```
docker run -it \
  --name rebus_node_1 \
  -p 26656:26656 \
  -p 26657:26657 \
  -e STAKE_TOKEN=urebusx \
  -e UNSAFE_CORS=true \
  ghcr.io/cosmoscontracts/rebus:v5.0.1 \
  ./setup_and_run.sh rebus16g2rahf5846rxzp3fwlswy08fz8ccuwk03k57y
```

## Quick(est) start dev build

The quickest way to get up-and-running for development purposes, as is documented in the main repo, is to run:

```bash
STAKE_TOKEN=urebusx UNSAFE_CORS=true docker-compose up
```

This builds and runs the node and:

* Creates and initialises a validator
* Adds a default user with a known address (`rebus16g2rahf5846rxzp3fwlswy08fz8ccuwk03k57y`)

To use a specific version of Rebus, check out a tag before running docker compose.

## Interacting with Rebus in Docker

To call Rebus inside a container, use `docker exec` like so:

```bash
# compile wasm - run this in your smart contract folder
docker run --rm -v "$(pwd)":/code \
  --mount type=volume,source="$(basename "$(pwd)")_cache",target=/code/target \
  --mount type=volume,source=registry_cache,target=/usr/local/cargo/registry \
  cosmwasm/rust-optimizer:0.12.6

# copy wasm to container
docker cp artifacts/your_compiled.wasm rebus_node_1:/your_compiled.wasm

# store wasm
docker exec -i rebus_node_1 \
  rebusd tx wasm store "/your_compiled.wasm" \
  --gas-prices 0.1urebusx --gas auto --gas-adjustment 1.3 \
  -y -b block --chain-id testing \
  --from validator --output json 
```

## Quickstart on the testnet with a public node

If you don't want to go through the process of setting up a node and just want to experiment with the Rebus uni testnet:

1. Get a public node's RPC address.
2. In `~/.rebus/config/client.toml` set `node="<public node RCP address>"` and `chain-id="uni-2"`.
3. Create a key to use by running `rebusd keys add <key-name>`.
4. Get that key's public address by running `rebusd keys show <key-name> -a`.
5. Get some test Rebus by sending `$request <key-address>` in the #faucet Discord channel.

You can then verify that you have funds by running `rebusd query bank balances <key-address>`. Happy hacking!
