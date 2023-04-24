# Smart-Contract Best Practices

### Author - Charlie Benson, Senior Blockchain Engineer

### *This repository is dedicated to documenting a brief overview of 'Best Practice' when it comes to writing and auditing Smart Contracts on the Ethereum Virtual Machine (EVM).*




# Mindset

## Easy to Fail
As the adoption of this technology increases, the value we store between these lines of code does too. 
The Ethereum Blockchain and other EVM's are public, permitting access to all of your SC functions and data. If not written with care, this can lead to easy access exploitability.


Depending on your SC, the logic may be non-trivial, and should therefore be approached with the expectation of erros. So the SC must be written to enable it to respond to bugs and errors with ease:
- Pausability.
- Rate limiting (maximum address usuage).
- Upgradeability (in the event of outdated logic).

## Test Before Launch
*Deployed Smart Contracts are IMMUTABLE.* 

- Test the contracts thouroughly with tools like Hardhat, Foundry, Chai, Slither, Mythos, Solhint, Securify etc.

- Have SC code reviewed and auditted by the likes of Certik, Hacken, Consensys Dilligence etc.

- Provide incentives through Bug Bounties on sites such as Hacken, Immunefi etc.

- Upgradeability allows for a rollout of phases/versions.

## Simplicity Is The Answer

*More Code == More Errors*

- Keep it simple, stupid. Smaller functions, modularised code. Clarity > Performance (This helps with future audits and developer/community code comprehension).

- Utilise open-source, accepted, auditted code libraries and dependencies. Such as Openzeppelin ERC standards, roles and upgradeability contracts.

- Avoid fuctionality that isn't required by decentralisation.

## Don't Think You Know It All

Ethereum and Solidity were only developed in 2015. New exploits, attack vectors, development standards and methods are uncovered and accepted frequently.


- New uncovered attack-vectors, should call for a re-audit of your SC.
- Upgrade to comply with newest tools and standards asap.
- Stay up to date with development norms and news.

## Common Exploits and Attack Vectors

It is easy to accidently create vulnerabilities. Here is an overview of all common exploits and how they work:

[Charlie's Smart Contract Vulnerabilty Dictionary.](https://github.com/CharlieJRBenson/Smart-Contract-Vulnerability-Dictionary)

Here is a repository of how to exploit the common vulnerabilities:

[Charlie's CTF Challenge Documentation.](https://www.github.com/CharlieJRBenson/SmartContractHacking)


## Key Compromises

Smart Contracts generally follow normal software engineering best practices:
- Modularisation.
- Efficiently reused code (functionised, class based).
- Upgradeablity.

However, some considerations must be made with regards to waying up security benefits, performance and comprehensibilty:

### Upgradeable or Fixed

*Upgradeability/Modularity/Modifiability == Complexity*

Remember we said to "Keep It Simple, Stupid". Refer to previous simpilicity arguments.

### Inherited or Self-Contained

Inherited contracts being those that inherit multiple abstract/non-abstract imported smart contracts.
Self-contained contracts being those that contain all the logic and data within one smart contract.

The latter improves comprehensibilty and security review. The former is useful when importing complex yet trusted contracts and standards, such as OpenZeppelin ERC's or Role's based logic.

### Reused or Duplicate Code Blocks

Maximise the use of functions and contracts to reuse code blocks without deuplication. Once again, very important for code legibility, security reviews and gas optimization.

# Security Audit Optimal Methodology

### *This section of this document is directed more at the security research and audit aspects of smart contracts, moreso than development.*

### *The following points are inspired by and refined from this Andy Li and Trust interview Dec 2022, linked [here](https://www.youtube.com/watch?v=NC4uzV-syIw&t=4099s&ab_channel=AndyLi).*

- Understand the system, including reading documentation and understanding expected behaviour from a user perspective.

- Examine the code, looking for points where developer assumptions can be falsified and identifying possible changes in state.

- Test and stress the system on these assumptions.

- Stay focused on the task at hand, and minimize distractions.

- But also take breaks to refresh the mind and improve concentration, subconscious problem-solving still happens.

- After identifying any early issues, don't submit a report until the last moment of a contest. Your growing understanding of the codebase could increase these issues to a higher severity rating.

- Make sure your reports communicate issues effectively with the development team, as they will be responsible for implementing any fixes or improvements.

- Focus on building a strong foundation of knowledge and staying up to date on new developments and techniques used to exploit projects.
Eg. Marketplace/Flash-loan/Dex projects will have the same fundamentals as their competition. The more you know and understand, the more you see.

- Ultimately use a systematic and thorough approach, and be prepared to adapt and pivot as needed depending on the project use case.

## Time Efficiency / Bug Hotspots

### *The most under-discussed yet critical concept in bounty hunting and competitive auditing is bug density.*

Every line or chunk of code has some invisible "danger" value, which is the probability of a mistake being injected. As a hunter, time and attention are your only resource constraints. It follows that to maximize success you need to spend those resources on the highest-value sections.* 

So what are the red hotspots on my heatmap?
- fundamentally complex code
- undertested/hard-to-test code
- novel ideas or implementations
- heuristics triggered - gas/delegatecall/callbacks/eth-weth duality etc.

Mastering the bug density heatmap is the single most profitable thing you can do in bounties.
