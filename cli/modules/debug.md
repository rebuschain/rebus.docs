---
description: The debug module is a tool for simple debugging.
---

# debug

## Available Commands

| Name                                        | Description                                           |
| ------------------------------------------- | ----------------------------------------------------- |
| [addr](debug.md#rebusd-debug-addr)           | Convert an address between hex and bech32             |
| [pubkey](debug.md#rebusd-debug-pubkey)       | Decode a ED25519 pubkey from hex, base64, or bech32   |
| [raw-bytes](debug.md#rebusd-debug-raw-bytes) | Convert raw bytes output (eg. \[10 21 13 127]) to hex |

### rebusd debug addr

Convert rebus address between `hex` and `bech32` format.

```
rebusd debug addr [address] [flags]
```

{% hint style="info" %}
**TIP**

The command will accept either `hex` or `bech32` coded address as the `[address]` argument. The command will return the same output for either.
{% endhint %}

{% hint style="info" %}
**TIP**

Your `bech32` encoded rebus local addresses can be queried with `rebusd keys list` 
{% endhint %}

Example usage:

```
# query bech32 encoded address
rebusd debug addr rebus1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg

# query hex address
rebusd debug addr FF1B810D9F74749B7065612A5F9AAC902E10CE2F
```

Returns:

```
Address: [255 27 129 13 159 116 116 155 112 101 97 42 95 154 172 144 46 16 206 47]
Address (hex): FF1B810D9F74749B7065612A5F9AAC902E10CE2F
Bech32 Acc: rebus1ludczrvlw36fkur9vy49lx4vjqhppn30h42ufg
Bech32 Val: rebusvaloper1ludczrvlw36fkur9vy49lx4vjqhppn30ggunj3
```

### rebusd debug pubkey

Decode a ED25519 pubkey from `hex`, `base64`, or `bech32`.

```
rebusd debug pubkey [pubkey] [flags]
```

{% hint style="info" %}
**TIP**

The command will accept `hex`, `base64` or `bech32` coded keys as `[pubkey] `argument. The command will return the same output for any of these inputs.
{% endhint %}

{% hint style="info" %}
**TIP**

Your `bech32` encoded validator pubkey can be queried with `rebusd tendermint show-validator`
{% endhint %}

Example usage:

```
# query hex address
rebusd debug pubkey F2AF5F796A1626C8BB51535E361F2E4B66A61B9AAD177B83452E0FCD5A14690DE

# query base64 encoded address
rebusd debug pubkey 8q9feWoWJsi7UVNeNh8uS2amG5qtF3uDRS4PzVoUaQ0=

# query base32 encoded address
rebusd debug pubkey rebuspub1zcjduepq72h477t2zcnv3w632d0rv8ewfdn2vxu645thhq699c8u6ks5dyxs7f2qt6Returns something similar to:
```

Returns:

```
Address: A50DF747BBF892E0FB0BCBAE6C3E2A5AE4A17D5A
Hex: F2AF5F796A1626C8BB51535E361F2E4B66A61B9AAD177B83452E0FCD5A14690D
JSON (base64): {"type":"tendermint/PubKeyEd25519","value":"8q9feWoWJsi7UVNeNh8uS2amG5qtF3uDRS4PzVoUaQ0="}
Bech32 Acc: rebuspub1zcjduepq72h477t2zcnv3w632d0rv8ewfdn2vxu645thhq699c8u6ks5dyxs7f2qt6
Bech32 Validator Operator: rebusvaloperpub1zcjduepq72h477t2zcnv3w632d0rv8ewfdn2vxu645thhq699c8u6ks5dyxssaf8x6
Bech32 Validator Consensus: rebusvalconspub1zcjduepq72h477t2zcnv3w632d0rv8ewfdn2vxu645thhq699c8u6ks5dyxsahwpfj
```

### rebusd debug raw-bytes

Convert raw bytes output (eg. \[10 21 13 127]) to `hex`.

```
rebusd debug raw-bytes <raw-bytes>
```

Example command:

```
rebusd debug raw-bytes "10 21 13 127"
```

Returns:

```
0A150D7F
```
