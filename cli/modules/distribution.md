---
description: The distribution module allows you to manage your staking rewards
---

# distribution

## Available Commands

| Name | Description |
| :--- | :--- |
| [commission](distribution.md#rebusd-query-distribution-commission) | Query distribution validator commission |
| [community-pool](distribution.md#iris-query-distribution-community-pool) | Query the amount of coins in the community pool |
| [params](distribution.md#iris-query-distribution-rewards) | Query distribution params |
| [rewards](distribution.md#iris-query-distribution-rewards) | Query all distribution delegator rewards or rewards from a particular validator |
| [slashes](distribution.md#iris-query-distribution-slashes) | Query distribution validator slashes. |
| [validator-outstanding-rewards](distribution.md#iris-query-distribution-validator-outstanding-rewards) | Query distribution outstanding \(un-withdrawn\) rewards for a validator and all their delegations |
| [fund-community-pool](distribution.md#iris-tx-distribution-fund-community-pool) | Funds the community pool with the specified amount |
| [set-withdraw-addr](distribution.md#iris-tx-distribution-set-withdraw-addr) | Set the withdraw address for rewards associated with a delegator address |
| [withdraw-all-rewards](distribution.md#iris-tx-distribution-withdraw-all-rewards) | Withdraw all rewards for a single delegator |
| [withdraw-rewards](distribution.md#iris-tx-distribution-withdraw-rewards) | Withdraw rewards from a given delegation address, and optionally withdraw validator commission if the delegation address given is a validator operator |

### rebusd query distribution commission

Query validator commission rewards from delegators to that validator.

```text
rebusd query distribution commission [validator] [flags]
```

### rebusd query distribution community-pool <a id="iris-query-distribution-community-pool"></a>

Query all coins in the community pool which is under Governance control.

```text
rebusd query distribution community-pool [flags]
```

### rebusd query distribution params <a id="iris-query-distribution-params"></a>

Query distribution params.

```text
 rebusd query distribution params [flags]
```

### rebusd query distribution rewards <a id="iris-query-distribution-rewards"></a>

Query all rewards earned by a delegator, optionally restrict to rewards from a single validator.

```text
rebusd query distribution rewards [delegator-addr] [validator-addr] [flags]
```

### rebusd query distribution slashes <a id="iris-query-distribution-slashes"></a>

Query all slashes of a validator for a given block range.

```text
rebusd query distribution slashes [validator] [start-height] [end-height] [flags]
```

### rebusd query distribution validator-outstanding-rewards <a id="iris-query-distribution-validator-outstanding-rewards"></a>

Query distribution outstanding \(un-withdrawn\) rewards for a validator and all their delegations.

```text
rebusd query distribution validator-outstanding-rewards [validator] [flags]
```

### rebusd tx distribution fund-community-pool <a id="iris-tx-distribution-fund-community-pool"></a>

Funds the community pool with the specified amount.

```text
rebusd tx distribution fund-community-pool [amount] [flags]
```

### rebusd tx distribution set-withdraw-addr <a id="iris-tx-distribution-set-withdraw-addr"></a>

Set the withdraw address for rewards associated with a delegator address.

```text
rebusd tx distribution set-withdraw-addr [withdraw-addr] [flags]
```

### rebusd tx distribution withdraw-all-rewards <a id="iris-tx-distribution-withdraw-all-rewards"></a>

Withdraw all rewards for a single delegator.

```text
rebusd tx distribution withdraw-all-rewards [flags]
```

### rebusd tx distribution withdraw-rewards <a id="iris-tx-distribution-withdraw-rewards"></a>

Withdraw rewards from a given delegation address, and optionally withdraw validator commission if the delegation address given is a validator operator.

```text
rebusd tx distribution withdraw-rewards [validator-addr] [flags]
```

