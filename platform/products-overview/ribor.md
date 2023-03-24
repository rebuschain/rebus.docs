---
order: 97
icon: /public/assets/ribor-icon.svg
---
# Ribor

Ribor, the Rebus Inter-Blockchain Offer Rate, is a reference rate that is constructed from the daily yield offered by total $REBUS staking. The Ribor fills the role of rate indices, like Libor, used by banks in managing instruments tied to traditional FIAT currencies. For Rebus, this means platform partners have a rate at which they can build DeFi instruments (or products) tied to a respective Ribor.  

## Intended Audience

This section is intended for development teams building instruments or products tied to $REBUS and are already familiar with the role of rate indices. For more information regarding the role of rate indices, [read here](https://www.bankrate.com/rates/interest-rates/libor/).

## How does it work?

From Investopedia “a reference rate is an interest rate benchmark used to set other interest rates.”

Ribor mimics the function of commonly used [reference rate indices](https://www.investopedia.com/terms/r/referencerate.asp), like [Libor](https://www.investopedia.com/terms/l/libor.asp) and [Euribor](https://www.investopedia.com/terms/e/euribor.asp), but in a way that works for respective DeFi instruments.

In Tradfi, several bonds (e.g., floating rates bonds) have interest linked to the LIbor or Euribor.

For example Goldman Sachs can issue a bond that will pay to the subscriber an interest of Libor 6 month + 1% every 6 months. So every six months they check the value of Libor 6-month and define the interest to be paid. For example the index at that date can have a value of 2% so the final interest will be 2% + 1%.

[Goldman Sachs floating rate bond](https://www.bondsupermart.com/bsm/bond-factsheet/US38141GVX95): Reference rate is 3M USD Libor + 1.75% per annum[  
Morgan Stanley floating rate bond](https://www.sec.gov/Archives/edgar/data/895421/000090514817000489/efc17-290_fwp.htm). Reference/Base Rate is Libor + 1.22%[](https://www.sec.gov/Archives/edgar/data/895421/000090514817000489/efc17-290_fwp.htm)

Another example would be a variable interest rate offered on a home loan. The interest paid is equal to the prime, or reference rate, plus a fixed amount, called the spread. An adjustable rate mortgage (ARM) may have a prime rate of 5% + 1%. So the borrower’s payment fluctuates up or down with the prime rate changes, but the bank can always count on the spread rate of 1%.

Ribor follows this concept but against specific DeFi cryptocurrencies to arrive at reference rates for each specific coin:

* $REBUS → Ribor Reb
* $ATOM → Ribor Atom
* $OSMO → Ribor Osmo
* $EVMOS → Ribor Evmos
