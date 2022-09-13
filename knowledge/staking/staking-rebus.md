---
description: How to stake your Rebus with the Omniflix UI and Keplr browser extension
icon: browser
tags: [knowledge]
---

# Rebus Staking UI

## Overview

In this tutorial we will learn how to stake Rebus to a validator of the Rebus network. This will earn you rewards and help to secure the Rebus network. We will be achieving this with the following general steps:

* [Install and configure the Keplr browser extension](../wallets/keplr-browser-extension.md)
* [Open the Rebus staking UI and login with your Keplr wallet](./staking-rebus/#open-the-rebus-staking-ui-and-log-in-with-keplr-browser-extension)
* [Select a validator and stake your Rebus tokens](./staking-rebus/#select-a-validator-and-stake-your-rebus-tokens)
* [Redelegate Tokens](./staking-rebus/#redelegate-tokens)
* [Undelegate Tokens](./staking-rebus/#undelegate-tokens)
* [Collect staking rewards](./staking-rebus/#collect-staking-rewards)

{% hint style="info" %}
For users with a Rebus stakedrop allocation, you will need to add your rebus wallet associated with the stakedrop to your Keplr browser extension. You can do this by following the Keplr [guide ](../wallets/keplr-browser-extension.md#import-an-existing-account)and entering the mnemonic associated with your cosmos (atom) wallet address.
{% endhint %}

{% hint style="warning" %}
Delegation of your tokens to a validator will make them unusable for any other purpose. The tokens become "bonded". To "unbond" your tokens, you will need to un-delegate them. #TODO veifty that this process takes **14 days**. During this unbonding time you **will NOT receive rewards**.
{% endhint %}

## Open the Rebus Staking UI and log in with Keplr browser extension

Open the Chrome browser and navigate to the Rebus webapp (TBA). You will see the following page:
![](<../../public/assets/rebus-staking-landing.png>)

{% hint style="info" %}
Be sure that you have the wallet you wish to use selected by clicking the Keplr icon in your Chrome toolbar, selecting the silhouette in the top right of the Keplr window and then selecting the account you wish to use.
{% endhint %}

Click the **Connect Wallet** to continue. A popup window will appear requesting to connect rebus.omniflix.co to your Keplr wallet.

![](<../../public/assets/rebus-staking-request-connection.png>)

Click **Approve** to continue.

![](<../../public/assets/rebus-staking-landing.png>)

## Select a validator and stake your Rebus tokens

To see all the available validators, click the **All Validators** tab if it's not already selected. A list of active validators will be shown. To see more validators you can click the pagination arrows at the bottom of the page. To delegate tokens to your desired validator, click the **DELEGATE** button to the right hand side of the row for the validator you wish to delegate too. You can also delegate from the My Token header section of the page. 

A form will appear, showing the validator and a field to enter the amount of tokens to delegate. Your available tokens can be seen at the bottom of the form. Enter the amount of tokens you wish to delegate and click  **DELEGATE**.

![](<../../public/assets/rebus-stake-tokens.png>)

A Keplr wallet popup will appear asking for approval for the transaction. Click **Approve** to finalize the delegation.

![](<../../public/assets/rebus-approve-transaction.png>)

After the transaction is completed, a popup will indicate that the tokens were successfully delegated. Click **DONE** to continue.

![](<../../public/assets/rebus-staked-success.png>)

Your tokens are now delegated to the selected validator. You can now see the delegated amount next to the validator in the validator list. You will also be given additional options to REDELEGATE and UNDELEGATE for this validator.

![](<../../public/assets/rebus-stake-result.png>)

## Redelegate tokens

If you want to move your tokens to a different validator you can use the redelegate buttons. Once you click on them a popup will show up asking you the from and to validator and the amount you would like to redelegate.

![](<../../public/assets/rebus-redelegate.png>)

Click on the **Redelegate** button and approve the transaction in Keplr as you did before. At this point a popup will appear with indicating that the redelegation succeeded.

![](<../../public/assets/rebus-redelegate-success.png>)

After redelegating your tokens you should now see two validator listed.

![](<../../public/assets/rebus-redelegate-result.png>)

## Undelegate tokens

If you want to remove your tokens from a validator you can use the undelegate buttons. Once you click on them a popup will show up asking you which validator and the amount you would like to undelegate.

![](<../../public/assets/rebus-undelegate.png>)

Click on the **Undelegate** button and approve the transaction in Keplr as you did before. At this point a popup will appear with indicating that the undelegation succeeded.

![](<../../public/assets/rebus-undelegate-success.png>)

After undelegating your tokens you should now see one validator listed.

![](<../../public/assets/rebus-undelegate-result.png>)

## Collect staking rewards

Work in progress....



