<img src="https://i.imgur.com/mpgAQZc.png">

## Whitepaper

### Abstract

Current architectures all suffer from a number of issues: Extensibility, scalability and lack of on-chain data availability. Up until now, the primitive nature of the blockchain has posed restrictions on the development of exciting DApps. We believe these problems stem from the relationship between two very important parts of the consensus architecture, namely canonicality and validity, too closely together.

Lack of on-chain resources have put a strain on complex blockchain innovation and use cases. The use of Oracles remove the true purpose of blockchain's core functionality by adding a centralized party to handle off-chain data.

This Rublix whitepaper introduces an architecture which fundamentally sets itself apart from the rest of the existing blockchains by integrating a strategic consensus method for reliable market data accessible on-chain.

Rublix is proposing a trustless and decentralized blockchain which enables real-time market data to be accessed easily through its chain while retaining maximum validity through the utilization of several data sources, and using a consensus agreement to determine the final accurate value. This gives traders, fund managers and investors the power to write smart contracts with the added ability of executing commands based on an underlying price of a stock, cryptocurrency or forex market.

### Table of Contents

1. [Blockchain Mission](#1-developing-an-efficient-and-high-quality-blockchain)
   * [UX](#incredible-ux)
   * [Scalability](#scalability)
   * [Upgrading and Bug Recovery](#quick-upgrades-and-bug-recovery)
   * [Low Latency](#low-latency)
   * [Performance](#performance)
2. [Hybrid Consensus Algorithm](#2-hybrid-consensus-algorithm)
   * [Proof of Authority / Stake](#proof-of-authority--proof-of-stake-model)
3. [Market Data Concensus Model](#3-market-data-consensus-model)
   * [Validator Weighting](#32-validator-weighting)
   * [Remaining Trustless](#33-remaining-trustless)
   * [Ethereum Prototype Contracts](#34-ethereum-prototype-contracts)
   * [Use Cases](#35use-cases)
4. [Milestone Releases](#4-milestone-releases)
   * [Rise](#rise)
   * [Genesis](#genesis)
     * [Token Swap](#token-swap)
   * [Epilogue](#epilogue)
5. [Governance Model](#5-governance-model)
6. [Dcentralized Applications](#6-decentralized-applications)
   * [Hedge Platform](#hedge-platform)
     * [Version 1](#hedge-v1-smart-contract-integration-blueprints)
     * [Version 2](#hedge-v2-proprietary-blockchain)
7. [Upgrading and Maintaining the Protocol](#7-upgrading-and-maintaining-the-protocol)
8. [Disclaimer](#8-disclaimer)

# 1. Developing an Efficient and High Quality Blockchain

In order to gain worldwide use, our blockchain will need to be flexible enough to meet the following criteria:

#### Incredible UX

Due to the complex nature of the Blockchain, in order to attract the masses to the platform, users must be welcomed with an interface which is easy to navigate, understand and get used to.

#### Scalability

Disruptive projects like Facebook, Uber and Youtube all handle thousands if not millions of active connections on the daily. Current mainstream Blockchain projects are unable to handle such loads and therefore a platform that can handle a large amount of active users simultaneously is essential to future success.

#### Quick Upgrades and Bug Recovery

Businesses building blockchain based applications need the flexibility to enhance their applications with new features.

All Blockchain projects are subject to bugs, even with the most rigorous amount of testing. The platform must be robust enough to fix bugs quickly when they inevitably occur.

#### Low Latency

A good UX demands reliable feedback with a delay of no more than a few seconds. Longer delays frustrate users and make applications built on a blockchain less competitive with existing centralized alternatives.

#### Coordinated Performance

Large scale applications need to divide the workload across multiple CPUs and computers. Validators will require an expansion method which does not sacrifice security.

# 2. Hybrid Consensus Algorithm

#### Proof of Authority / Proof of Stake Model

The Proof of Authority model provides one of the highest levels of security as an attacker with unwanted connection or hacked authority can not overwhelm the entire network potentially reverting or disrupting all transactions. By initially allowing a trusted set of individuals to validate blocks, we dramatically lower the risk of malicious nodes trying to alter the chain with false information.

Benefits of the Rublix Consensus Model:

```
1. Lower transaction fees
2. Energy efficent
3. More secure than traditional PoW protocols
4. Incredible scalability
```

We anticipate validators to be invite only. To start the chain, we will assign 20 internal validators to secure the network.

# 3. Market Data Consensus Model

<p align="center">
<img src="https://i.imgur.com/5SjgY1H.png">
</p>

### 3.2 Validator Weighting

We anticpate a reputation algorithm to reward validators which are truthful and provide consistant accurate information. Validators with a higher reputation will be prioritized to provide data over its weaker brothers.

Rublix will attempt to provide reputable data on-chain by:

* Providing agent incentives across the network
* Incorporating stake disincentives to put a cost on malicious behavior
* Developing a strong, statistics powered reputation engine which incorporates a degree of machine learning in future iterations
* Developing a scalable, decentralized reputation scoring system which allows the network to store historically informed reputation scores across all validators, or so that validators are enabled to inquire about reputation information via others which have transacted with the agent in question

<p align="center">
<img src="https://i.imgur.com/QDh4w7q.png">
</p>

### 3.3 Remaining Trustless

Incase of a faulty validator on the network delivering data, we want to be more accurate than taking a simplified average.

We introduce a validator/node layer with real-time market data integration using multiple data sources to reach price action consensus. The values are based off validator reputation and averages from multiple real-time Websockets.

### 3.4 Ethereum Prototype Contracts

We have created Smart Contracts using Oraclize which demonstrate the functionality of bringing external market data from a single API onto the chain for Smart Contract resolution. Unfortunately the real-time aspect will not be able to operate due to excessive fees from high frequency API queries. Using Oracles on the Ethereum chain we run into three major problems:

```
1. Inability to obtain data in real-time
2. Centralized API source removes trust factor
3. Expensive GAS fees on the Ethereum network
4. Consensus cannot be automated
```

An example of one of our test Smart Contracts is demonstrated below:

```
pragma solidity ^0.4.11;
import "github.com/oraclize/ethereum-api/oraclizeAPI.sol";

contract ExampleContract is usingOraclize {

    string public AAPL;
    event updatedPrice(string price);
    event newOraclizeQuery(string description);

    function ExampleContract() payable {
        updatePrice();
    }

    function __callback(bytes32 myid, string result) {
        if (msg.sender != oraclize_cbAddress()) throw;
        EURGBP = result;
        updatedPrice(result);
    }

    function updatePrice() payable {
        if (oraclize_getPrice("URL") > this.balance) {
            newOraclizeQuery("Query was NOT sent, please add some ETH to cover for the query fee");
        } else {
            newOraclizeQuery("Query was sent, standing by for the answer..");
            oraclize_query("URL", "json(https://www.quandl.com/api/v3/datatables/SHARADAR/SEP.json?ticker=AAPL&api_key=<YOURAPIKEY>)");
        }
    }
}
```

By integrating the data supply system into the validators level at genesis we are able to overcome these limitations on the Rublix Blockchain.

### 3.5 Use Cases

#### Inexpensive Network

The hybrid consensus model provides an inexpensive way to secure the network. Users can run existing DApps on the Rublix Blockchain and spend less money on transaction fees. Overall cost of the network's security will also be cheaper due to considerably lower market cap. 

#### No Miners

Because consensus lies in the validators (NODES) with no mining required, we are able to have blazing fast transaction speeds while not having to worry about scalability.

# 4. Milestone Releases

Due to the nature and complexity of Blockchain technology, the Rublix project will be spread into multiple stages.

#### Rise

The Hedge Alpha platform operates at a preliminary stage on the Ethereum network using a centeralized Oracle to bring market data onto the chain for basic validation. Consensus is reached by manually executing the Smart Contract by a 3rd party to collect data from the Oracle. The user is rewarded transaction fees as bounty.

#### Genesis

We will migrate from Rise to Genesis once our testnet is live, appears to be functioning appropriately, market data is implemented on-chain and is fully stable in the eyes of our core developers and auditors.

The first release of the Rublix Blockchain will be established with 20 internal validators. The chain debut will feature several simple DApps and vigerous public testing will occur.

##### Token Swap

A token swap is planned for after the Rublix network is deployed and deemed to be in a stable state by its senior developers.

#### Epilogue

The Hedge platform is completely migrated onto the Rublix Blockchain. DApps are built and running efficently on the newly established chain.

# 5. Governance Model

Governance is the process by which people reach consensus on subjective matters that cannot be controlled entirely by software algorithms. In the Rublix instance, initial validators have to be choosen by the power of a select few in order to secure the network. The Rublix software-based blockchain implements a governance process that efficiently combines a hybrid Proof of Authority and Proof of Stake protocol. In order for a user to become a validator, they must be invited by an authoritive figure and stake the same amount of tokens as the existing validator who elected them. The agents stake can be gifted or purchased on an exchange. This ensures the newcomer is serious about becoming an elite member on the Rublix network.

A blockchain based on the Rublix software recognizes that power originates within the token holders and initial validators. The block validators and producers are given limited and checked authority to freeze accounts, update defective applications, and propose hard forking changes to the underlying protocol.

Embedded into the Rublix software is the election of block producers. Before any change can be made to the blockchain these block producers must approve it. If the block producers refuse to make changes desired by the token holders then they can be voted out. If the block producers make changes without permission of the token holders then all other non-producing full-node validators (exchanges, etc) will reject the change.

# 6. Decentralized Applications

Rublix will migrate its development of Decentrailzed Applications on the Rublix Blockchain.

### Hedge Platform

Our flagship DApp, Hedge, is in development and currently being built on the Ethereum network, but will eventually be migrated to the Rublix Blockchain. Hedge is a networking hub for financial and cryptocurrency trading experts and newcomers seeking real-time trading predictions for cryptocurrencies, stocks, options, commodities, or any other tradable product.
 
The Hedge platform incorporates blockchain technology directly into the functionality whereby traders submit predictions into a smart contract-driven "blueprint" that will execute true or false results based on real market information. Hedge rewards traders with RBLX Tokens for successful predictions as paid for by the blueprint purchasers. Traders with successful predictions will also be rewarded positive ranking points on the Hedge platform based on the smart contract authority and Hedge's Proof-of-Ranking algorithm. Blueprints will thus carry an intrinsic value based on the trader's track record and ranking.
 
Users who identify a trader with a high ranking and reputation can purchase their blueprints using RBLX Tokens to gain access to that trader's predictions. If the trader makes a correct prediction via the blueprint, they will receive the tokens from the purchasers. Otherwise, the tokens are returned to the purchaser as coded in the smart contract. The higher the trader's ranking on Hedge, the more expensive the blueprint. This ranking, reward and verification system greatly enhances a traders credibility, motivation to succeed and earning potential, in addition to filtering out poor performers with unproven track records.

#### Hedge v1: Smart Contract Integration (Blueprints)

The first and official public release of Hedge (v1) will be in the form of an Ethereum based dApp. This will provide the groundwork necessary to release a fully functioning product utilizing our planned smart contract architecture, which will handle the majority of our anticipated features. Meanwhile, the Rublix blockchain will be in research and continue its potential development giving the entire Rublix platform ample room for future growth.

By incorporating smart contract capabilities, Hedge v1 allows for the facilitation of outcomes for analyst Blueprints. This system will be able to compare market predictions coded into each smart contract using Oracles, and then execute positive or negative rankings for the trader based on the end result of what took place in the market at a future point in time. Traders who correctly anticipate market movements will automatically be rewarded with positive ranking points on the Hedge platform based on the smart contract authority.

In our context, an Oracle is an agent that finds, validates and submits market information to the blockchain to be used by our smart contracts. When a particular value (i.e., date/time, price, etc.) is reached an event automatically triggers. The primary task of an Oracle is to provide these values to the smart contract in a secure and accurate manner.

This heightened level of validation will greatly enhance traders' credibility and potential to attract subscribers to their private channel, while at the same time filtering out poor performers with unproven track records.

#### Hedge v2: Proprietary Blockchain

Hedge v2, which is planned for a late-2018 release, will run off Rublix's core blockchain. By upgrading to this unique, industry specific technology and framework, the Rublix platform will incorporate the following upgraded features:

* Full empowerment, customization and control for future updates and integrations to the Hedge platform, as well as the ability to build out more complex projects.

* Real-time market data will allow blueprints to be solved on-chain.

* A reduction in dependency on the Ethereum Network and its inherent limitations.

* Ability to work with community members who want to build on top of our finance platform using our Developer Toolkit.

#### Blueprint Smart Contracts

Simple description of a Blueprint creation:

John accesses the Hedge application, undertakes technical analysis on the BTCUSD chart and decides to post the dynamics of a trade he is going to make. He clicks “Create Blueprint” then enters the follow data:

* Expiry of the smart contract - When does this trade end?
* Category - What kind of product is it (cryptocurrency, token, equity, ETF, option, etc.)?
* Entry and Exit points - At what price does this trade start and finish?
* Address - Where will the RBLX tokens be distributed if this trade is successful?

The remaining data will be automatically populated based on the fundamentals of the Blueprint:

* Potential gain - The percentage of gain between the entry and exit points.
* Blueprint buy-in price (See Appendix.)
* Ranking impact (See Appendix.)

# 7. Upgrading and Maintaining the Protocol

Due to the nature of blockchains, hard forks, and bugs, the initial release of the Rublix Blockchain will retain a controlled group of validators for a period of 6 months. This period will allow the software to perform as normal but allow the development team to retain control of upgrading software quickly. After a sufficent time has passed with no software issues, the validators will then be able to extend invites to the public. This method will allow us to test the network sufficently and prevent hard forks from occuring at early stages.

1. Validators acknowledge a change is being requested to the software.
2. Validators propose a change to the constitution and obtains 66% approval.
3. Validators maintain 66% approval for 14 consecutive days (2 weeks).
4. By default configuration of the Rublix Blockchain software, the process of updating the blockchain to add new features takes 2 to 3 months, while updates to fix non-critical bugs that do not require changes to the constitution can take 1 to 2 months.
5. All validators that do not upgrade to the new code shut down automatically.

# Emergency Updates and Changes

The validators may accelerate the process if a software change is required to fix an extemely harmful bug or security exploit that is actively harming users. Generally speaking it could be against the constitution for accelerated updates to introduce new features or fix harmless bugs.

# 8. Disclaimer 

This Rublix whitepaper is for information purposes only and is subject to change. Rublix does not guarantee the accuracy of or the conclusions reached in this white paper, and this whitepaper is provided as is. Rublix does not make and expressly disclaims all representations and warranties, express, implied, statutory or otherwise, whatsoever, including, but not limited to: 

1. Warranties of merchantability, fitness for a particular purpose, suitability, usage, title or non-infringement.
2. The contents of this white paper are free from error or misinformation.
3. That such contents will not infringe third-party rights.
 
Rublix and its affiliates shall carry no liability for damages of any kind arising out of the use, reference to, or reliance on this white paper or any of the content contained herein, even if advised of the possibility of such damages. In no event will Rublix or its affiliates be liable to any person or entity for any damages, losses, liabilities, costs or expenses of any kind, whether direct or indirect, consequential, compensatory, incidental, actual, exemplary, punitive or special for the use of, reference to, or reliance on this whitepaper or any of the content contained herein, including, without limitation, any loss of business, revenues, profits, data, use, goodwill or other intangible losses.

Copyright (c) 2018 Rublix Without permission, anyone may use, reproduce or distribute any material in this whitepaper for non-commercial and educational use (i.e., other than for a fee or for commercial purposes) provided that the original source and the applicable copyright notice are cited and proper credit is given.

# 9. Special Thanks

Special thanks to the welcoming Ethereum community. Thank you for all the support and feedback: Jason Matthison, Ameer Rosic.
