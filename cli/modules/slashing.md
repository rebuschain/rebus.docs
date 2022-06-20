---
description: The slashing module can unjail your validator
---

# slashing

## Available Commands

| Name | Description |
| :--- | :--- |
| [unjail](slashing.md#rebusd-tx-slashing-unjail) | Unjail validator previously jailed for downtime or double-sign. |

### rebusd tx slashing unjail

Unjail validator previously jailed for downtime.

```text
rebus tx slashing unjail [flags]
```

#### Unjail a validator

The following example will unjail a validator using its validator operator \(owner\) key :

```text
rebusd tx slashing unjail --from rebus1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg --chain-id rebus
```

{% hint style="info" %}
**TIP**

The validator operator key must be stored in the local keystore. 
{% endhint %}

