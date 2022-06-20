---
description: The tendermint module allows for querying of validator and node addresses.
---

# tendermint

## Available Commands

| Name, shorthand | Description |
| :--- | :--- |
| [show-address](tendermint.md#rebusd-tendermint-show-address) | Shows this node's tendermint validator consensus address |
| [show-node-id](tendermint.md#iris-tendermint-show-node-id) | Show this node's ID |
| [show-validator](tendermint.md#iris-tendermint-show-validator) | Show this node's tendermint validator info |
| [version](tendermint.md#iris-tendermint-version) | Print tendermint libraries' version |

### rebusd tendermint show-address

The following command will show the tendermint validator address of the local node.

```text
rebusd tendermint show-address
```

Returns the bech32 encoded validator consensus address `<rebusvalcon...>`:

```text
rebusvalcons1xyld7wpwjwx5reu8k0rrveceqztyp3h3fy3m6m
```

### rebusd tendermint show-node-id <a id="iris-tendermint-show-node-id"></a>

The following command will show the nodes ID

```text
rebusd tendermint show-node-id
```

Returns something similar to:

```text
ec730773944fbdc6a8c4918984f571aa57c975a3
```

### rebusd tendermint show-validator <a id="iris-tendermint-show-validator"></a>

The following command will show the validators tendermint consensus pubkey:

```text
rebusd tendermint show-validator
```

Returns something similar to:

```text
rebusvalconspub1zcjduepqltmy70ayq5c52fqga7xv336wv3jn8wxjcqra72amp6gcm7l8jwkss0ekqe
```

### rebusd tendermint version <a id="iris-tendermint-version"></a>

```text
rebusd tendermint version
```

Returns something similar to:

```text
tendermint: ""
abci: 0.17.0
blockprotocol: 11
p2pprotocol: 8
```

