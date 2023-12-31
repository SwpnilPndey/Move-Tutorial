## What issue does it solve? 

Aptos blockchain uses a new language called Move which is inherently more safer than the more common smart contract language called Solidity 

The idea is simple : the developer should not be held responsible for any vulnerabilities in a smart contract if the issue lie in the language itself 


## The consensus mechanism used in Aptos ? 

Aptos uses Hot Stuff mechanism for its consensus. Its similar to BFT

- Star based communication between nodes, not mesh based. So, the nodes elect a leader and all communications of BFT generals happens to this leader, making the communication network simpler 

- The mechanism doesnot allow same validators to become leaders for two times in a row


## Aptos Block-STM Parallel execution ?

Here we need to understand how unconfirmed transactions stored in the mempool are validated and confirmed in Ethereum, Solana and Aptos 

### In Ethereum, the transactions are executed sequentially. It is slowest process.

### In Solana, the transactions are divided into two groups, dependent or independent. Dependent ones are executed sequentially but independent can be executed paralley, making it faster than Ethereum 

This grouping exercise is known as State Dependency Matrix. if the transactions are dependent on same blockchain states (state variables in simple terms) then they need to be executed sequentially (otherwise double spending may occur)


### Aptos on the other hand, optimistically assumes that all transactions are independents

Based on that, the state version table is maintained such that the transactions are executed parallely. The only difference is that only data is maintained, the transaction is not validated at this step. Now we keep validating each transaction sequentially and check if there is a mismatch between the results of each transaction when it was supposed to be independent and when done sequential. If there is a mismatch, the states are updated accordingly, otherwise the same state is maintained. The optimistic nature of transaction execution saves a lot of time for Aptos blockchain than Solana and Ethereum 


![Execution engine](images/execution%20engine.jpg)


## Move is a resource based language instead of transaction based language (Just like Rust)

So, in EVM, if the NFT ownership changes from A to B, it is stored as a transaction showing the change 

In Move, this is resource based, that is object changes its owner details instead of recording it as a shift from one person to other 


![Resource based language](images/transaction%20versus%20resource.jpg)


## Move has higher access control as the signer is the only entity capable of adding resources into an account


## Move structs cant be duplicated by default, this is called concept of scarcity (limited resources) 


