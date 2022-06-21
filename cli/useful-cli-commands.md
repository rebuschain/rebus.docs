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

Import a key from a mnemonic (Comsos/Keplr or Keplr+Ledger):

```bash
rebusd keys add <new-key-name> --recover --coin-type 118 --algo secp256k1 
```

Import a key from a mnemonic (Metamask or Metamask+Ledger):

```bash
rebusd keys add <new-key-name> --recover --coin-type 60 --algo eth_secp256k1 
```

Export a private key (warning: don't do this unless you know what you're doing!)

```bash
rebusd keys export <your-key-name> --unsafe --unarmored-hex
```


Convert address from Bench32 to HEX (example):

```bash
rebusd debug addr rebus1dl90xa89ljj29mna8uasdxs3nejdw46x8767tc

Address bytes: [111 202 243 116 229 252 164 162 238 125 63 59 6 154 17 158 100 215 87 70]
Address (hex): 6FCAF374E5FCA4A2EE7D3F3B069A119E64D75746
Address (EIP-55): 0x6fCAf374E5fCa4a2ee7D3F3B069A119e64D75746
Bech32 Acc: rebus1dl90xa89ljj29mna8uasdxs3nejdw46x8767tc
Bech32 Val: rebusvaloper1dl90xa89ljj29mna8uasdxs3nejdw46xefxp7m
```

Convert address from HEX to Bench32 (example):

```bash
rebusd debug addr 6FCAF374E5FCA4A2EE7D3F3B069A119E64D75746

Address bytes: [111 202 243 116 229 252 164 162 238 125 63 59 6 154 17 158 100 215 87 70]
Address (hex): 6FCAF374E5FCA4A2EE7D3F3B069A119E64D75746
Address (EIP-55): 0x6fCAf374E5fCa4a2ee7D3F3B069A119e64D75746
Bech32 Acc: rebus1dl90xa89ljj29mna8uasdxs3nejdw46x8767tc
Bech32 Val: rebusvaloper1dl90xa89ljj29mna8uasdxs3nejdw46xefxp7m
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