# Smart-Contract Best Practices

### Author - Charlie Benson, Senior Blockchain Engineer

### *This repository is dedicated to documenting a brief overview of 'Best Practice' when it comes to writing Smart Contracts on the Ethereum Virtual Machine (EVM).*




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

- Provide incentives through Bug Bounties on sites such as Hacken, Immunefi etc

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

[Charlie's Smart Contract Vulnerabilty Dictionary.](https://wwww.github.com/CharlieJRBenson/)

Here is a repository of how to exploit the common vulnerabilities:

[Charlie's Ethernaut Challenge Documentation.](https://www.github.com/CharlieJRBenson/SmartContractHacking)