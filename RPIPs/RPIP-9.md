---
rpip: RPIP-9 
title: Increase Deposit Pool Limit 
description: Increase the Rocket Pool Deposit Pool Limit to 5K ETH
author: Ken Smith (@htimsk), Darren Langley (@darrenlangley)
discussions-to: https://dao.rocketpool.net/t/proposal-to-increase-the-deposit-pool-dp-limit/817
status: Draft
type: Protocol
category Core
created: 2022-08-09
---

## Abstract
This proposal simply increases the Protocol DAO setting that controls the limit on the amount of waiting ETH that can be present in the deposit pool.

## Motivation
Increasing the deposit pool limit will allow for more efficient and larger deposits by Institutional, DAO, and private whale depositors into the deposit pool. As an example, to reach our unofficial goal of becoming 22% of the amount of ETH staked on the beacon chain (2.8M ETH) we would require 690 full deposit pool deposits at the current setting. (2.8M - 100K / 2 / 2K max deposit). Increasing the limit to 5k would allow us to accomplish the same in only 270 transactions.

## Specification
The Core team will execute bootstrapSettingUint on the RocketDAOProtocol contract updating the `deposit.pool.maximum` pDAO setting to 5000 ether (5000000000000000000000).   

## Rationale
This proposal is to increase the deposit pool limit to 5,000 ETH from the current setting of 2,000 ETH. The max limit was designed to restrict the amount of the regular ETH left unstated, thus nonproductive at generating returns. Increasing the deposit pool limit does present a small potential reduction risk on the rETH APR but only occurs when the deposit pool has a positive balance.

The proposal was discussed and the impact assessed in the [Proposal to increase the deposit pool dp limit](https://dao.rocketpool.net/t/proposal-to-increase-the-deposit-pool-dp-limit/817) DAO forum post.

## Backwards Compatibility
No backwards incompatibility. The current limit is 2000 ETH so even if the deposit pool was full we are increasing not decreasing.

## Test Cases
This is a very low risk change. The deposit pool limit setting has already been used during deployment to ensure a phased rollout. The deposit pool limit has been increased to 5K ETH on the Goerli testnet already but we can construct the transaction payload and execute against Goerli to ensure it has the desired effect.

## Reference Implementation
Not applicable.

## Security Considerations
Increasing the deposit pool limit mildly increases the possibility for a flashloan style attack but for this to occur there would have to be an exploit present that yielded some value: no known exploit exists that would yield value and this has been carefully considered by auditors. It does make arbitarge opportunities slightly more profitable but the deposit pool is still limited and so these are very mild concerns.  

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).