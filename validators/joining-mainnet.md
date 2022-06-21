---
description: General instructions to join the Rebus mainnet after network genesis.
order: 996
icon: /public/assets/join.png
---

# Joining Mainnet

## Mainnet binary version

The correct version of the binary for mainnet at genesis is `v1.0.0`. Its release page can be found [here](https://github.com/rebuschain/rebus.core/releases/tag/v1.0.0).

{% hint style="danger" %}
Note that because of the Lupercalia upgrade, you will need to sync a node from after the Lupercalia upgrade block, 2578099. To sync to this version, follow the guide in 'Syncing after Lupercalia'.
{% endhint %}

## Mainnet chain-id

Below is the list of Rebus mainnet id's and their current status. You will need to know the version tag for installation of the `rebusd` binary.

| chain-id | Description                                        |  Status | Block Start | Block Finish |
| -------- | -------------------------------------------------- | :-----: | ----------- | ------------ |
| reb_1111-1   | This is the first chain-id from the genesis. | current | 0           | N/A          |

## Recommended Minimum Hardware

The minimum recommended hardware requirements for running a validator for the Rebus mainnet are:

| Chain-id | Requirements                                                                                   |
| -------- | ---------------------------------------------------------------------------------------------- |
| reb_1111-1   | <ul><li>4 Cores (modern CPU's)</li><li>32GB RAM</li><li>1TB of storage (SSD or NVME)</li></ul> |

{% hint style="danger" %}
These specifications are the minimum recommended. As Rebus Network is a smart contract platform, it can at times be very demanding on hardware. Low spec validators WILL get stuck on difficult to process blocks.
{% endhint %}

{% hint style="warning" %}
Note that the mainnet will accumulate data as the blockchain continues. This means that you will need to expand your storage as the blockchain database gets larger with time.
{% endhint %}

## Rebusd Installation

To get up and running with the rebusd binary, please follow the instructions [here](getting-setup.md).

{% hint style="warning" %}
Mainnet will initially use the `v1.0.0` [tag](https://github.com/rebuschain/rebus.core/releases/tag/v1.0.0) on GitHub. Make sure you build [this version](https://github.com/rebuschain/rebus.core/tree/v1.0.0) of the Rebus binary.
{% endhint %}

## Configuration of Shell Variables

For this guide, we will be using shell variables. This will enable the use of the client commands verbatim. It is important to remember that shell commands are only valid for the current shell session, and if the shell session is closed, the shell variables will need to be re-defined.

If you want variables to persist for multiple sessions, then set them explicitly in your shell .profile, as you did for the Go environment variables.

To clear a variable binding, use `unset $VARIABLE_NAME` . Shell variables should be named with ALL CAPS.

### Choose the required mainnet chain-id

Choose the `<chain-id>` for the mainnet you would like to join from [here](joining-mainnet.md#mainnet-chain-id). Set the `CHAIN_ID`:

```bash
CHAIN_ID=<chain-id>

# Example
CHAIN_ID=reb_1111-1
```

You can also set this in your `.profile` file:

```bash
export CHAIN_ID=reb_1111-1
```

Then source it:

```bash
source .profile
```

### Set your moniker name

Choose your `<moniker-name>`, this can be any name of your choosing and will identify your validator in the explorer. Set the `MONIKER_NAME`:

```bash
MONIKER_NAME=<moniker-name>

# Example
MONIKER_NAME="ValidatorT1000"
```

### **Setting the  peers**

Active and running peers will be required to tell your node where to connect to other nodes and join the network. To retrieve the peers for the chosen mainnet:

```bash
#Set the base repo URL for the testnet & retrieve peers
CHAIN_REPO="https://raw.githubusercontent.com/rebuschain/rebus.mainnet/master" && \
export PEERS="$(curl -s "$CHAIN_REPO/seeds.txt")"

# check it worked
echo $PEERS
```
{% hint style="info" %}
NB: If you are unsure about this, you can ask in discord for the current peers and explicitly set them in `~/.rebus/config/config.toml` instead.
{% endhint %}

### Set minimum gas prices

In `$HOME/.rebus/config/app.toml`, set minimum gas prices:

```
sed -i.bak -e "s/^minimum-gas-prices *=.*/minimum-gas-prices = \"0.0008arebus\"/" ~/.rebus/config/app.toml
```

{% hint style="info" %}
The above configuration will set the validator to accept both `urebus` and `IBC Atom` as fees for transactions
{% endhint %}

## Setting up the Node

These instructions will direct you on how to initialize your node, synchronize to the network and upgrade your node to a validator.

### **Initialize the chain**

```bash
rebusd init $MONIKER_NAME --chain-id $CHAIN_ID
```

This will generate the following files in `~/.rebusd/config/`

* `genesis.json`
* `node_key.json`
* `priv_validator_key.json`

### Download the genesis file

```
curl https://raw.githubusercontent.com/rebuschain/rebus.mainnet/master/genesis.json > ~/.rebusd/config/genesis.json
```

This will replace the genesis file created using `rebusd init` command with the mainnet `genesis.json`. \*\*\*\*

### **Setting the peers**

Using the peers variable we set earlier, we can set the `seeds` in `~/.rebusd/config/config.toml`:

```bash
sed -i.bak -e "s/^seeds *=.*/seeds = \"$PEERS\"/" ~/.rebusd/config/config.toml
```

### **Create (or restore) a local key pair**

Either create a new key pair, or restore an existing wallet for your validator:

```bash
# Create new keypair
rebusd keys add <key-name> --coin-type 118 --algo secp256k1

# Restore existing rebus wallet with mnemonic seed phrase.
# You will be prompted to enter mnemonic seed.
rebusd keys add <key-name> --recover --coin-type 118 --algo secp256k1

# Query the keystore for your public address
rebusd keys show <key-name> -a
```

Replace `<key-name>` with a key name of your choosing.


{% hint style="danger" %}
After creating a new key, the key information and seed phrase will be shown. It is essential to write this seed phrase down and keep it in a safe place. The seed phrase is the only way to restore your keys.
{% endhint %}

### **Get some Rebus tokens**

You will require some Rebus tokens to bond to your validator. To be in the active set you will need to have enough tokens to be in the top 125 validators by delegation weight.

If you do not have any Rebus tokens for you validator you can purchase tokens [here](https://www.rebuschain.com/where).

## Setup cosmovisor

Follow [these](setting-up-cosmovisor.md) instructions to setup cosmovisor and start the node.

{% hint style="info" %}
Using cosmovisor is completely optional. If you choose not to use cosmovisor, you will need to be sure to attend network upgrades to ensure your validator does not have downtime and get jailed.
{% endhint %}

## Syncing the node

After starting the rebusd daemon, the chain will begin to sync to the network. The time to sync to the network will vary depending on your setup and the current size of the blockchain, but could take a very long time. To query the status of your node:

```bash
# Query via the RPC (default port: 26657)
curl http://localhost:26657/status | jq .result.sync_info.catching_up
```

If this command returns `true` then your node is still catching up. If it returns `false` then your node has caught up to the network current block and you are safe to proceed to upgrade to a validator node.

## Upgrade to a validator

{% hint style="danger" %}
**Do not attempt to upgrade your node to a validator until the node is fully in sync as per the previous step.**
{% endhint %}

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

{% hint style="info" %}
The above transaction is just an example. There are many more flags that can be set to customise your validator, such as your validator website, or keybase.io id, etc. To see a full list:

```bash
rebusd tx staking create-validator --help
```
{% endhint %}

## Backup critical files

There are certain files that you need to backup to be able to restore your validator if, for some reason, it damaged or lost in some way. Please make a secure backup of the following files located in `~/.rebus/config/`:

* `priv_validator_key.json`
* `node_key.json`

It is recommended that you encrypt the backup of these files.


