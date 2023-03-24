---
order: 94
icon: image
---
# NFT

This section describes products based on the NFT Rebus Market:  

* NFT Liquidity Product 1 - Digital Underlying
* NFT Liquidity Product 2 - Physical Underlying

All NFT Products are built as [Vaults](rebus-vault.md) which invest in a third party NFT.  

## Summary

* The current NFT market is not liquid. A bidding process is required each time you want to buy or sell an NFT, meaning time delays for transactions as well as a chance the trade will not happen.
* In the regular crypto market there is always a buy offer (maker) at a price that is the market price - the offer price.
* In the regular crypto market it is also possible to borrow stablecoins using crypto assets as collateral. This is explained in detail in the [stablecoin product](stable-coin-products.md) documentation.

Our NFT products allows the holder to leverage held NFTs as collateral, whether they’re physical or digital, to borrow money (FIAT).  
  
If the loan is not repaid, the Pool takes possession of the NFT and sells it on the open market. In the case of a physical underlying, the loan can only be granted against a purchase commitment by a third party at a defined price and upon expiry of the borrowing contract.

## NFT Liquidity Product 1 - Digital Backing

The logic of the product is to use the NFT as collateral to borrow money.  
The product, through the [Vault](rebus-vault.md), invests in the third party Stability Pool Side previously explained.

**Investment Currency**: FIAT

**Who invests in this product?** Those looking for a low– risk, NFT-specific investment. This product is partially market neutral, and requires a moderate-term participation window.**  

**Reward**: Rewards scale with the size and frequency of the liquidation of the borrowing side, plus an interest [(Ribor)](ribor.md).

**Duration**: Perpetual - redemption is allowed at any time at the market price.

**Currency Risk (for investors FIAT based)**: **<span style="color:limegreen">Low</span>**

**Market Risk**: **<span style="color:limegreen">Low</span>**

**Overall Risk**: **<span style="color:limegreen">Low</span>**
  
**Risks**:  Rapid decline in the price of the NFT - VaR (99%, 3 months) = -0.9%

‍**Opportunities**: Increase in size and volume of the liquidation of the borrowing side.

## NFT Liquidity Product 2 - Physical Backing

Similar to NFT Product 1 but focused on the NFT holder's need to borrow money for a given time frame.

**Investment Currency**: FIAT

**Who invests in this product?** Those looking to leverage held NFTs for short or moderate term borrowing, with low to moderate risk. The product is not LONG on NFT price but partially SHORT, partially market NEUTRAL.

**Reward**: The reward is based on the size and frequency of the liquidation of the borrowing side, plus interest ([Ribor](https://www.rebuschain.com/platform/products-overview/ribor)).

**Duration**: X months

**Currency Risk (for investors FIAT based)**: **<span style="color:limegreen">Low</span>**

**Market Risk**: **<span style="color:limegreen">Low</span>**

**Overall Risk**: **<span style="color:limegreen">Low</span>**

**Risks**: Rapid decline in the price of the NFT  - VaR (99%, 3 months) = -0.9%

‍**Opportunities**: Increase in magnitude and volume of liquidation transactions on the borrowing side.
