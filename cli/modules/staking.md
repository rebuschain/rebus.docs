---
description: >-
  The staking module provides a set of subcommands to query the staking state
  and send staking transactions.
---

# staking

## Available Commands

| Name | Description |
| :--- | :--- |
| [validator](staking.md#iris-query-staking-validator) | Query a validator |
| [validators](staking.md#iris-query-staking-validators) | Query for all validators |
| [delegation](staking.md#iris-query-staking-delegation) | Query a delegation based on address and validator address |
| [delegations](staking.md#iris-query-staking-delegations) | Query all delegations made from one delegator |
| [delegations-to](staking.md#iris-query-staking-delegations-to) | Query all delegations to one validator |
| [unbonding-delegation](staking.md#iris-query-staking-unbonding-delegation) | Query an unbonding-delegation record based on delegator and validator address |
| [unbonding-delegations](staking.md#iris-query-staking-unbonding-delegations) | Query all unbonding-delegations records for one delegator |
| [unbonding-delegations-from](staking.md#iris-query-staking-unbonding-delegations-from) | Query all unbonding delegatations from a validator |
| [redelegations-from](staking.md#iris-query-staking-redelegations-from) | Query all outgoing redelegatations from a validator |
| [redelegation](staking.md#iris-query-staking-redelegation) | Query a redelegation record based on delegator and a source and destination validator address |
| [redelegations](staking.md#iris-query-staking-redelegations) | Query all redelegations records for one delegator |
| [pool](staking.md#iris-query-staking-pool) | Query the current staking pool values |
| [params](staking.md#iris-query-staking-params) | Query the current staking parameters information |
| [historical-info](staking.md#iris-query-staking-historical-info) | Query historical info at given height |
| [create-validator](staking.md#iris-tx-staking-create-validator) | Create new validator initialized with a self-delegation to it |
| [edit-validator](staking.md#iris-tx-staking-edit-validator) | Edit existing validator account |
| [delegate](staking.md#iris-tx-staking-delegate) | Delegate liquid tokens to an validator |
| [unbond](staking.md#iris-tx-staking-unbond) | Unbond shares from a validator |
| [redelegate](staking.md#iris-tx-staking-redelegate) | Redelegate illiquid tokens from one validator to another |

### rebusd query staking validator <a id="iris-query-staking-validator"></a>

#### Query a validator by validator address <a id="query-a-validator-by-validator-address"></a>

Query information for validator address `<rebusvaloper...>`:

```text
rebusd query staking validator <rebusvaloper...>
```

Will return something similar to:

```text
commission:
  commission_rates:
    max_change_rate: "0.010000000000000000"
    max_rate: "0.200000000000000000"
    rate: "0.110000000000000000"
  update_time: "2021-07-01T09:06:42.110582713Z"
consensus_pubkey:
  '@type': /cosmos.crypto.ed25519.PubKey
  key: +vZPP6QFMUUkCO+MyMdOZGUzuNLAB98ruw6Rjfvnk60=
delegator_shares: "10647850539.181674918343698393"
description:
  details: ""
  identity: FEE30F35994C320D
  moniker: nullmames
  security_contact: ""
  website: ""
jailed: false
min_self_delegation: "1"
operator_address: rebusvaloper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
status: BOND_STATUS_BONDED
tokens: "10331782033"
unbonding_height: "631804"
unbonding_time: "2021-08-25T00:26:38.283926951Z"
```

### rebusd query staking validators <a id="iris-query-staking-validators"></a>

#### Query all validators <a id="query-all-validators"></a>

The following will return information for ALL validators:

```text
rebusd query staking validators
```

The returned values will be similar to those from [`rebusd query staking validator`](staking.md#iris-query-staking-validator)\`\`

### rebusd query staking delegation <a id="iris-query-staking-delegation"></a>

Query a delegation based on delegator address and validator address.

```text
rebusd query staking delegation [delegator-addr] [validator-addr]
```

#### Query a delegation <a id="query-a-delegation"></a>

The following will return delegations for a delegator to a particular validator address `<rebusvaloper...>` :

```text
rebusd query staking delegation <rebus...> <rebusvaloper...>
```

Returns something similar to:

```text
balance:
  amount: "9159423104"
  denom: urebus
delegation:
  delegator_address: rebus1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg
  shares: "9439626961.941610808328957187"
  validator_address: rebusvaloper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
```

### rebusd query staking delegations <a id="iris-query-staking-delegations"></a>

Query all delegations delegated from one delegator.

```text
rebusd query staking delegations [delegator-address] [flags]
```

#### Query all delegations of a delegator <a id="query-all-delegations-of-a-delegator"></a>

The following command will return all delegations from a delegators address `<rebus...>`:

```text
rebusd query staking delegations <rebus...>
```

Will return something similar to:

```text
delegation_responses:
- balance:
    amount: "1100000"
    denom: urebus
  delegation:
    delegator_address: rebus1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg
    shares: "1100000.000000000000000000"
    validator_address: rebusvaloper1ms8tvfkerhyf6mca2qc79t7mr3eh9dsr79mjf2
- balance:
    amount: "9166092794"
    denom: urebus
  delegation:
    delegator_address: rebus1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg
    shares: "9446500690.213833508382324426"
    validator_address: rebusvaloper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
pagination:
  next_key: null
  total: "0"
```

### rebusd query staking delegations-to <a id="iris-query-staking-delegations-to"></a>

Query all delegations to one validator.

```text
rebusd query staking delegations-to [validator-address] [flags]
```

#### Query all delegations to one validator <a id="query-all-delegations-to-one-validator"></a>

The following command will return all delegations to a validator address `<rebusvaloper...>`:

```text
rebusd query staking delegations-to <rebusvaloper...>
```

Will return something similar to:

```text
delegation_responses:
- balance:
    amount: "990000675"
    denom: urebus
  delegation:
    delegator_address: rebus1qnshaxp9w7aecthj2sn4c0uct07urg3tsd2rqs
    shares: "1020286644.656983874857994825"
    validator_address: rebusvaloper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
- balance:
    amount: "180180122"
    denom: urebus
  delegation:
    delegator_address: rebus1na45quuuzuv5xtzl5qqp9zep9rkluqykwtcgd3
    shares: "185692169.327571065224155062"
    validator_address: rebusvaloper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
```

### rebusd query staking unbonding-delegation <a id="iris-query-staking-unbonding-delegation"></a>

Query an unbonding-delegation record based on delegator and validator address.

```text
rebusd query staking unbonding-delegation [delegator-addr] [validator-addr] [flags]
```

#### Query an unbonding delegation record <a id="query-an-unbonding-delegation-record"></a>

```text
rebusd query staking unbonding-delegation <rebus...> <rebusvaloper...>
```

### rebusd query staking unbonding-delegations <a id="iris-query-staking-unbonding-delegations"></a>

#### Query all unbonding delegations records of a delegator <a id="query-all-unbonding-delegations-records-of-a-delegator"></a>

```text
rebusd query staking unbonding-delegations <rebus...>
```

### rebusd query staking unbonding-delegations-from <a id="iris-query-staking-unbonding-delegations-from"></a>

#### Query all unbonding delegations from a validator <a id="query-all-unbonding-delegations-from-a-validator"></a>

```text
rebusd query staking unbonding-delegations-from <rebusvaloper...>
```

### rebusd query staking redelegations-from <a id="iris-query-staking-redelegations-from"></a>

Query all outgoing redelegations of a validator

```text
rebusd query staking redelegations-from [validator-address] [flags]
```

#### Query all outgoing redelegatations of a validator <a id="query-all-outgoing-redelegatations-of-a-validator"></a>

```text
rebusd query staking redelegations-from <rebusvaloper...>
```

### rebusd query staking redelegation <a id="iris-query-staking-redelegation"></a>

Query a redelegation record based on delegator and source validator address and destination validator address.

```text
rebusd query staking redelegation [delegator-addr] [src-validator-addr] [dst-validator-addr] [flags]
```

#### Query a redelegation record <a id="query-a-redelegation-record"></a>

```text
rebusd query staking redelegation <rebus...> <rebusvaloper...> <rebusvaloper...>
```

### rebusd query staking redelegations <a id="iris-query-staking-redelegations"></a>

#### Query all redelegations records of a delegator <a id="query-all-redelegations-records-of-a-delegator"></a>

```text
rebusd query staking redelegations <rebus...>
```

### rebusd query staking pool <a id="iris-query-staking-pool"></a>

#### Query the current staking pool values <a id="query-the-current-staking-pool-values"></a>

```text
rebusd query staking pool
```

Returns something similar to:

```text
bonded_tokens: "1547447152807"
not_bonded_tokens: "67232814293"
```

### rebusd query staking params <a id="iris-query-staking-params"></a>

#### Query the current staking parameters information <a id="query-the-current-staking-parameters-information"></a>

```text
rebusd query staking params
```

Returns something similar to:

```text
bond_denom: urebus
historical_entries: 10000
max_entries: 7
max_validators: 125
unbonding_time: 1814400s
```

### rebusd query staking historical-info <a id="iris-query-staking-historical-info"></a>

#### Query historical info at given height <a id="query-historical-info-at-given-height"></a>

```text
rebusd query staking historical-info <height>
```

### rebusd tx staking create-validator <a id="iris-tx-staking-create-validator"></a>

Send a transaction to apply to be a validator and delegate a certain amount of `rebus` to it.

```text
rebusd tx staking create-validator [flags]
```

**Flags:**

| Name, shorthand | type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| --amount | string | Yes |  | Amount of coins to bond |
| --commission-rate | float | Yes | 0.0 | The initial commission rate percentage |
| --commission-max-rate | float |  | 0.0 | The maximum commission rate percentage |
| --commission-max-change-rate | float |  | 0.0 | The maximum commission change rate percentage \(per day\) |
| --min-self-delegation | string |  |  | The minimum self delegation required on the validator |
| --details | string |  |  | Optional details |
| --genesis-format | bool |  | false | Export the transaction in gen-tx format; it implies --generate-only |
| --identity | string |  |  | Optional identity signature \(ex. UPort or Keybase\) |
| --ip | string |  |  | Node's public IP. It takes effect only when used in combination with |
| --node-id | string |  |  | The node's ID |
| --moniker | string | Yes |  | Validator name |
| --pubkey | string | Yes |  | Go-Amino encoded hex PubKey of the validator. For Ed25519 the go-amino prepend hex is 1624de6220 |
| --website | string |  |  | Optional website |
| --security-contact | string |  |  | The validator's \(optional\) security contact email |

#### Create a validator <a id="create-a-validator"></a>

```text
rebusd tx staking create-validator --chain-id=rebus --from=<key-name> --fees=0.025rebus --pubkey=<validator-pubKey> --commission-rate=0.1 --amount=100000000urebus --moniker=<validator-name>
```

{% hint style="info" %}
**TIP**

Refer to [mainnet](../../validators/mainnet.md) instructions for detailed information.
{% endhint %}

### rebusd tx staking edit-validator <a id="iris-tx-staking-edit-validator"></a>

Edit an existing validator's settings, such as commission rate, name, etc.

```text
rebusd tx staking edit-validator [flags]
```

**Flags:**

| Name, shorthand | type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| --commission-rate | float |  | 0.0 | Commission rate percentage |
| --moniker | string |  |  | Validator name |
| --identity | string |  |  | Optional identity signature \(ex. UPort or Keybase\) |
| --website | string |  |  | Optional website |
| --details | string |  |  | Optional details |
| --security-contact | string |  |  | The validator's \(optional\) security contact email |
| --min-self-delegation | string |  |  | The minimum self delegation required on the validator |

#### Edit validator information <a id="edit-validator-information"></a>

```text
rebusd tx staking edit-validator --from=<key-name> --chain-id=rebus --fees=1rebus --commission-rate=0.10 --moniker=<validator-name>
```

### rebusd tx staking delegate <a id="iris-tx-staking-delegate"></a>

Delegate tokens to a validator.

```text
rebusd tx staking delegate [validator-addr] [amount] [flags]
```

```text
rebusd tx staking delegate <rebusvaloper...> <amount> --chain-id=rebus --from=<key-name>
```

### rebusd tx staking unbond <a id="iris-tx-staking-unbond"></a>

Unbond tokens from a validator.

```text
rebusd tx staking unbond [validator-addr] [amount] [flags]
```

#### Unbond some tokens from a validator <a id="unbond-some-tokens-from-a-validator"></a>

```text
rebusd tx staking unbond <rebusvaloper...> 1000000urebus --from=<key-name> --chain-id=rebus 
```

### rebusd tx staking redelegate <a id="iris-tx-staking-redelegate"></a>

Transfer delegation from one validator to another.

{% hint style="info" %}
TIP

There is no `unbonding time` during the redelegation, so you will not miss the rewards. But you can only redelegate once per validator, until a period \(= `unbonding time`\) exceed.
{% endhint %}

```text
rebusd tx staking redelegate [src-validator-addr] [dst-validator-addr] [amount] [flags]
```

#### Redelegate some tokens to another validator <a id="redelegate-some-tokens-to-another-validator"></a>

```text
rebusd tx staking redelegate <rebusvaloper...> <rebusvaloper...> 1000000urebus --chain-id=rebus --from=<key-name>
```

