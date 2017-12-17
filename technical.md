<img src="https://i.imgur.com/mpgAQZc.png">

## Whitepaper

### Abstract

Current architectures all suffer from a number of issues: Extensibility, scalability and lack of on-chain data availability. Up until now, the primitive nature of the blockchain has posed restrictions on the development of exciting DApps. We believe these problems stem from the relationship between two very important parts of the consensus architecture, namely canonicality and validity, too closely together.

Lack of on-chain resources have put a strain on complex blockchain innovation and use cases. The use of Oracles remove the true purpose of blockchain's core functionality by adding a centralized party to handle off-chain data.

This Rublix whitepaper introduces an architecture which fundamentally sets itself apart from the rest of the existing blockchains by integrating a strategic consensus method for reliable market data accessible on-chain.

Rublix is proposing a trustless and decentralized blockchain which enables real-time market data to be accessed easily through its chain while retaining maximum validity through the utilization of several data sources, and using a consensus agreement to determine the final accurate value. This gives traders, fund managers and investors the power to write smart contracts with the added ability of executing commands based on an underlying price of a stock, cryptocurrency and other markets.

### 1. Hybrid Consensus Algorithm

Proof of Authority x Proof of Stake Model

The Proof of Authority model provides one of the highest levels of security as an attacker with unwanted connection or hacked authority can not overwhelm the entire network potentially reverting or disrupting all transactions. By allowing a trusted set of individuals to validate blocks, we dramatically lower the risk of malicious nodes trying to alter the chain with false information.

This paper introduces an architecture, the Rublix chain and the Hedge DApp which showcases the power of the Rublix Blockchain.

### 2. Market Data Consensus Model

![alt text](https://i.imgur.com/1ew2b6H.png "Market Data Model")

#### 2.2 Node Weighting

We anticpate a reputation algorithm to reward nodes which are truthful and provide consistant accurate information. Nodes with a higher reputation will be prioritized to provide data over its weaker brothers.

Rublix will attempt to providing reputable data on-chain by:

* Providing agent incentives across the network
* Incorporating stake disincentives to put a cost on malicious behavior
* Developing a strong, statistics based reputation engine which incorporates a degree of machine learning in future iterations
* Developing a scalable, decentralized reputation score system which allows the network to store historically informed reputation scores across all nodes, or so that nodes are enabled to inquire about reputation information via other nodes which have transacted with the agent in question

#### 2.3 Remaining Trustless

We introduce a node layer with real-time market data integration using multiple data sources to reach value consensus.

#### 2.4 Ethereum Prototype Contracts

We have created Smart Contracts using Oraclize which demonstrate the functionality of bringing external market data from a single API onto the chain for Smart Contract resolution. Unfortunately the real-time aspect will not be able to operate due to excessive fees from high frequency API queries. Using Oracles on the Ethereum chain we run into three major problems:

```
1. Inability to obtain data in real-time
2. Centralized API source removes trust factor
3. Expensive GAS fees on the Ethereum network
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

#### 3. Releases

Genesis - The first release of the Rublix Blockchain.

### Disclaimer 

This Rublix whitepaper is for information purposes only and is subject to change. Rublix does not guarantee the accuracy of or the conclusions reached in this white paper, and this whitepaper is provided “as is”. Rublix does not make and expressly disclaims all representations and warranties, express, implied, statutory or otherwise, whatsoever, including, but not limited to: 
1. Warranties of merchantability, fitness for a particular purpose, suitability, usage, title or non-infringement.
2. The contents of this white paper are free from error or misinformation.
3. That such contents will not infringe third-party rights.
 
Rublix and its affiliates shall carry no liability for damages of any kind arising out of the use, reference to, or reliance on this white paper or any of the content contained herein, even if advised of the possibility of such damages. In no event will Rublix or its affiliates be liable to any person or entity for any damages, losses, liabilities, costs or expenses of any kind, whether direct or indirect, consequential, compensatory, incidental, actual, exemplary, punitive or special for the use of, reference to, or reliance on this whitepaper or any of the content contained herein, including, without limitation, any loss of business, revenues, profits, data, use, goodwill or other intangible losses.

Copyright (c) 2018 Rublix Without permission, anyone may use, reproduce or distribute any material in this whitepaper for non-commercial and educational use (i.e., other than for a fee or for commercial purposes) provided that the original source and the applicable copyright notice are cited and proper credit is given.