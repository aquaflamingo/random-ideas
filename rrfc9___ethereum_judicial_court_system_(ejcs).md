# RRFC9 - Ethereum Judicial Court System (EJCS)
At present, Ethereum is the predominate platform for crypto project development. However, Ethereum struggles, as various crypto projects do, with the trouble of malicious actors. Though the platform solves the "hard problems"  consensus and generalized distributed compute, there remains the "soft problems" of semantics and nuances in human interactions. 

Notably, the DAO hack in 2016 was a rather obvious example of human consensus to solve the "soft problem" of a significant portion of the treasury being stolen. This was not based on any particular jurisprudence but rather a community agreement and hard fork. However, in Ethereum "code is law", and therefore contract exploits by clever but arguably morally objectionable actors are continually running up against the problem of "big enough" to warrant intervention by the ecosystem.

In human societies, judicial and court systems exist to settle grievances between parties in an objective and fair way based on shared ethical canon. The [Code of Hammurabi](https://www.worldhistory.org/Code_of_Hammurabi/), for example, states that:

> If a builder builds a house for someone, and does not construct it properly, and the house which he built falls in and kill its owner, then that builder shall be put to death.

From this we see the enforcement of ethical behaviour for the builder to ensure high quality of his construction. In this situation, Hammurabi and his cabinet would be the assumed authority for which this canon would be enforced. However, Ethereum and other similar distributed computation platforms posses no means by which the shared ethical canon of civilization, and primarily internet society, can be arbitrated. Though much has been written on the topics of reputation systems in decentralized compute platforms, little (if any) of it has materialized. After all, there will always be the central feature of these networks which is open access for public key construction. Any an individual can simple create _n_ new "identities" to operate as within these logical worlds, and the reputation dependent components becomes easily gameable especially with financial incentives creating dark market. What's more, there is a real risk implicit in social reputation systems. Quantifying social interaction scores and making them easily indexed, searched and actioned upon could trend towards some undesired consequences.

Rebuttle:

> Yes but that can help us avoid bad actors

Certainly, however, one must be humble enough to see that while the majority social consensus, a la democratic politics, is a utility in allocating shared values into the structure of decision making, civilization has an _equal_ necessity to support heterodox thinking (or loses it at its own peril). Heterdoxy can be, after all, an extremely valuable catalyst of novelty and invention. If quantifiable reputation scores were freely available there could be a positive uptick in existential risk, should the broad social consensus overfit the present environment which it always does. See: Over-fitting, Darwinism.   

Given that "code is law" within Ethereum, it is intriguing to wonder if it were possible to construct some type of smart contract system to act as a "self governing body" within Ethereum. A programmatic "Judicial System" for Ethereum, if you will. Such a system of smart contracts could arbitrate disputes between counterparties within Ethereum by receiving formal complaints and escalations. With a central system in place, other smart contract software systems could integrate with it. Familiarity with the ERC-20 and ERC-721 standards is helpful to see how this could be operationalized. 

Recall that the standard API interfaces for ERC-20 and ERC-721 open the roads to smart contract "composability" within Ethereum. Put a different way, such standardizations have created global inter-contract form factors allowing for higher order abstractions to take place. 

Creating a shared standard is one way in which the Ethereum ecosystem could enforce ethical canon. One could imagine a new standard interface that is mixable into new smart contract programs to provide freezing functionality to balances of a given address based on the authority of a court system:

```solidity 

interface ISubjectToEthereumJudicialCourtSystem {
  modifier onlyEthereumCourt { 
     require(msg.sender == ethereumJudicialSystemContractAddress); _; 
  }
  
  
  onlyEthereumCourt freezeAccount(address256 account)
  onlyEthereumCourt unfreezeAccount(address256 account)
  
}
```

In the above case, if there was a complaint filed with the Ethereum Judicial Court System (EJCS) against an actor (a/k/a an address) within the ecosystem, the EJCS could broadcast an event to the blockchain which all ERC-20 programs could be listening for. Upon receipt of a complaint, that actor's balances within the contracts could be frozen until the complaint is addressed. Simple in principe, the mechanics and game theory of freezing would require a great deal of consideration if only from a technical perspective. In specific, the operationalization of *how* an EJCS could itself be governed and run presents various challenges and options.

## Operationalism for EJCS

### Prediction Markets
One could imagine that certain prediction markets could evolve within the ecosystem so as to provide speculators a means to anticipate the outcome of a particular judicial case. This could in way provide a sandbox implementation of [Futarchy](https://en.wikipedia.org/wiki/Futarchy): a theoretical governance system under which prediction markets are used to influence policy decisions. 

### Governance Tokens
It could be very important that the design of EJCS would explicitly _not_ have a governance token. This is in part because the EJCS would primarily an economic public good: enforcement of contract law on-chain. 

The accessibility of the system should be available to any participant within the Ethereum ecosystem rather than a particular "EJCS Token" holder thus creating clear struggles of incentive alignments. Technically speaking, it's unclear at this time how such a system could be governed *without* a token. 

The contract system would need some type of representation of "voting rights" wherein systems could vote for particular proposals of new policies and laws. Interestingly, such a requirement could actually provide a novel use case for an ERC-721 tokens. As in, perhaps the state of the Ethereum blockchain could be snapshot of balance holding addresses before main net deploy, and each address could be allocated a unique "Voting Right" ERC-721 token. Ideally, you would simply give a token to every possible derivable Ethereum address, but there is clear abuse opportunity in that path.

### Node Based Implementations
The mechanics and implementation of the EJCS could be fairly complex, and in itself, it is a curious question as to how the EJCS would relate to the native protocol level "law". That is: the Ethereum protocol is enforced by the protocol specification and node implementations (i.e. `geth`, `parity`) that interact over P2P connections, whereas EJCS would only be enforced by the mutual consensus of native Ethereum programmers to use the system. In other words, the "human" elements. It is not difficult to imagine, for example, that there would be an apparent "security feature" to such operators who wished to integrate with EJCS. They could market to their users that their protocol was compatible with a mutual ethical framework to deter malicious behaviour. This leaves one to wonder if, for example, this could provide an opportunity for real world insurance entities to begin insuring certain projects given the ability to potentially enforce contracts. But that is all, very far reaching speculation. 

## Other Considerations for an EJCS
The EJCS protocol considerations would need to be thought through with more detail. For example, what tasks would be handled by the system? 
- Official Complaints
- Freezing Accounts of Malicious Actors
- Codification of Legal Proposals
- Self Governing 
- How would actors in these networks represent themselves?

