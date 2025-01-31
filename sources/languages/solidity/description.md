To understand Solidity, it is imperative to comprehend the context in which it
is used. So, the first question to ask is: what is a smart contract?

### Smart Contract<sup>1</sup>

[According to Wikipedia][1], a smart contract is a computer protocol intended to
digitally facilitate, verify, or enforce the negotiation or performance of a
contract. They allow the performance of credible transactions without third-parties.

The contracts used in this sense are the exact same as the regular contracts
you're familiar with. By removing the human factor and voiding the need for a
third-party, people and business are able to save money and reduce the chance of
fraud. Smart contracts are the main driving force of blockchains.

### Blockchain<sup>1</sup>

[According to Wikipedia][2], a blockchain is a continuously growing list of records,
called blocks, which are linked and secured using cryptography. Each block
typically contains a cryptographic hash of the previous block, a timestamp,
and transaction data.

Blockchain is the force driving the technology of all digital currencies.
A couple of examples are Bitcoin, Ripple, Ethereum, Litecoin, Nem just to cite a few.

[Blockgeeks][3] has a great analogy which should help you understand blockchain works:

    Picture a spreadsheet that is duplicated thousands of times across a network
    of computers. Then imagine that this network is designed to regularly update
    this spreadsheet and you have a basic understanding of the blockchain.

Another wonderful description provided by [William Mougayar][4] goes as follows:

    Imagine two entities (eg banks) that need to update their own user account
    balances when there is a request to transfer money from one customer to another.
    They need to spend a tremendous (and costly) amount of time and effort for
    coordination, synchronization, messaging and checking to ensure that each
    transaction happens exactly as it should.

    Typically, the money being transferred is held by the originator until it can be
    confirmed that it was received by the recipient. With the blockchain, a single
    ledger of transaction entries that both parties have access to can simplify the
    coordination and validation efforts because there is always a single version of
    records, not two disparate databases.

Welcome to solidity!
