<img src="https://i.imgur.com/mpgAQZc.png">

## Whitepaper

### Abstract

Until now, the primitive nature of blockchain technology and the lack of on-chain resources have hindered complex blockchain innovation and has posed restrictions on the development of exciting and elaborate DApps. Many blockchain architectures suffer from a number of issues: extensibility, scalability and on-chain data availability. We believe these problems stem from the relationship between two very important parts of the consensus architecture - canonicality and validity - being too closely associated. Furthermore, the use of Oracles adds a centralized party to manage off-chain data which defeats the true purpose of blockchains' core functionality.

This Rublix whitepaper introduces an architecture that integrates a strategic consensus method for reliable market data accessible on-chain.

Rublix is proposing a trustless and decentralized blockchain that enables real-time market pricing data to be accessed on-chain while maintaining integrity by utilizing several data sources and a unique consensus agreement to determine accurate values. This gives traders, fund managers, investors and users of any kind the power to write smart contracts with the added ability of executing commands based on an underlying price of a stock, cryptocurrency, forex market, et al.

### Table of Contents

1. [Blockchain Mission](#1-developing-an-efficient-and-high-quality-blockchain)
   * [Attractive UX & Usability](#incredible-ux)
   * [Scalability](#scalability)
   * [Bug Recovery & Quick Upgrades](#quick-upgrades-and-bug-recovery)
   * [Functionality & Purpose](#functionality)
   * [Coordinated Performance](#performance)
2. [Hybrid Consensus Algorithm](#2-hybrid-consensus-algorithm)
   * [Proof-of-Authority / Proof-of-Stake Model](#proof-of-authority--proof-of-stake-model)
3. [Market Data Consensus Model](#3-market-data-consensus-model)
   * [Market Data Consensus Diagram](#31-market-data-consensus-diagram)
   * [Validator Weighting](#32-validator-weighting)
   * [Remaining Trustless](#33-remaining-trustless)
   * [Ethereum Prototype Contracts](#34-ethereum-prototype-contracts)
   * [Use Cases](#35-use-cases)
4. [Milestone Releases](#4-milestone-releases)
   * [Rise](#rise)
   * [Genesis](#genesis)
     * [Token Swap](#token-swap)
   * [Epilogue](#epilogue)
5. [Governance Model](#5-governance-model)
6. [Decentralized Applications](#6-decentralized-applications)
   * [Hedge Platform](#hedge-platform)
     * [Version 1](#hedge-v1-smart-contract-integration-s)
     * [Version 2](#hedge-v2-proprietary-blockchain)
     * [Blueprint Smart Contracts](#blueprint-smart-contracts)
     * [Proof-of-Ranking Algorithm](#)
       * [Overview](#overview)
       * [Implementation](#implementation)
7. [RBLX Token](#7-rblx-token)
     * [Purpose](#purpose)
     * [Reward Mechanism](#reward-mechanism)
8. [Upgrading and Maintaining the Protocol](#8-upgrading-and-maintaining-the-protocol)
9. [Disclaimer](#9-disclaimer)

# 1. Blockchain Mission

In order to develop an efficient and high quality blockchain for worldwide use, the Rublix Blockchain will need the ability and flexibility to meet the following criteria:

#### Attractive UX & Usability

Due to the complex nature of the blockchain, users must be welcomed with an interface that is easy to navigate, understand and use in order to achieve mass adoption. The Rublix blockchain will be built in the widely used Python language.

#### Scalability

Disruptive centralized projects like Facebook, Uber and Youtube all handle millions of active connections simultaneously. In order to achieve similar worldwide scalability, decentralized applications built on the Rublix Blockchain will utilize a unique consensus model (structured as a hybrid between Proof-of-Authority and Proof-of-Stake) that can support massive user load.

#### Functionality & Purpose

There exists a need for trusted financial information. The Rublix Blockchain is being built to make use of trusted and immutable financial data posted on-chain.

#### Quality of Information

In order to ensure the highest quality of information, the appropriate incentives and consensus mechanisms must be established. Rublix  is implementing a novel verification process combined with the most well-developed architectures on the market to ensure utmost integrity for data validation and access.

####  Bug Recovery and Quick Upgrades

All blockchain projects are subject to bugs even with the most rigorous amount of testing. Additionally, blockchain-based businesses need the ability to enhance their applications with new features. The Rublix architecture will be structured appropriately in order to upgrade functionality and fix bugs quickly and efficiently.

#### Coordinated Performance

High-load applications need to spread the workload across multiple CPUs and computers. Rublix validators will use an expansion method that does not sacrifice performance or security.

# 2. Hybrid Consensus Algorithm

#### Proof-of-Authority / Proof-of-Stake Model

The Proof-of-Authority model provides one of the highest levels of security, as an attacker with unwanted connection or hacked authority can not overwhelm the entire network by potentially reverting or disrupting all transactions. By initially allowing a trusted set of individuals to validate blocks, we dramatically lower the risk of malicious nodes trying to alter the chain with false information.

Benefits of the Rublix Consensus Model:

```
1. Lower transaction fees
2. More energy efficient
3. More secure than traditional Proof-of-Work protocols
4. Substantially higher scalability
```

We anticipate validators to be invite only. To start the chain, we will assign 20 internal validators to secure the network.

# 3. Market Data Consensus Model

#### Market Data Consensus Diagram

<p align="center">
<img src="https://i.imgur.com/5SjgY1H.png">
</p>

#### Validator Weighting

We anticpate a reputation algorithm to reward validators which are truthful and provide consistently accurate information. Validators with a higher reputation will be prioritized to provide data over its weaker brothers.

Rublix will attempt to provide reputable data on-chain by:

* Providing agent incentives across the network
* Incorporating stake disincentives to put a cost on malicious behavior
* Developing a strong, statistics-powered reputation engine which incorporates a degree of machine learning in future iterations
* Developing a scalable, decentralized reputation scoring system which allows the network to store historically informed reputation scores across all validators, or so that validators are enabled to inquire about reputation information via others which have transacted with the agent in question

<p align="center">
<img src="https://i.imgur.com/QDh4w7q.png">
</p>

#### Remaining Trustless

In case of a faulty validator on the network delivering data, we want to be more accurate than taking a simplified average.

We introduce a validator/node layer with real-time market data integration using multiple data sources to reach price action consensus. The values are based off validator reputation and averages from multiple real-time Websockets.

#### Ethereum Prototype Contracts

We have created smart contracts using Oraclize which demonstrate the functionality of bringing external market data from a single API onto the chain for smart contract resolution. Unfortunately the real-time aspect is not possible due to excessive fees from high frequency API queries. Using Oracles on the Ethereum chain we run into four major problems:

```
1. Inability to obtain real-time data
2. Centralized API source removes trust factor
3. Expensive GAS fees on the Ethereum network
4. Consensus cannot be automated
```

#### Resolving a Contract on the Ethereum Blockchain

<p align="center">
<img src="https://i.imgur.com/faaqoFf.png">
</p>

#### Conclusion

By integrating the data supply system into the validation level at genesis we are able to overcome these limitations on the Rublix Blockchain.

#### Example Code

Example of a basic Blueprint contract:

This contract compares the end of day data of `AAPL` using Quandl API.

```
pragma solidity ^0.4.20;

//***********************************START
contract RublixBluePrintContract {

  struct buyerarray {
      address etherAddress;
      uint amount;
  }

//********************************************PUBLIC VARIABLES
  
  buyerarray[] public buyerlist;
  uint public Buyers_Until_ReleaseOfContract=0;
  uint public Total_Buyers=0;
  uint public FeeRate=5;
  uint public BluePrintFund = 0;
  uint public TotalBluePrintFund = 0;
  uint public Total_Deposits=0;
  uint public Total_Payouts=0;
  uint public MinDeposit=100 finney;
  uint public entrypoint=0;
  uint public exitpoint=0;
  

  address public owner;
  uint Fees=0;
  // simple single-sig function modifier
  modifier onlyowner { if (msg.sender == owner) _ }

//********************************************INIT

  function RublixBluePrintContract() {
    owner = 0xee462a6717f17c57c826f1b4d3813495296c9;  //this contract is an attachment to RublixHedger
  }

//********************************************TRIGGER

  function() {
    enter();
  }
  
//********************************************ENTER

  function enter() {
    if (msg.value >10 finney) {

    uint amount=msg.value;
    uint payout;


    // add a new participant to the system and calculate total buyers
    uint list_length = buyerlist.length;
    Total_Buyers=list_length+1;
    Buyers_Until_ReleaseOfContract=40-(Total_Buyers % 40);
    buyerlist.length += 1;
    buyerlist[list_length].etherAddress = msg.sender;
    buyerlist[list_length].amount = amount;



    // set payout variables
     Total_Deposits+=amount;       	//update deposited amount
	    
      Fees   =amount * FeeRate/100;    // 5% fee to the owner
      amount-=amount * FeeRate/100;
	    
      BluePrintFund += amount*80/100;     // 80% to the balance
      amount-=amount*80/100;  
	    
      TotalBluePrintFund += amount;               	//remaining to the TotalBluePrintFund


    // payout fees to the owner
     if (Fees != 0) 
     {
	uint minimal= 1990 finney;
	if(Fees<minimal)
	{
      	owner.send(Fees);		//send fee to owner
	Total_Payouts+=Fees;        //update paid out amount
	}
	else
	{
	uint Times= Fees/minimal;

	for(uint i=0; i<Times;i++)   // send the fees out in packets compatible to EthVentures dividend function
	if(Fees>0)
	{
	owner.send(minimal);		//send fee to owner
	Total_Payouts+=Fees;        //update paid out amount
	Fees-=minimal;
	}
	}
     }
 
    if (msg.value >= MinDeposit) 
     {
	     
   //payout to participants	
     if(list_length%40==0 && TotalBluePrintFund > 0)   				//every 40th player wins the TotalBluePrintFund if  it's not 0
	{
	buyerlist[list_length].etherAddress.send(TotalBluePrintFund);         //send pay out to participant
	Total_Payouts += TotalBluePrintFund;               					//update paid out amount   
	TotalBluePrintFund=0;									//TotalBluePrintFund update
	}
     else   											//you either win the TotalBluePrintFund or the balance, but not both in 1 round
	if(uint(sha3(buyerlist[list_length].etherAddress,list_length))+uint(sha3(msg.gas)) % 4 ==0 && BluePrintFund > 0) 	//if the hashed length of your address is even, 
	{ 												   								//which is a 25% chance, then you get paid out all balance!
	buyerlist[list_length].etherAddress.send(BluePrintFund);        //send pay out to participant
	Total_Payouts += BluePrintFund;               					//update paid out amount
	BluePrintFund = 0;                      						//BluePrintFund update
	}
    
    
    
    //enter function ends
	}
    }
  }

//********************************************NEW OWNER

  function setOwner(address new_owner) onlyowner { //set new owner of the casino
      owner = new_owner;
  }
//********************************************SET MIN DEPOSIT

  function setMinDeposit(uint new_mindeposit) onlyowner { //set new minimum deposit rate
      MinDeposit = new_mindeposit;
  }
//********************************************SET FEE RATE

  function setFeeRate(uint new_feerate) onlyowner { //set new fee rate
      FeeRate = new_feerate;
  }
}
```

Calling the Oracle to verify the price at the end of each day:

````
pragma solidity ^0.4.20;
import "github.com/oraclize/ethereum-api/oraclizeAPI.sol";

contract RublixBluePrintPriceUpdateContract is usingOraclize {

    string public RBLXBLCPU;
    event updatedPrice(string price);
    event newOraclizeQuery(string description);

    function RublixBluePrintPriceUpdateContract() payable {
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
            //uypdate api wiht crpto
            oraclize_query("URL", "json(https://www.quandl.com/api/v3/datatables/SHARADAR/SEP.json?ticker=AAPL&api_key=<YOURAPIKEY>)");
        }
    }
}


//on daily basis mon-friday we want to update the ticker price in the contrct
````

#### Use Cases

#### Inexpensive Network

The hybrid consensus model provides an inexpensive way to secure the network. Users can run existing DApps on the Rublix Blockchain and spend less money on transaction fees. Overall cost of the network's security will also be cheaper due to considerably lower market cap. 

#### No Miners

Due to consensus lying in the validators (nodes) with no mining required, scalibility concerns subside as transactions are not reliant on resource intensive confirmations.

# 4. Milestone Releases

Due to the nature and complexity of blockchain technology, the Rublix project will be spread into multiple stages.

#### Rise

The Hedge Alpha platform operates at a preliminary stage on the Ethereum network using a centeralized Oracle to bring market data onto the chain for basic validation. Consensus is reached by manually executing the smart contract by a 3rd party to collect data from the Oracle. The user is rewarded transaction fees as bounty.

#### Genesis

We will migrate from Rise to Genesis once our testnet is live and functioning appropriately, market data is correctly implemented on-chain and has passed rigorous testing from our senior developers and the Rublix audit committee.

The first release of the Rublix Blockchain will be established with 20 internal validators. The chain debut will feature several simple DApps and extensive public testing will occur.

##### Token Swap

A token swap will occur after the Rublix network is deployed, tested and deemed to be in a stable state by the Rublix audit committee and 3rd party consultants.

#### Epilogue

The Hedge platform will be completely migrated onto the Rublix Blockchain. Subsequent DApps may be built and deployed on the newly established chain.

# 5. Governance Model

Governance is the process in which actors reach consensus on subjective matters that cannot be controlled entirely by software algorithms. In the Rublix instance, initial validators must be chosen by the power of a select few in order to secure the network. The Rublix Blockchain implements a governance process that efficiently combines a hybrid Proof-of-Authority and Proof-of-Stake protocol. In order for a user to become a validator, they must be invited by an authoritive figure and stake the same number of tokens as the existing validator who elected them. The agents' stake can be gifted or purchased on an exchange. This procedure ensures the newcomer is committed to becoming a trusted validator on the Rublix network.

A blockchain based on the Rublix software recognizes that power originates within the token holders and initial validators. The block validators and producers are given limited and checked authority to freeze accounts, update defective applications and propose changes requiring a hard fork to the underlying protocol.

Embedded into the Rublix software is the election of block producers. Before any changes can be made to the blockchain, block producers must approve the proposed alterations. If block producers refuse to undertake the suggested changes made by the token holders, the proposals can be voted out. If block producers make changes without permission of the token holders then all other non-producing full-node validators (for example, exchanges) will reject the change.

# 6. Decentralized Applications

Rublix will migrate its development of decentrailzed applications onto the Rublix Blockchain.

### Hedge Platform

Our flagship DApp, Hedge, is in development and is currently being built on the Ethereum network but will eventually be migrated to the Rublix Blockchain. Hedge is a networking hub for financial and cryptocurrency trading experts and newcomers seeking real-time trading predictions for cryptocurrencies, stocks, options, commodities or any other tradable product.
 
The Hedge platform incorporates blockchain technology directly into the functionality whereby traders submit predictions into a smart contract-driven "Blueprint" that will execute true or false results based on real market information. Hedge rewards traders with RBLX Tokens for successful predictions as paid for by the Blueprint purchasers. Traders with successful predictions will also be rewarded positive ranking points on the Hedge platform based on the smart contract authority and Hedge's Proof-of-Ranking algorithm. Blueprints will thus carry an intrinsic value based on the trader's track record and ranking.
 
Users who identify a trader with a high ranking and reputation can purchase their Blueprints using RBLX Tokens to gain access to that trader's predictions. If the trader makes a correct prediction via the Blueprint, they will receive the tokens from the purchasers. Otherwise, the tokens are returned to the purchaser as coded in the smart contract. The higher the trader's ranking on Hedge, the more expensive the Blueprint. This ranking, reward and verification system greatly enhances a trader's credibility, motivation to succeed and earning potential, in addition to filtering out poor performers with unproven track records.

#### Hedge v1: Smart Contract Integration (Blueprints)

The first and official public release of Hedge (v1) will be in the form of an Ethereum based dApp. This will provide the groundwork necessary to release a fully functioning product utilizing our planned smart contract architecture on the Rublix Blockchain, which will handle all of our anticipated features. Meanwhile, the Rublix Blockchain will continue to be researched and built and continue its  development giving Hedge and other Rublix projects ample room for growth.

By incorporating smart contract capabilities, Hedge v1 allows for the facilitation of outcomes for analyst Blueprints. This system will be able to compare market predictions coded into each smart contract using Oracles, and then execute positive or negative rankings for the trader based on the end result of what took place in the market at a future point in time. Traders who correctly anticipate market movements will automatically be rewarded with positive ranking points on the Hedge platform based on the smart contract authority.

In our context, an Oracle is an agent that finds, validates and submits market information to the blockchain to be used by our smart contracts. When a particular value (i.e., date/time, price, etc.) is reached an event automatically triggers. The primary task of an Oracle is to provide these values to the smart contract in a secure and accurate manner.

This heightened level of validation will greatly enhance traders' credibility and potential to attract subscribers to their private channel, while at the same time filtering out poor performers with unproven track records.

#### Hedge v2: Proprietary Blockchain

Hedge v2, which is planned for a late-2018 release, will run off Rublix's core blockchain. By upgrading to this unique, industry specific technology and framework, the Rublix platform will incorporate the following upgraded features:

* Full empowerment, customization and control for future updates and integrations to the Hedge platform, as well as the ability to build out more complex features.

* Real-time market data will allow Blueprints to be solved on-chain automatically withouth the need for an Oracle.

* A reduction in dependency on the Ethereum network and its inherent limitations.

* Ability to work with community members who want to build on top of our finance platform using our Developer Toolkit.

#### Blueprint Smart Contract Details

Each smart contract is written based on parameters set by the trader using the Hedge web application. Any audience member can then 'buy' this analysis, which is called a 'Blueprint.' Depending on the outcome of the Blueprint (a correct or incorrect trade), the contract will then execute an outcome when specific parameters are carried out. The executed contract will affect the trader's reputation, ranking and RBLX earnings; RBLX is only awarded from the audience to the trader upon making a correct Blueprint, otherwise the RBLX tokens are returned to the audience. This means that audience members will only 'pay' for trader recommendations with RBLX if their Blueprint is 'true,' otherwise the smart contract will execute a 'false' outcome and return the RBLX to the audience member. 
 
The purpose of the smart contract integration into the Blueprints is to create a higher level of validation, verification and transparency of analyst performance, which in turn affects their ranking and reward. Plenty of traders and analysts who make market predictions on social media, during interviews or to clients directly have uncertain ramifications for being incorrect and may even delete or refute previous predictions. The Hedge platform intends to filter out poor performers and allows traders' true wisdom to speak for itself by utilizing verified smart contracts posted on the blockchain.


#### *Step by Step creation of a Blueprint contract:*

John accesses the Hedge application, undertakes technical analysis on the BTCUSD chart and decides to post the dynamics of a trade he is going to make. He clicks “Create Blueprint” then enters the following data:

* Expiration of the Contract - When does the trade end?
* Category - What kind of product is it (cryptocurrency, token, equity, ETF, option, etc.)?
* Entry and Exit points - At what price does this trade start and finish?
* Address - Where will the RBLX tokens be distributed if this trade is successful?

The remaining data will be automatically populated based on the fundamentals of the Blueprint:

* Potential gain from the trade as a percentage.
* Blueprint purchase price based on John's ranking on the Hedge platform.
* Ranking impact for a correct or incorrect Blueprint.


#### Proof-of-Ranking Algorithm

##### Overview

The Proof of Ranking algorithm is a propritary multi variable set of forumlas which assigns each trader on the platform an overall rank. 

##### Implementation

The premis of the formula is to filter each individual and provide an accurate risk analysis on the user as they grow their track record.

Let R(u,t) be the Proof-Of-Rank function describing a user u at a time t. R(u,t) is a real-valued function where `u=(u\_1,u\_2,...,u\_N)` is an N-dimensional vector of real values.

````
R(u,t) = f(u,t, w(t))
````

Where w(t) is a real-valued scalar weighting function, independent of the user u, and only depending on the time.

# 7. RBLX Token

### Purpose

The Rublix token (RBLX) will be used for the Hedge v1 platform while on the Ethereum network. It will allow for an easy transition to the token swap which will take place at a later date. 

### Reward Mechanism

The RBLX token is used as a reward token within its eco-system.

# 8. Upgrading and Maintaining the Protocol

Due to the nature of blockchains, hard forks, and bugs, the initial release of the Rublix Blockchain will retain a controlled group of validators for a period of 6 months. This period will allow the software to perform as normal but allow the development team to retain control of upgrading software quickly. After a sufficent amount of time with no software issues, the validators will then be able to extend invites to the public. This method will allow us to test the network and its validators sufficently and prevent hard forks from occuring at early stages.

1. Validators acknowledge a change is being requested to the software.
2. Validators propose a change to the constitution and obtains 66% approval.
3. Validators maintain 66% approval for 14 consecutive days (2 weeks).
4. By default configuration of the Rublix Blockchain software, the process of updating the blockchain to add new features takes 2 to 3 months, while updates to fix non-critical bugs that do not require changes to the constitution can take 1 to 2 months.
5. All validators that do not upgrade to the new code shut down automatically.

# Emergency Updates and Changes

The validators may accelerate the process if a software change is required to fix an extemely harmful bug or security exploit that is actively harming users. It could be against the constitution for accelerated updates to introduce new features or fix harmless bugs.

# 9. Disclaimer 

This Rublix whitepaper is for information purposes only and is subject to change. Rublix does not guarantee the accuracy of or the conclusions reached in this white paper, and this whitepaper is provided as is. Rublix does not make and expressly disclaims all representations and warranties, express, implied, statutory or otherwise, whatsoever, including, but not limited to: 

1. Warranties of merchantability, fitness for a particular purpose, suitability, usage, title or non-infringement.
2. The contents of this whitepaper are free from error or misinformation.
3. That such contents will not infringe third-party rights.
 
Rublix and its affiliates shall carry no liability for damages of any kind arising out of the use, reference to, or reliance on this white paper or any of the content contained herein, even if advised of the possibility of such damages. In no event will Rublix or its affiliates be liable to any person or entity for any damages, losses, liabilities, costs or expenses of any kind, whether direct or indirect, consequential, compensatory, incidental, actual, exemplary, punitive or special for the use of, reference to, or reliance on this whitepaper or any of the content contained herein, including, without limitation, any loss of business, revenues, profits, data, use, goodwill or other intangible losses.

Copyright (c) 2018 Rublix Without permission, anyone may use, reproduce or distribute any material in this whitepaper for non-commercial and educational use (i.e., other than for a fee or for commercial purposes) provided that the original source and the applicable copyright notice are cited and proper credit is given.
