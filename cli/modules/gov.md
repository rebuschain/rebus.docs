---
description: >-
  The governance module provides tools for querying, submitting, and voting on
  proposals
---

# gov

## Available Commands

| Name | Description |
| :--- | :--- |
| [proposal](gov.md#rebus-query-gov-proposal) | Query details of a single proposal |
| [proposals](gov.md#rebus-query-gov-proposals) | Query proposals with optional filter |
| [vote](gov.md#rebus-query-gov-vote) | Query details of a single vote |
| [votes](gov.md#rebus-query-gov-votes) | Query votes on a proposal |
| [deposit](gov.md#rebus-query-gov-deposit) | Query details of a deposit |
| [deposits](gov.md#rebus-query-gov-deposits) | Query deposits on a proposal |
| [tally](gov.md#rebus-query-gov-tally) | Get the tally of a proposal vote |
| [param](gov.md#rebus-query-gov-param) | Query the parameters \(voting |
| [params](gov.md#rebus-query-gov-params) | Query the parameters of the governance process |
| [proposer](gov.md#rebus-query-gov-proposer) | Query which address proposed a proposal with a given ID. |
| [submit-proposal](gov.md#rebus-tx-gov-submit-proposal) | Submit a proposal along with an initial deposit |
| [deposit](gov.md#rebus-tx-gov-deposit) | Deposit tokens for an active proposal |
| [vote](gov.md#rebus-tx-gov-vote) | Vote for an active proposal, options: yes/no/no\_with\_veto/abstain |

### rebusd query gov proposal <a id="rebus-query-gov-proposal"></a>

Query details of a single governance proposal:

```text
rebusd query gov proposal [proposal-id] [flags]
```

**Flags:**

| Name, shorthand | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| --depositor | Address |  |  | Filter proposals by depositor address |
| --limit | uint |  | 100 | Limit to the latest \[number\] of proposals. Default to all proposals |
| --status | string |  |  | Filter proposals by status |
| --voter | Address |  |  | Filter proposals by voter address |

### rebusd query gov proposals <a id="rebus-query-gov-proposals"></a>

Query all proposals:

```text
rebusd query gov proposals
```

Query proposals with conditions filters:

```text
rebusd query gov proposals --limit=3 --status=Passed --depositor=<rebus...>
```

### rebusd query gov vote <a id="rebus-query-gov-vote"></a>

Query details of a single vote.

```text
rebusd query gov vote [proposal-id] [voter-addr] [flags]
```

### rebusd query gov votes <a id="rebus-query-gov-votes"></a>

Query votes on a proposal.

```text
rebusd query gov votes [proposal-id] [flags]
```

### rebusd query gov deposit <a id="rebus-query-gov-deposit"></a>

Query details for a single proposal deposit on a proposal by its identifier.

```text
rebusd query gov deposit [proposal-id] [depositer-addr] [flags]
```

### rebusd query gov deposits <a id="rebus-query-gov-deposits"></a>

Query details for all deposits on a proposal.

```text
rebusd query gov deposits [proposal-id] [flags]
```

### rebusd query gov tally <a id="rebus-query-gov-tally"></a>

Query tally of votes on a proposal.

```text
rebusd query gov tally [proposal-id] [flags]
```

### rebusd query gov param <a id="rebus-query-gov-param"></a>

Query the parameters \(voting \| tallying \| deposit\) of the governance process.

```text
rebusd query gov param [param-type] [flags]
```

Example:

```text
# query voting parameters
rebusd query gov param voting

# query tallying parameters
rebusd query gov param tallying

# query deposit parameters
rebusd query gov param deposit
```

### rebusd query gov params <a id="rebus-query-gov-params"></a>

Query the all the parameters for the governance process.

```text
rebusd query gov params [flags]
```

### rebusd query gov proposer <a id="rebus-query-gov-proposer"></a>

Query which address proposed a proposal with a given ID.

```text
rebusd query gov proposer [proposal-id] [flags]
```

### rebusd tx gov submit-proposal <a id="rebus-tx-gov-submit-proposal"></a>

Submit a proposal along with an initial deposit. Proposal title, description, type and deposit can be given directly or through a proposal JSON file. Available Commands:

| Name | Description |
| :--- | :--- |
| cancel-software-upgrade | Cancel the current software upgrade proposal |
| community-pool-spend | Submit a community pool spend proposal |
| param-change | Submit a parameter change proposal |
| software-upgrade | Submit a software upgrade proposal |

#### rebusd tx gov submit-proposal community-pool-spend <a id="rebus-tx-gov-submit-proposal-community-pool-spend"></a>

Submit a community pool spend proposal along with an initial deposit. The proposal details must be supplied via a JSON file.

```text
rebusd tx gov submit-proposal community-pool-spend <path/to/proposal.json> --from=<key_or_address>
```

Where proposal.json contains, for example:

```text
{
    "title": "Community Pool Spend",
    "description": "Send me tokens, to benefit the Rebus community",
    "recipient": "rebus1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg",
    "amount": "1000000urebus",
    "deposit": "1000urebus"
}
```

#### rebusd tx gov submit-proposal param-change <a id="rebus-tx-gov-submit-proposal-param-change"></a>

Submit a parameter proposal along with an initial deposit. The proposal details must be supplied via a JSON file. For values that contains objects, only non-empty fields will be updated.

{% hint style="warning" %}
**IMPORTANT**

Currently parameter changes are evaluated but not validated, so it is very important that any "value" change is valid \(ie. correct type and within bounds\) for its respective parameter, eg. "MaxValidators" should be an integer and not a decimal.
{% endhint %}

Proper vetting of a parameter change proposal should prevent this from happening \(no deposits should occur during the governance process\), but it should be noted regardless.

```text
rebusd tx gov submit-proposal param-change <path/to/proposal.json> --from=<key_or_address>
```

Where proposal.json contains, for example:

```text
{
    "title": "Staking Param Change",
    "description": "Update max validators",
    "changes": [
        {
        "subspace": "staking",
        "key": "MaxValidators",
        "value": 105
        }
    ],
    "deposit": "1000urebus"
}
```

#### rebusd tx gov submit-proposal software-upgrade <a id="rebus-tx-gov-submit-proposal-software-upgrade"></a>

Submit a software upgrade along with an initial deposit. Please specify a unique name and height OR time for the upgrade to take effect.

```text
rebusd tx gov submit-proposal software-upgrade [name] (--upgrade-height [height] | --upgrade-time [time]) (--upgrade-info [info]) [flags]
```

**Flags:**

| Name, shorthand | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| --deposit | Coin | Yes |  | Deposit of the proposal |
| --title | string | Yes |  | Title of proposal |
| --description | string | Yes |  | Description of proposal |
| --upgrade-height | int64 |  |  | The height at which the upgrade must happen \(not to be used together with --upgrade-time\) |
| --time | string |  |  | The time at which the upgrade must happen \(not to be used together with --upgrade-height\) |
| --info | string |  |  | Optional info for the planned upgrade such as commit hash, etc. |

{% hint style="info" %}
**TIP**

To enable nodes managed by [forbole/cosmovisor](https://github.com/forbole/cosmovisor) to undertake an automatic upgrade, where the operator has the required environment variable set.

Store an os/architecture -&gt; binary URI map in the upgrade plan `info` field as JSON under the `"binaries"` key, eg:

```text
{
  "binaries": {
    "linux/amd64":"https://example.com/rebus.zip?checksum=sha256:aec070645fe53ee3b3763059376134f058cc337247c978add178b6ccdfb0019f"
  }
}
```
{% endhint %}

#### rebusd tx gov submit-proposal cancel-software-upgrade <a id="rebus-tx-gov-submit-proposal-cancel-software-upgrade"></a>

Cancel a software upgrade along with an initial deposit.

```text
rebusd tx gov submit-proposal cancel-software-upgrade [flags]
```

**Flags:**

| Name, shorthand | Type | Required | Default | Description |
| :--- | :--- | :--- | :--- | :--- |
| --deposit | Coin | Yes |  | Deposit of the proposal |
| --title | string | Yes |  | Title of proposal |
| --description | string | Yes |  | Description of proposal |

### rebusd tx gov deposit <a id="rebus-tx-gov-deposit"></a>

Submit a deposit for an active proposal. You can find the `proposal-id` by running `rebusd query gov proposals`.

```text
rebusd tx gov deposit [proposal-id] [deposit] [flags]
```

### rebusd tx gov vote <a id="rebus-tx-gov-vote"></a>

Submit a vote for an active proposal. You can find the `proposal-id` by running `rebusd query gov proposals`. Vote for an active proposal, options: \(yes \| no \| no\_with\_veto \| abstain\).

```text
rebusd tx gov vote [proposal-id] [option] [flags]
```

Example vote, voting `yes` on proposal number `1`:

```text
rebusd tx gov vote 1 yes --from=<key_or_address> --fees=1rebus
```
