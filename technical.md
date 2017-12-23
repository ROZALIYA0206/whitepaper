<img src="https://i.imgur.com/mpgAQZc.png">

## Whitepaper

### Abstract

Current architectures all suffer from a number of issues: Extensibility, scalability and lack of on-chain data availability. Up until now, the primitive nature of the blockchain has posed restrictions on the development of exciting DApps. We believe these problems stem from the relationship between two very important parts of the consensus architecture, namely canonicality and validity, too closely together.

Lack of on-chain resources have put a strain on complex blockchain innovation and use cases. The use of Oracles remove the true purpose of blockchain's core functionality by adding a centralized party to handle off-chain data.

This Rublix whitepaper introduces an architecture which fundamentally sets itself apart from the rest of the existing blockchains by integrating a strategic consensus method for reliable market data accessible on-chain.

Rublix is proposing a trustless and decentralized blockchain which enables real-time market data to be accessed easily through its chain while retaining maximum validity through the utilization of several data sources, and using a consensus agreement to determine the final accurate value. This gives traders, fund managers and investors the power to write smart contracts with the added ability of executing commands based on an underlying price of a stock, cryptocurrency and other markets.

# Developing an Efficient and High Quality Blockchain

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

# 1. Hybrid Consensus Algorithm

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

# 2. Market Data Consensus Model

<p align="center">
<img src="https://i.imgur.com/1ew2b6H.png">
</p>

### 2.2 Node/Validator Weighting

We anticpate a reputation algorithm to reward validators which are truthful and provide consistant accurate information. Validators with a higher reputation will be prioritized to provide data over its weaker brothers.

Rublix will attempt to provide reputable data on-chain by:

* Providing agent incentives across the network
* Incorporating stake disincentives to put a cost on malicious behavior
* Developing a strong, statistics based reputation engine which incorporates a degree of machine learning in future iterations
* Developing a scalable, decentralized reputation score system which allows the network to store historically informed reputation scores across all nodes, or so that nodes are enabled to inquire about reputation information via other nodes which have transacted with the agent in question

<p align="center">
<img src="https://i.imgur.com/8ZQQ2dj.png">
</p>

### 2.3 Remaining Trustless

We introduce a node layer with real-time market data integration using multiple data sources to reach value consensus. The values are not always based on averages but 

### 2.4 Ethereum Prototype Contracts

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

By integrating the data supply system into the Nodes at genesis we are able to overcome these issues on the Rublix Blockchain.

### 2.5 Use Cases

#### Inexpensive Network

The hybrid consensus model provides an inexpensive way to secure the network. Users can run existing DApps on the Rublix Blockchain and spend less money on transaction fees. Overall cost of the network’s security will also be cheaper due to lower market cap. 

#### No Miners

Because consensus lies in the validators (NODES) with no mining required, we are able to have blazing fast transaction speeds while not having to worry about scalability.

# 3. Releases

### Genesis

The first release of the Rublix Blockchain will be established by 20 internal validators.

# 4. Governance Model

Governance is the process by which people reach consensus on subjective matters that cannot be controlled entirely by software algorithms. In the Rublix instance, initial validators have to be choosen by the power of a select few in order to secure the network. The Rublix software-based blockchain implements a governance process that efficiently combines a hybrid Proof of Authority and Proof of Stake protocol. In order for a user to become a validator, they must be invited by an authoritive figure and stake the same amount of tokens as the existing validator who elected them. The agents stake can be gifted or purchased on an exchange.

A blockchain based on the Rublix software recognizes that power originates within the token holders and initial validators. The block validators and producers are given limited and checked authority to freeze accounts, update defective applications, and propose hard forking changes to the underlying protocol.

Embedded into the Rublix software is the election of block producers. Before any change can be made to the blockchain these block producers must approve it. If the block producers refuse to make changes desired by the token holders then they can be voted out. If the block producers make changes without permission of the token holders then all other non-producing full-node validators (exchanges, etc) will reject the change.

# 5. Upgrading and Maintaining the Protocol

Due to the nature of blockchains, hard forks, and bugs, the initial release of the Rublix Blockchain will retain a controlled group of validators for a period of 6 months. This period will allow the software to perform as normal but allow the development team to retain control of upgrading software quickly. After a sufficent time has passed with no software issues, the validators will then be able to extend invites to the public. This method will allow us to test the network sufficently and prevent hard forks from occuring at early stages.

1. Validators acknowledge a change is being requested to the software.
2. Validators propose a change to the constitution and obtains 66% approval.
3. Validators maintain 66% approval for 14 consecutive days (2 weeks).
4. By default configuration of the Rublix Blockchain software, the process of updating the blockchain to add new features takes 2 to 3 months, while updates to fix non-critical bugs that do not require changes to the constitution can take 1 to 2 months.
5. All validators that do not upgrade to the new code shut down automatically.

# Emergency Updates and Changes

The validators may accelerate the process if a software change is required to fix an extemely harmful bug or security exploit that is actively harming users. Generally speaking it could be against the constitution for accelerated updates to introduce new features or fix harmless bugs.

# Disclaimer 

This Rublix whitepaper is for information purposes only and is subject to change. Rublix does not guarantee the accuracy of or the conclusions reached in this white paper, and this whitepaper is provided as is. Rublix does not make and expressly disclaims all representations and warranties, express, implied, statutory or otherwise, whatsoever, including, but not limited to: 

1. Warranties of merchantability, fitness for a particular purpose, suitability, usage, title or non-infringement.
2. The contents of this white paper are free from error or misinformation.
3. That such contents will not infringe third-party rights.
 
Rublix and its affiliates shall carry no liability for damages of any kind arising out of the use, reference to, or reliance on this white paper or any of the content contained herein, even if advised of the possibility of such damages. In no event will Rublix or its affiliates be liable to any person or entity for any damages, losses, liabilities, costs or expenses of any kind, whether direct or indirect, consequential, compensatory, incidental, actual, exemplary, punitive or special for the use of, reference to, or reliance on this whitepaper or any of the content contained herein, including, without limitation, any loss of business, revenues, profits, data, use, goodwill or other intangible losses.

Copyright (c) 2018 Rublix Without permission, anyone may use, reproduce or distribute any material in this whitepaper for non-commercial and educational use (i.e., other than for a fee or for commercial purposes) provided that the original source and the applicable copyright notice are cited and proper credit is given.