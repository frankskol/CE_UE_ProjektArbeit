This repository contains Francisco Litvay's and Tomislav Dodig's Projectarbeit
# Thema - Distributed Ledgers

## Distributed Ledger Technologies
## Blockchain
### Historical Development
### Properties
## Achieving Decentralized Consensus
### Decentralization in Blockchain
One of the definitions of Blockchain, as seen in (VIRIYASITAVAT & HOONSOPON, 2018), is a “decentralized database with the ability to operate in a decentralized setting without relying on a trusted intermediary”. Thus, decentralization is a core characteristic of blockchain systems. This decentralized nature is based both on confirmation mechanisms as well as the network topology itself. In traditional database systems, a central authority is necessary to guarantee the trustworthiness of transactions. In Blockchains, every node takes part in the transaction creation and validation process.

In Bitcoin, the reference client has four different functions: it serves as a wallet, miner, routing node and contains a copy of the full blockchain, which is the chain of blocks containing transactions. Since every full node of the network has a full copy of the blockchain, invalid transactions can be easily detected. Malicious users trying to use resources they don’t have can be quickly counteracted by looking up the transaction history in the ledger. Invalid transactions are then not added to blocks and don’t become part of the blockchain. In this way, no single authority validates transactions, but the whole network itself. Most blockchains follow this format for their reference client.

In fact, even nodes that do not have a copy of the full blockchain can participate in transaction validation. There are two ways in which this can happen: The first one is by having a light node, which uses another node as the source of the blockchain. In this case, the wallet and the routing node are present, but not the full blockchain and mining components. This implies, however, that the validator must trust the node from which he is receiving data. Another possibility is called node pruning, in which nodes maintain only the most relevant transactions, relying less on full nodes for validation. This requires considerably less disk space. However, both kinds do not eliminate the necessity of maintaining full nodes to keep the blockchain decentralized, since even pruned nodes need to rely on full nodes for transactions they do not possess.  

Moreover, transaction creation also occurs in a decentralized manner.  As explained in (LI ET AL., 2017),  to guarantee the reliability and consistency of the data and transactions, blockchains use decentralized consensus mechanisms. Although different mechanisms exist, the three main examples are PoW, PoS and DPoS. 


### Security issues of Centralization
Regarding transaction validation, centralization in a blockchain increases the less full nodes there are for validation. Specifically, Full nodes, since they are the ones that other nodes can rely upon to validate transactions. Pruned or light nodes do not have an entire copy of the blockchain, and thus have to rely on full nodes to validate all possible transactions. The less full nodes there are in a blockchain system, the more users must trust specific nodes. Reducing the situation to an extreme case, if there is only one full node, the whole network depends wholly on this third person to validate their transactions, returning blockchain systems to the same situation as before their invention. In such situation of fewer full nodes, the easier it is for a node to provide an altered version of the blockchain. However, with more nodes, such alterations can be easily detected by comparing data from one node with the rest of the network. In a blockchain with many full nodes, a user must not trust any individual node, only the network itself. The functioning of validation is independent from the blockchains consensus mechanisms, in most cases. The use of PoW, PoS or DPoS does not alter this situation.

One factor that increases the difficulty of maintaining a full node is increased blockchain size. As time passes, blocks are added to the blockchain, increasing the required disk space. The importance of this factor is related to the system’s block size. A blockchain whose blocks occupy 8MB will require 8x more disk space than a blockchain whose blocks occupy 1MB at the same block height. Nevertheless, a bigger block size also allows blocks to store more transactions, so there is a trade-off between throughput and required disk space in blockchains. Pruned nodes can be used to contribute to validation without requiring ever increasing disk space, but full nodes are still required to maintain the network.

Another source of centralization in Blockchains is in transaction creation. As noted in (Chen, Xu, Gao, Lu, & Shi, 2018), such centralization poses security risks to the whole system. If a user or group of users can achieve 51% of dominance in the network’s consensus mechanism, be it through votes in staking or computational power in Proof of Work, they have the possibility of removing or reordering transactions in the blockchain.

This is because, as elucidated by (CONTE DE LEON, STALICK, JILLEPALLI, HANEY, & SHELDON, 2017), despite being sometimes incorrectly described in this manner, blocks are not immutable in blockchain systems. It is possible to revert blocks by redoing the work necessary for its creation, for example. A security feature of blockchain systems is that such deletion of blocks in the blockchain in reality has to be done before a new block arrives. This is because nodes will choose chains based on their total work (in Proof of Work Systems). To alter a chain, one needs to generate a chain with more hash power than concurrent ones. However, as time passes, more hashing power is invested in the original chain. This makes it increasingly difficult to alter older blocks. 

However, as explained in (KANO & NAKAJIMA, 2018) ,  having 51% control of the network creates the possibility of double spending by block alteration. Imagine a chain A, in which user i sends 1 bitcoin to user j. After j has confirmed payment receipt when the block has been confirmed, the 51% unites to create a chain B in which user i used the same funds to pay for something else. Since chain B will have more hashing power, it will be recognized and accepted by the nodes, effectively letting user i spend his money two times, although in the blockchain registry it has only been spent once. Nevertheless, as previously described, the older a block is, the safer it is from alteration by a 51% attack.

Similar problems arise in Stake systems. Consider transactions x and y. Both spend the same funds, but transaction x was broadcasted first. Although theoretically x is the transaction that should be included in the block, the 51% can vote for transaction y’s confirmation, altering the ideal functioning of the system.

Another issue of centralization is that the 51% can choose to deny the inclusion of specific transactions in blocks. This is because transactions not yet included in a block stay in a transaction pool. Miners or block validators then choose which transactions will be included in the next block. By controlling block creation, a “denial of service” can be put into force by targeting users and stopping them of spending their funds, leaving their transactions indefinitely in the transaction pool. 

A further danger that centralization poses to blockchain networks is the possibility of changes in the network itself. By possessing the majority of consent power in a network, 51% attackers could change consensus rules in the system, potentially altering features making the system even more vulnerable to such a 51% dominance.

As shown in (LI ET AL., 2017), these security issues are specially a problem in small networks. Blockchains that already possess a high number of users demand a considerably higher cost of attack than a newly born networks, since the hash rate is still low and the blockchain is still undergoing valuation. Also, new networks have a lower number of full nodes, which again raises the issue of having to trust specific nodes.

### Proof of Work
Proof of Work functions by utilizing computationally hard but easily verifiable one-way puzzles. To create a block that will be added to the network, a miner must solve this computational puzzle. The first one to solve the puzzle broadcasts his solution to other nodes. Other nodes seeing the solution can easily verify that the solution solves the puzzle, but to calculate the solution would require going through all the work that the successful miner had to undergo. The miner thus achieves network consensus and receives a bitcoin reward for his solution. This reward comes from the coinbase transaction in the beginning of each block and from the transaction fees included in the transactions that users created. Users include transaction fees in their transactions to give an incentive for miners to include their transaction before other transactions in the mined block. Since every full node can mine, this is a decentralized solution.

With the increased economic interest in blockchains, more interested people set up nodes, but this also caused a centralization tendency, especially in the mining industry. The difficulty of the puzzle in Proof of Work systems is based on the network’s hash rate to produce blocks evenly according to the established block time, the interval of the inclusion of blocks in the blockchain. This means that the block difficulty will adjust itself to the network’s hash power to have a stable block time. In Bitcoin, for example, this block time is of 10 minutes.

However, increased economic interest has dramatically raised the number of miners looking for profit. Due to the increased network competitiveness and puzzle difficulty, it is impractical for individuals to mine, since the chances of achieving the solution to create a block diminishes. This led to the creation of mining pools, in which many miners aggregate their hash rate for joint mining. This, as shown by (BEIKVERDI & SONG, 2015), does not decrease the amount of rewards that the miners will receive, since the hash rate is aggregated, but considerably lowers the reward variance. Thus, instead of once in a few months receiving a large quantity of bitcoins for one block, miners in pools get to receive small amounts regularly, giving them more stability and income predictability. Nevertheless, this practice is not without disadvantages. By concentrating the hash power of many miners, mining pools make it considerably easier for a group to reach the necessary 51% hash rate for performing a successful attack.

Another hindrance present in Bitcoin and other blockchains that use similar functions for mining, is that simple computers are not able to compete with Application Specific Integrated Circuits (or ASICs) made specifically for solving the computational problems necessary for mining. Such ASICs can only solve the required problem, but drastically outperforms regular computers in its function. This makes it almost impossible for normal users without specialized hardware to participate in the mining process, since the network difficulty adjusts to the higher network hash rate caused by the introduction of ASICs. The implication of this situation is the further centralization of the mining power in the hands of users that already have a higher mining power. One proposed solution to this problem is the use of different functions in the mining process that are ASIC resistant, rendering the use of such hardware inefficient and returning the mining power to the hands of normal computers, allowing them broader participation in the mining process.

Further proposals were made for solving the centralization problem in Proof of Work systems. One worth mentioning is the proposal made by (KANO & NAKAJIMA, 2017), that confronts the anti-ASIC approach. In this model, a psychological incentive is added on top of the economic incentive through a gamification of the mining process. Such system requires elevated computational power, which means that in this model increased use of ASICs could actually help counter centralization.

### Proof of Stake
Proof of Stake utilizes the proof of ownership of the cryptocurrency to provide data credibility. During block creation, users must pay a certain amount of cryptocurrency. If the block or transaction can be confirmed, the cryptocurrency will be returned to the original node, else it will be fined. In blockchain systems due to use of asymmetric cryptography, proving ownership of a quantity of funds is simple. The user must only unlock the respective UTXOs, Unspent Transaction Outputs. These outputs are funds of the blockchain’s asset which are locked with the user’s public key and can only be spent by the user which possesses the respective private key. The selection of who will be the next block creator is different across implementations. Examples include randomizing functions or giving increasing importance to aging stakes.  When disputes regarding transactions arise, nodes vote with their staked cryptocurrency to decide which transaction is valid. In this mechanism, every node that possesses a balance higher than 0 of the blockchain’s asset can participate in the process, making it a decentralized solution.

Proof of Stake systems have a different condition necessary for a 51% attack. Instead of controlling 51% of hashrate, attackers in a Proof of Stake blockchain need 51% of the staked amount of the blockchain’s cryptocurrency/asset to realize such an attack. The indicated approach to is already a method of countering security issues that centralization raises on PoW systems by adding an economic incentive not to tamper with the network. In PoW blockchains, if an attacker desires to attack a blockchain, he needs 51% of hashing power. Such hashing power comes from hardware. The implication of this is that attackers can fraud a network and still maintain the economic value of their hardware. After an attack, the hardware can be used for other purposes or be sold.

On the other hand, since 51% attacks on PoS systems require possession of the blockchain’s asset itself, attacks on the network can only be made at personal expense. Frauding a network drastically lowers users trust in it, decreasing its value. After the successful execution of a 51% attack in a PoS network, the monetary value of the stake used for executing the fraud plummets, as few users want to participate in a frauded network. Such approach to 51% attacks means that even if a potential attacker achieves 51% of the stake in a PoS system, he still has an economic incentive to keep the blockchain intact and secured.

However, pure PoS systems have their downside. The 51% necessary for such an attack is not the total amount of the cryptocurrency, but of the staked amount. This means that offline nodes that possess an amount of the cryptocurrency will not have a say in the consensus, since their funds are not staked. The implications of this is that actual attacks can be executed with less than 51% of the network’s assets when not all funds are staked. The less of network’s assets are required for executing the attack, the less the monetary loss of the attacker is, facilitating an attack.

The early network problem posed by (CHEN ET AL., 2018) in Proof of Work blockchains also occurs in PoS ones, but in a different fashion. While PoW early blockchains have a low hash rate, in PoS early blockchains have low monetary value. This makes it easy for potential attackers to amass enormous quantities of funds in a blockchain’s initial phase, making the cost of a centralization attack considerably lower than in a more established and valued PoS Blockchain.

### Delegated Proof of Stake
Delegated Proof of Stake works in a similar way to Proof of Stake. As simply described by (ZHENG ET AL., 2017), “The major difference between PoS and DPOS is that PoS is direct democratic while DPOS is representative democratic”. In Delegated Proof of Stake, nodes can stake their assets, but also delegate their staking power to representative nodes that will vote for them with their stake in the consensus process. Just as in Proof of Stake, only nodes that possess the cryptocurrency participate in the consensus process, making it a decentralized solution for consensus.

DPoS blockchains, as explained previously, work similarly to pure Proof of Stake systems. Since 51% attacks also require staking, DPoS blockchains also entail a monetary incentive for users to safeguard the network, working identically to PoS in that regard.
The difference comes with the possibility of stake delegation. By delegating a stake to a trusted representative, users possessing funds need not stay online to have their assets staked and participating in the consensus system. This considerably alleviates the problem present in PoS, in which attacks are made easier because large quantities of assets are not staked. In many DPoS systems, prechosen representatives are present, meaning users must opt-out of standard representatives if they so desire. This makes sure that the entirety of the blockchain’s assets will be staked.

The delegation mechanism thus ensures that most assets will participate in the consensus mechanism, rendering attacks with less than 51% of the network improbable. It is of note however that in such blockchains there can be centralization in representatives themselves in case they are delegated larger quantities to stake. Users fearing misuse of their stakes ought to change representatives to avoid such issues.

## References:
Beikverdi, A., & Song, J. (2015). Trend of centralization in Bitcoin’s distributed network. In Software Engineering, Artificial Intelligence, Networking and Parallel/Distributed Computing (SNPD), 2015 16th IEEE/ACIS International Conference on (pp. 1–6). IEEE.

Chen, L., Xu, L., Gao, Z., Lu, Y., & Shi, W. (2018). Protecting Early Stage Proof-of-Work Based Public Blockchain. In 2018 48th Annual IEEE/IFIP International Conference on Dependable Systems and Networks Workshops (DSN-W) (pp. 122–127). IEEE.

Conte de Leon, D., Stalick, A. Q., Jillepalli, A. A., Haney, M. A., & Sheldon, F. T. (2017). Blockchain: properties and misconceptions. Asia Pacific Journal of Innovation and Entrepreneurship, 11(3), 286–300.

Kano, Y., & Nakajima, T. (2017). A New Approach to Mining Work in Blockchain Technologies. In Proceedings of the 15th International Conference on Advances in Mobile Computing & Multimedia (pp. 107–114). ACM.

Kano, Y., & Nakajima, T. (2018). A novel approach to solve a mining work centralization problem in blockchain technologies. International Journal of Pervasive Computing and Communications, 14(1), 15–32.

Li, X., Jiang, P., Chen, T., Luo, X., & Wen, Q. (2017). A survey on the security of blockchain systems. Future Generation Computer Systems.

Nakamoto, S. (2008). Bitcoin: A peer-to-peer electronic cash system.

Viriyasitavat, W., & Hoonsopon, D. (2018). Blockchain characteristics and consensus in modern business processes. Journal of Industrial Information Integration.

Zheng, Z., Xie, S., Dai, H., Chen, X., & Wang, H. (2017). An overview of blockchain technology: Architecture, consensus, and future trends. In Big Data (BigData Congress), 2017 IEEE International Congress on (pp. 557–564). IEEE.


