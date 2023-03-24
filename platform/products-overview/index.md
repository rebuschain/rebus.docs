---
icon: telescope
---
# Products Overview

Investments in decentralized finances (DeFi) protocols and tokens, are all over the headlines recently and are growing everyday. However, we still have not seen participation from a majority of investors. So, why not? Largely, complexity of access and vague answers to questions like “how can I invest?” and “what can I do with it?” By creating a mechanism that satisfies regulators, traditional finance (TradFi) institutions will be able to add new, DeFi revenue streams through existing Asset Management services with use cases already familiar to their clients.   
By simultaneously simplifying access and expanding DeFi investment opportunities  through TradFi, Rebus is facilitating a growth in the market that many experts are comparing to the hyper-adoption of the internet seen in the mid-to-late 1990s. Whether or not you’re already invested in DeFi, $REBUS is the safest way to invest in the success of the entire Cosmos Appchain.  
  
Our overarching goal at Rebus is to give Traditional Finance institutions (TraFi) simple access to the Decentralized Finance (DeFi) world. We will achieve this by reducing regulatory friction for TraFi institutions and providing strategies which match their investment ethos and regulatory standpoint.  
  
In doing so, we mimic the concepts and nomenclatures that exist in the traditional finance world.

## Rebus interest rate index

The idea is that in the world of TraFi there are, for each currency, one or more interest rate indices that allow the user to build products linked to these indices.  
‍  
Here are two examples of index rates in the TraFi world:  
‍  
Goldman Sachs floating rate bond: [bondsupermart](https://www.bondsupermart.com/bsm/bond-factsheet/US38141GVX95)  
Morgan Stanley floating rate bond. [Libor](https://www.sec.gov/Archives/edgar/data/895421/000090514817000489/efc17-290_fwp.htm) \+ 1.22%

For securities with a floating rate interest the global standard is Libor / Euribor / OIS + spread.  
  
Some definitions of the main interest rates from Investopedia:

## Euro Interbank Offered Rate (Euribor)

Euribor, or the Euro Interbank Offer Rate, is a reference rate that is constructed from the average interest rate at which eurozone banks offer unsecured short-term lending on the inter-bank market. The maturities on loans used to calculate Euribor often range from one week to one year.  
‍  
This is the benchmark rate with which banks lend or borrow excess reserves from one another over short periods of time, from one week to 12 months. These short-term loans are often structured as repurchase agreements (repos) and are intended to maintain bank liquidity and to make sure that excess cash is able to generate an interest return rather than sit idle.

## London Interbank Offered Rate (LIBOR)

The London Interbank Offered Rate (LIBOR) is a benchmark interest rate at which major global banks lend to one another in the international interbank market for short-term loans.  
‍  
LIBOR, which stands for London Interbank Offered Rate, serves as a globally accepted key benchmark interest rate that indicates borrowing costs between banks. The rate is calculated and will continue to be published each day by the Intercontinental Exchange (ICE), but due to recent scandals and questions around its validity as a benchmark rate, it is being phased out. According to the Federal Reserve and regulators in the UK, LIBOR will be phased out by June 30, 2023, and will be replaced by the Secured Overnight Financing Rate (SOFR). As part of this phase-out, LIBOR one-week and two-month USD LIBOR rates will no longer be published after December 31, 2021.1

## Euro Overnight Index Average (Eonia)

The Euro Overnight Index Average (Eonia) is the average overnight reference rate for which European banks lend to one another in euros. The Eonia is the interest rate for one-day loans between European banks and is considered an interbank rate. However, European regulatory reforms have resulted in a push to replace Eonia by January 2022.  
‍  
Eonia is a daily reference rate that expresses the weighted average of unsecured overnight interbank lending in the European Union and the European Free Trade Association (EFTA). It is calculated by the European Central Bank (ECB) based on the loans made by 28 panel banks.2

The idea is to create an interest rate index  for the Rebus currency following the Rebus Monetary Policy

## The Rebus Monetary Policy

The Rebus Monetary Policy allocates a certain amount of Rebus Tokens to staking each year for the first fifteen years: Rebus | Token-economics  
‍  
These tokens will be shared between all the stakers. The yield will be computed daily as follow:  
\
**Daily yield = (tokens put in) / (tokens staked)**
  
If the total amount of tokens staked gets close to zero, the yield will learn to be infinite, but we can assume that a minimum quantity of tokens will always be put in staking. The maximum yield value will be based on that assumed minimum.  
  
On the other hand, we can compute the minimum yield if we assume that all tokens are put in staking.  
  
The chart below shows the estimated Staking Maximum Yield and the Staking Minimum Yield for the first three years according to the Rebus Monetary Policy.
  
The idea is to have an interest rate that is fixed every day like what happens with Euribor, Libor, EONIA etc.  
  
Keeping in mind how Rebus Monetary Policy is made, the most similar interest rate should be the EONIA which is a daily rate (the maturity is 1 day) expressed in APR (Annual Percentage Rate).  
  
This new interest rate  - the Rebus interest rate - must have a name; Ribor

## Ribor interest rate features

**Fixing**: daily
  
**Value**: difference between daily effective yield and daily minimum staking yield. This means that the Ribor will always be greater or equal to zero.  
  
‍**Representation**: Annual Percentage Rate (APR)After the end of the Rebus Monetary Policy (15 years) the Ribor definition will be changed and based on a supply - demand dynamics.  
  
The chart below shows the estimated Ribor Yield for the first three years. This is a simulation based on the assumptions previously made on amount of Staking Minimum and Maximum.

## Ribor

The [Ribor](ribor.md), or the Rebus Inter-Blockchain Offer Rate, is a reference rate that is constructed from the daily yield offered by the staking.  
  
The Ribor will be computed for different coins as:  

* Rebus → Ribor Reb
* Atom → Ribor Atom
* Osmo → Ribor Osmo
* Juno → Ribor Juno
* etc…

The indexes computing for each coin will be will be based on the following:  

### Definitions

* **Maximum Coins in Staking (MCS)**: is the maximum amount of coins in staking relative to the amount of coins in circulation at agiven date. This value will be published on the Rebus website every day at 12PM am and will also be available on chain.
* **Amount of Coins in Staking (ACS)**: is the real amount of coins staked on a daily basis. This value will be published on the Rebus website every day at 12PM and will also be available on chain.
* **Rebus Staking Reward (RSR)**: $REBUS daily staking, specified by the Rebus Token Economics.
* **Daily Minimum Yield :** RSR / MCS \* 365
* **Daily Real Yield :** RSR / ACS \* 365
* The Yield / Rate representation are APR (Annual Percentage Rate)

### Ribor Logic

* **Fixing:** Computed every morning and published on the Rebus website.
* **Value:** Daily Real Yield - Daily Minimum Yield. This means that the Ribor will always be greater than zero.
* **Representation:** Annual Percentage Rate (APR)

## Products & Coins

Thanks to its technological conformation, many of the products offered by Rebus may use as underlying different coins linked to the Cosmos or Ethereum ecosystems.  
  
More in detail the following Products are built on topo of different coins like (Rebus, Atomo, Osmo, Juno etc.)  

* Staking Products
* Liquidity Products
* Machine Learning Products
* Options
