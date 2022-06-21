---
icon: feed-star
order: 999
---
# Useful CLI Commands

Get standard debug info from the `rebus` daemon:

```bash
rebusd status
```

Check if your node is catching up:

```bash
# Query via the RPC (default port: 26657)
curl http://localhost:26657/status | jq .result.sync_info.catching_up
```

Get your node ID:

```bash
rebusd tendermint show-node-id
```

{% hint style="info" %}
Your peer address will be the result of this plus host and port, i.e. `<id>@<host>:26656` if you are using the default port.
{% endhint %}

Check if you are jailed or tombstoned:

```bash
rebusd query slashing signing-info $(rebusd tendermint show-validator)
```

Set the default chain for commands to use:

```bash
rebusd config chain-id rebus-1
```

Get your `valoper` address:

```bash
rebusd keys show <your-key-name> -a --bech val
```

See keys on the current box:

```bash
rebusd keys list
```

Import a key from a mnemonic:

```bash
rebusd keys add <new-key-name> --recover
```

Export a private key (warning: don't do this unless you know what you're doing!)

```bash
rebusd keys export <your-key-name> --unsafe --unarmored-hex
```

Withdraw rewards (including validator commission), where `rebusvaloper1...` is the validator address:

```bash
rebusd tx distribution withdraw-rewards <rebusvaloper1...> --from <your-key>  --commission
```

Stake:

```bash
rebusd tx staking delegate <rebusvaloper1...> <AMOUNT>urebus --from <your-key>
```

Find out what the JSON for a command would be using `--generate-only`:

```bash
rebusd tx bank send $(rebusd keys show <your-key-name> -a) <recipient addr> <AMOUNT>urebus --generate-only
```

Query the results of a gov vote that has ended, from a remote RPC (NB - you have to specify a height before the vote ended):

```bash
 rebusd q gov votes 1 --height <height-before-vote-ended> --node https://rpc-archive.rebusnetwork.io:443
```

Query the validator set (and jailed status) via CLI:

```bash
rebusd query staking validators --limit 1000 -o json | jq -r '.validators[] | [.operator_address, (.tokens|tonumber / pow(10; 6)), .description.moniker, .jail, .status] | @csv' | column -t -s"," | sort -k2 -n -r | nl
```
<!-- // TODO figure out what we do here
Get contract state:

```bash
rebusd q wasm contract-state all <contract-address>
```
-->