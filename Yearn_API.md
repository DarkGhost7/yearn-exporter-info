---
layout: page
title: "Yearn API"
permalink: /Yearn-API/
---

# API Info for Yearn Exporter
## exporter_v1
Exporter for v1 Vaults. Default http server is `http://localhost:8800`.
To run the `exporter_v1()` method navigate to the directory where you copied [yearn-exporter](https://github.com/iearn-finance/yearn-exporter), open a console, and type `brownie run yearn exporter_v1 --network mainnet`.
### yearn
#### param
##### `available`
Liquidity in Vault - Invested in all Strategies. Amount in LP tokens that is free to withdrawal without a fee.
##### `base price`
Virtual Price the vault started at.
##### `boost`
Current Boost
##### `crv apy`
Lowest amount of CRV APY generated with 0 boost
##### `crv price`
Current price of CRV 
##### `crv reward rate`
Curve APY * Boost ?
##### `earned`
Current amount of accumulated CRV rewards
##### `gauge balance`
Amount of LP tokens deposited in the gauge.
##### `gauge total`
Total deposited in the gauge
##### `inflation rate`
##### `max boost`
Max boost you can get with that % of the gauge
##### `min vecrv`
How much veCRV you need to get max boost
##### `relative weight`
% of all CRV rewards this curve pool gets
##### `share price`
getPricePerFullShare()/1e18
##### `strategy balance`
Current amount of lp tokens allocated to the strategy
##### `strategy buffer`
From 0 to 1: with 1 meaning the vault has all liquidity allocated to strategies. ? (minus some percent 5%?)
##### `vault balance`
Total amount of liquidity, in the vault lp token, in the vault. ?
##### `vault total`
?
##### `vecrv balance`
Yearn total veCRV voting power
##### `vecrv total`
Total voting power of the Curve Dao
##### `virtual price`
##### `working balance`
(Gauge balance / (2.5 * Boost)) - Balance which is being rewarded
##### `working total`
Total balance which is rewarded, from which you can calculate avg boost
#### Vaults
`aLink`
`curve.fi/3pool`
`curve.fi/busd`
`curve.fi/compound`
`curve.fi/gusd`
`curve.fi/musd`
`curve.fi/sbtc`
`curve.fi/y`
`DAI`
`GUSD`
`Link`
`TUSD`
`USDC`
`USDT`
`WETH`
`YFI`
### yearn_timing
#### load
Inculdes the registry and its load time in milliseconds
#### describe
Inculdes the vaults and their load time in milliseconds
## exporter_v2
Exporter for v2 Vaults. Default http server is `http://localhost:8801`.
To run the `exporter_v2()` method navigate to the directory where you copied [yearn-exporter](https://github.com/iearn-finance/yearn-exporter), open a console, and type `brownie run yearn exporter_v2 --network mainnet`.
### yearn_vault
#### param
`totalAssets`
The total quantity of all assets under control of this Vault, whether they're loaned out to a Strategy, or currently held in the Vault.
`totalBalanceSheet`
Provide an accurate estimate for the total amount of assets (principle + return) that the strategies are currently managing, denominated in terms of ?.
`maxAvailableShares`
Determines the total quantity of shares this Vault can provide, factoring in assets currently residing in the Vault, as well as those deployed to strategies.
`pricePerShare`
Price for a single vault share
`debtOutstanding`
`creditAvailable`
`expectedReturn`
`totalSupply`
`emergencyShutdown`
True or false: 0 = false 1 = true
(more info here)[https://app.gitbook.com/@lehnberg/s/yearn-docs-test/untitled-1#method-setemergencyshutdown]
`depositLimit`
Max amount of tokens able to be deposited in this vault in lp shares.
`debtLimit`
`totalDebt`
`lastReport`
`managementFee`
`performanceFee`
#### vault
`USDC`
`DAI`
### yearn_strategy
#### param
`debtOutstanding`
`creditAvailable`
`expectedReturn`
`emergencyExit`
`estimatedTotalAssets`
`performanceFee`
`activation`
`debtLimit`
`rateLimit`
`lastReport`
`totalDebt`
`totalReturns`
`collateralTarget`
`getCompValInWei`
`getCurrentPosition_supply`
`getCurrentPosition_borrow`
`getblocksUntilLiquidation`
`netBalanceLent`
`predictCompAccrued`
`storedCollateralisation`
`wantPrice`
#### strategy
`StrategyCreamCRV`
`LeveragedDaiCompStrategyV2`
`YearnWethCreamStratV2`
`StrategyHegic`
`StrategyHegicWBTC`
`StrategyUniswapPairPickle`
#### vault
`USDC`
`DAI`
### yearn_timing
#### action
describe
#### vault
`USDC`
`DAI`