# Investment Rebalancer

Supplement to [this](https://www.bogleheads.org/forum/viewtopic.php?f=1&t=297892) discussion on Bogleheads.org

### Purpose
Enables user to calculate *Lazy Rebalancing* of a portfolio by specifying amount available to add and target asset allocation (AA).


### General Notes
1. Built using Microsoft Excel 16.32 with Microsoft 365 subscription.
2. Security names and prices may not automatically populate if user does not have MS 365 subscription. They *should* be able to update manually.
3. Employs the built-in Solver function, found under "Data" tab.


## Tab 1 - Mutual Fund Rebalancer
__User inputs__:
* Amount ($) available to invest in securities
* Securities in portfolio
* Desired asset allocation
* Amount ($) currently held in each security

__Spreadsheet calculates__:
* Amount ($) to add to each security to maximally utilize available funds to get closer to AA

## Tab 2 - Lazy Rebalancer Website
__User inputs__:
* Same as Tab 1

__Spreadsheet calculates__:
* No "calculations" per se, but formats a block that can be copied and pasted into the [Optimal Lazy Rebalancer](http://optimalrebalancing.tk/index.html)

## Tab 3 - ETF
ETF tab assumes that purchases are limited to whole shares. Whereas the Mutual Fund tab returns the optimal *dollar* investment, the ETF tab returns the optimal *share purchase* quantity.

__User inputs__:
* Amount ($) available to invest in securities
* Securities in portfolio
* Desired asset allocation
* Amount (# shares) currently held in each security

__Spreadsheet calculates__:
* Number of shares to purchase maximally utilize available funds to get closer to AA
* May leave cash un-invested if residual cash is less than lowest share price *or* only enough to purchase share(s) that would result in worse deviation from AA

## Methodology

1. For each security, create an error term: 

    ```error = (current invested + new investment) / (target investment)```

2. Solve for amount of new investment in each security so that the ending portfolio has the best possible error for any individual security 

    ```maximize( minimum security error )``` 

3. Do not exceed the amount of new money available to invest


