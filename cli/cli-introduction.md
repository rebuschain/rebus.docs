---
description: >-
  A general introduction Rebus cli along with a brief description of commands and
  flags
---

# Introduction

## Introduction

`rebusd` is a command line client for the Rebus network. Rebus users can use `rebusd` to send transactions to the Rebus network and query the blockchain data.

{% hint style="info" %}
See [here](../validators/getting-setup.md) for instructions on installing `rebusd`.
{% endhint %}

### Working Directory <a href="#working-directory" id="working-directory"></a>

The default working directory for the `rebusd` is `$HOME/.rebus`, which is mainly used to store configuration files and blockchain data. The Rebus `key` data is saved in the working directory of `rebusd`. You can also specify the `rebusd` working directory by using the `--home` flag when executing `rebusd`.&#x20;

### Connecting to a Full-Node

By default, `rebusd` uses `tcp://localhost:26657` as the RPC address to connect to the Rebus network. This default configuration assumes that the machine executing `rebusd` is running as a full-node.

The RPC address can be specified to connect to any full-node with an exposed RPC port by adding the `--node` flag when executing `rebusd`

### Global Flags <a href="#global-flags" id="global-flags"></a>

#### GET Commands <a href="#get-commands" id="get-commands"></a>

All GET commands have the following global flags:

| Name, shorthand | type   | Required | Default Value | Description                          |
| --------------- | ------ | -------- | ------------- | ------------------------------------ |
| --chain-id      | string |          |               | The network Chain ID                 |
| --home          | string |          | $HOME/.rebus   | Directory for config and data        |
| --trace         | string |          |               | Print out full stack trace on errors |
| --log\_format   | string |          | plain         | Logging format (json \| plain)       |

#### POST Commands <a href="#post-commands" id="post-commands"></a>

All POST commands have the following global flags:

| Name, shorthand   | type   | Required | Default               | Description                                                                                                    |
| ----------------- | ------ | -------- | --------------------- | -------------------------------------------------------------------------------------------------------------- |
| --account-number  | int    |          | 0                     | AccountNumber to sign the tx                                                                                   |
| --broadcast-mode  | string |          | sync                  | Transaction broadcasting mode (sync \| async \| block)                                                         |
| --dry-run         | bool   |          | false                 | Ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it                        |
| --fees            | string |          |                       | Fees to pay along with transaction                                                                             |
| --from            | string |          |                       | Name of private key with which to sign                                                                         |
| --gas             | string |          | 200000                | Gas limit to set per-transaction; set to "simulate" to calculate required gas automatically                    |
| --gas-adjustment  | float  |          | 1                     | Adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set |
| --gas-prices      | string |          |                       | Gas prices in decimal format to determine the transaction fee                                                  |
| --generate-only   | bool   |          | false                 | Build an unsigned transaction and write it to STDOUT                                                           |
| --help, -h        | string |          |                       | Print help message                                                                                             |
| --keyring-backend | string |          | os                    | Select keyring's backend                                                                                       |
| --ledger          | bool   |          | false                 | Use a connected Ledger device                                                                                  |
| --memo            | string |          |                       | Memo to send along with transaction                                                                            |
| --node            | string |          | tcp://localhost:26657 | \<host>:\<port> to tendermint rpc interface for this chain                                                     |
| --offline         | string |          |                       | Offline mode (does not allow any online functionality)                                                         |
| --sequence        | int    |          | 0                     | Sequence number to sign the tx                                                                                 |
| --sign-mode       | string |          |                       | Choose sign mode (direct \| amino-json), this is an advanced feature                                           |
| --trust-node      | bool   |          | true                  | Don't verify proofs for responses                                                                              |
| --yes             | bool   |          | true                  | Skip tx broadcasting prompt confirmation                                                                       |
| --chain-id        | string |          |                       | The network Chain ID                                                                                           |
| --home            | string |          | $HOME/.rebus           | Directory for config and data                                                                                  |
| --trace           | string |          |                       | Print out full stack trace on errors                                                                           |

### Module Commands <a href="#module-commands" id="module-commands"></a>

| **Subcommand**                          | **Description**                                               |
| --------------------------------------- | ------------------------------------------------------------- |
| [bank](modules/bank.md)                 | Bank subcommands for querying accounts and sending coins etc. |
| [debug](modules/debug.md)               | Debug subcommands                                             |
| [distribution](modules/distribution.md) | Distribution subcommands for rewards management               |
| [gov](modules/gov.md)                   | Governance and voting subcommands                             |
| [keys](modules/keys.md)                 | Keys allows you to manage your local keystore for tendermint  |
| [params](modules/params.md)             | Query parameters of modules                                   |
| [slashing](modules/slashing.md)         | Slashing subcommands                                          |
| [staking](modules/staking.md)           | Staking subcommands for validators and delegators             |
| [status](modules/status.md)             | Query remote node for status                                  |
| [tendermint](modules/tendermint.md)     | Tendermint state querying subcommands                         |
| [tx](broken-reference)                  | Tx subcommands                                                |
| [upgrade](modules/upgrade.md)           | Software Upgrade subcommands                                  |
