---
description: General instructions on how to join the Rebus testnets
order: 997
icon: /public/assets/testnet.png
---

# Joining Testnets

## Current testnets

Below is the list of Rebus testnets and their current status. You will need to know the version tag for installation of the `rebusd` binary.

For details of upgrades on the current testnet, as well as syncing, you can [check out the testnets repo, which is the definitive source of truth](https://github.com/rebuschain/rebus.testnet).

If you get stuck, then please ask on Discord.

| chain-id | Current Github version tag |             Description            | Status  |
| -------- | -------------------------- | :--------------------------------: | ------- |
| reb_3333-1    | v1.0.0                | Testing Rebus platform. | current |

## Minimum Hardware Requirements

The minimum recommended hardware requirements for running a validator for the Rebus testnets are:

| Chain-id | Requirements                                                                          |
| -------- | ------------------------------------------------------------------------------------- |
| reb_3333-1    | <ul><li>16GB RAM</li><li>200GB of disk space</li><li>at least 2 cores cpu</li></ul> |

{% hint style="warning" %}
These specifications are the minimum recommended. As Rebus Network is a smart contract platform, it can at times be very demanding on hardware. Low spec validators WILL get stuck on difficult to process blocks.
{% endhint %}

{% hint style="info" %}
Note that the testnets accumulate data as the blockchain continues. This means that you will need to expand your storage as the blockchain database gets larger with time.
{% endhint %}

## rebusd Installation

To get up and running with the rebusd binary, please follow the instructions [here](getting-setup.md)

## Configuration of Shell Variables

For this guide, we will be using shell variables. This will enable the use of the client commands verbatim. It is important to remember that shell commands are only valid for the current shell session, and if the shell session is closed, the shell variables will need to be re-defined.

If you want variables to persist for multiple sessions, then set them explicitly in your shell .profile, as you did for the Go environment variables.

To clear a variable binding, use `unset $VARIABLE_NAME` . Shell variables should be named with ALL CAPS.

### Choose a testnet

Choose the `<chain-id>` testnet you would like to join from [here](joining-the-testnets.md#current-testnets). Set the `CHAIN_ID`:

```bash
CHAIN_ID=<chain-id>

#Example
CHAIN_ID=reb_3333-1
```

### Set your moniker name

Choose your `<moniker-name>`, this can be any name of your choosing and will identify your validator in the explorer. Set the `MONIKER_NAME`:

```bash
MONIKER_NAME=<moniker-name>

#Example
MONIKER_NAME="ValidatorT1000"
```

### **Set persistent peers**

Active and running peers will be required to tell your node where to connect to other nodes and join the network. To retrieve the peers for the Rebus testnet:

```bash
#Set the base repo URL for the testnet & retrieve peers
CHAIN_REPO="https://raw.githubusercontent.com/rebuschain/rebus.testnet/master" && \
export PEERS="$(curl -s "$CHAIN_REPO/seeds.txt")"

# check it worked
echo $PEERS
```

{% hint style="info" %}
NB: If you are unsure about this, you can ask in discord for the current peers and explicitly set them in `~/.rebusd/config/config.toml` instead.
{% endhint %}

### Set minimum gas prices

In `$HOME/.rebus/config/app.toml`, set gas minimum prices:

```
# note testnet denom
sed -i.bak -e "s/^minimum-gas-prices *=.*/minimum-gas-prices = \"0.0008arebus\"/" ~/.rebus/config/app.toml
```

## Setting up the Node

{% hint style="info" %}
Running a node is different from running a Validator. In order to run a Validator, you must create and sync a node, and then upgrade it to a Validator.
{% endhint %}

These instructions will direct you on how to initialise your node, synchronise to the network and upgrade your node to a validator.

### **Initialize the chain**

```bash
rebusd init $MONIKER_NAME --chain-id $CHAIN_ID
```

This will generate the following files in `~/.rebusd/config/`

* `genesis.json`
* `node_key.json`
* `priv_validator_key.json`

{% hint style="info" %}
Note that this means if you jumped ahead and already downloaded the genesis file, this command will replace it and you will get an error when you attempt to start the chain.
{% endhint %}

### Download the genesis file

```
curl https://raw.githubusercontent.com/rebuschain/rebus.testnet/master/genesis.json > ~/.rebusd/config/genesis.json
```

This will replace the genesis file created using `rebusd init` command with the genesis file for the testnet. \*\*\*\*

### **Set persistent peers**

Using the peers variable we[ set earlier](joining-the-testnets.md#set-persistent-peers), we can set the `persistent_peers` in `~/.rebus/config/config.toml`:

```bash
sed -i.bak -e "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" ~/.rebus/config/config.toml
```

### **Create a local key pair**

Create a new key pair for your validator:

```bash
rebusd keys add <key-name> --coin-type 118 --algo secp256k1

# Query the keystore for your public address
rebusd keys show <key-name> -a
```

Replace `<key-name>` with a key name of your choosing.

If you already have a key from a previous testnet, you can recover it using the mnemonic:

```bash
rebusd keys add <key-name> --recover  --coin-type 118 --algo secp256k1
```

The key is Keplr and Keplr+Ledger wallet compatible. (type=118 algo=secp256k1)

{% hint style="danger" %}
After creating a new key, the key information and seed phrase will be shown. It is essential to write this seed phrase down and keep it in a safe place. The seed phrase is the only way to restore your keys.
{% endhint %}

### **Get some testnet tokens**

Testnet tokens can be requested from the `#faucet` channel on [Discord](https://discord.gg/tqfSntHxvv).

To request tokens type `$request <your-public-address>` in the message field and press enter.

## Setup cosmovisor

Follow [these](setting-up-cosmovisor.md) instructions to setup cosmovisor and start the node.

## Syncing the node

After starting the rebusd daemon, the chain will begin to sync to the network. The time to sync to the network will vary depending on your setup, but could take a very long time. To query the status of your node:

```bash
# Query via the RPC (default port: 26657)
curl http://localhost:26657/status | jq .result.sync_info.catching_up
```

If this command returns `true` then your node is still catching up. If it returns `false` then your node has caught up to the network current block and you are safe to proceed to upgrade to a validator node.

{% hint style="info" %}
Validators and sentries can rapidly join the network with state-sync. See instructions for using state-sync [here](joining-the-testnets.md#undefined).
{% endhint %}

## Upgrade to a validator

To upgrade the node to a validator, you will need to submit a `create-validator` transaction:

```bash
rebusd tx staking create-validator \
  --amount 9000000arebus \
  --commission-max-change-rate "0.1" \
  --commission-max-rate "0.20" \
  --commission-rate "0.1" \
  --min-self-delegation "1" \
  --details "validators write bios too" \
  --pubkey=$(rebusd tendermint show-validator) \
  --moniker $MONIKER_NAME \
  --chain-id $CHAIN_ID \
  --gas-prices 0.0025arebus \
  --from <key-name>
```

## Backup critical files

There are certain files that you need to backup to be able to restore your validator if, for some reason, it damaged or lost in some way. Please make a secure backup of the following files located in `~/.rebus/config/`:

* `priv_validator_key.json`
* `node_key.json`

It is recommended that you encrypt the backup of these files.
