---
layout: page
title: Yearn API
permalink: /Yearn-API/
description: >-
  Describes the Yearn Exporter Metrics and what the outputs mean. This guide
  assumes your using Docker thus the metric will show at localhost:8800/metrics
---

# Yearn Exporter Metrics

## yearn

This metric holds v1 vaults' info.

### param

#### **`available`**

Amount of shares that are free to withdrawal without a fee. \(Liquidity in Vault - Invested in all Strategies\) 

**`base price`**

Virtual Price the vault started at.

**`boost`**

Current Boost.

**`crv apy`**

Lowest amount of CRV APY generated with 0 boost.

**`crv price`**

The current price of CRV.

**`crv reward rate`**

Curve APY \* Boost?

**`earned`**

Current amount of accumulated CRV rewards.

**`gauge balance`**

Amount of LP tokens deposited in the gauge.

**`gauge total`**

Total deposited in the gauge.

**`inflation rate`**

**`max boost`**

Max boost you can get with that % of the gauge.

**`min vecrv`**

How much veCRV you need to get max boost.

**`relative weight`**

% of all CRV rewards this curve pool gets. This weeks weights can also be viewed [here](https://dao.curve.fi/) and the future weights for next week can be viewed [here](https://dao.curve.fi/gaugeweight).

**`share price`**

getPricePerFullShare\(\)/1e18.

**`strategy balance`**

Current amount of lp tokens allocated to the strategy.

**`strategy buffer`**

From 0 to 1: with 1 meaning the vault has all liquidity allocated to strategies. ? \(minus some percent 5%?\)

**`token price`**

Base price \* virtual\_price. This is meant to provide a balance price incase the vault's base price for some reason didn't start at 1.

**`vault balance`**

Total amount of shares in the vault. \( Shares invested in Strategy + Shares not invested in Strategy\)

**`vault total`**

Total amount of shares in the whole vault 

**`vecrv balance`**

Yearn total veCRV voting power.

**`vecrv total`**

Total voting power of the Curve Dao.

**`virtual price`**

Price of the underlying curve pool

**`working balance`**

\(Gauge balance / \(2.5 \* Boost\)\) - Balance which is being rewarded.

**`working total`**

Total balance which is rewarded, from which you can calculate avg boost.

### address

The vault's address. Deprecated for v1 vaults as "n/a" 

### vault

#### The v1 vault name

### version

This is the vault version deprecated for v1 vaults as "n/a"

## yearn\_vault

This is the metrics for v2 vaults

### address

This will show "n/a" if address doesn't exist or the vault is special else it will show the vaults contract address.

### experimental

Bool: True or False

Is vault non-production or production.

### param

`totalAssets` 

The total quantity of all assets under control of this Vault, whether they're loaned out to a Strategy, or currently held in the Vault.

 `totalBalanceSheet` 

Provides an accurate estimate for the total amount of assets \(principle + return\) that the strategies are currently managing, denominated in terms of ?.

 `maxAvailableShares` 

Determines the total quantity of shares this Vault can provide, factoring in assets currently residing in the Vault, as well as those deployed to strategies.

 `pricePerShare` 

Price for a single vault share - returns the price of the Vault’s wrapped token, denominated in the unwrapped native token. More info [here](https://app.gitbook.com/@lehnberg/s/yearn-docs-test/developers/yvaults-documentation/vault-interfaces#function-getpriceperfullshare)

 `debtOutstanding`

Total debt the whole vault has outstanding

 `creditAvailable`

 `expectedReturn`

 `totalSupply`

 `emergencyShutdown` 

True or false: 0 = false 1 = true [more info here](https://app.gitbook.com/@lehnberg/s/yearn-docs-test/untitled-1#method-setemergencyshutdown).

 `depositLimit` 

Max amount of tokens able to be deposited in this vault in lp shares.

 `debtLimit`

Current max debt limit the vault is able to take on across all strategies

 `totalDebt`

`lastReport` 

Last time a strategy harvested in unix time

`managementFee` 

`performanceFee`

### vault

### version

version type: `v1` or `v2` or `n/a`. For `yearn_vault` this should all be `v2`.

## yearn\_strategy

Metrics for v2 strategies and their smart contract methods

### address

This is the address of the strategy's vault.

### experimental

Bool: True or False

Is vault non-production or production.

### param

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

### strategy

The name of the strategy pulled from the contract `name` function.

### vault

The name of the vault affixed with the vault version number

### version

The vault version number usually "v2" could be "n/a" for special vaults.

## iearn

Metrics for Earn

### address

### param

## ironbank

Metrics for Cream v2 aka Ironbank

### address

### param

