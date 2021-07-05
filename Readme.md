# Introduction to Ybankrupt Network

_These docs are in active development by the Ybanktupy community.

## Background

Ybankrupt Network is a decentralized network for projects that have failed and need restructuring. The community can agreed to lock any remaining value to incentivize re launches following the concept of Standing on the shoulders of giants.

## Motivation
To lock value in all projects working towards a common goal. In this case stablecoin research like Iron Finance and subsequent projects. To democratize governance of projects to prevent rug pulls by creating a platform for developer grants.


## Votes

A Proposer is the term used to refer to an external person and/or team that proposes a restructure of a project for which they hold tokens or have developed. This can be as simplistic as creating a vault and determining a set of rules for the new platform for fellow project owners to stake on, or as complex as requiring extensive off-chain logic. The scope of Ybankrupt network is not to manage these proposals themselves, but to allow contracts to register as proposals for new developers to contribute and be rewarded for their work.

## Proposals

A Job is the term used to refer to a smart contract that wishes an external actor to perform an action. The external actor would in turn be rewarded upon approval of integration by the dao. For this reason they register as a proposal, and developers can connect/wrap the tokens inside the vaults for the failed project into the new project.

### Becoming a Proposer

To join as a Proposer you call ```bond(uint)``` on the Ybankrupt contract. You do not need to have BNKRPT tokens to join as a Proposer, so you can join with ```bond(0)```. There is a 3 day bonding delay before you can activate as a Proposer. Once the 3 days have passed, you can call ```activate()```. Once activated you ```lastProposal``` timestamp will be set to the current block timestamp.

### Registering a Proposal

A Proposal can be any system that requires external execution, the scope of Ybankrupt is not to define or restrict the action taken, but to create an incentive mechanism for all parties involved. There are two cores ways to create a Proposal.

#### Registering a Proposal via Governance

If you prefer, you can register as a Proposal by simply submitting a proposal via Governance, to include the contract as a job. If governance approves, no further steps are required.

#### Registering a Proposal via Contract Interface

You can register as a proposal by calling ```addLiquidityToJob(address,uint)``` on the Ybankrupt contract. You must not have any current active proposals associated with this account. Calling ```addLiquidityToJob(address,uint)``` will create a pending Governance vote for the proposal specified by address in the function arguments. You are limited to submit a new proposal request via this address every ```14 days```.

## Proposal Interface


## Gitcoin Grants Proposal registration



### Proposal Credits and rewards to developers

As mentioned in Job Interface, a job has a set amount of ```credits``` that they can award developers with. To receive ```credits``` you do not need to purchase BNKRPT tokens, instead you need to provide BNKRPT-WETH liquidity in Uniswap. This will give you an amount of credits equal to the amount of BNKRPT tokens in the liquidity you provide.

Your liquidity remains locked for the duration of the proposal. Your liquidity provided is never reduced and as such you can remove it whenever the proposal expires or is executed.


To add credits, you simply need to have BNKRPT-WETH LP tokens, you then call ```addLiquidityToJob(address,uint)``` specifying the proposal in the address and the amount in the uint. This will then transfer your LP tokens to the contract and keep them in escrow. You can remove your liquidity at any time by calling ```unbondLiquidityFromJob()```, this will allow you to remove the liquidity after 14 days by calling ```removeLiquidityFromJob()```

## LICENSING
Copyright @2021 YBankrupt

