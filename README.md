# Investigation of Fake_Phishing927630 Scam

I am gathering information about this incident. If you have found this document, your insights may be valuable.
If you are willing to contribute additional information or observations, please contact me through any available means. You may also open an **issue** or submit a **Pull Request**.

## Incident Overview

On **February 28**, an attack was carried out on multiple addresses controlled by the victim. As a result, **USDT and Ether** were withdrawn from the compromised EOAs.

- Both addresses were imported into the **Metamask plugin** in **Google Chrome** and kept there for years. Accounts were derived from the SEPARATE BIP-32 seed phrases stored in different places on the same system. And both were imported into metamask.
- The **Metamask plugin** was used to interact with DEXes and **ENS** recently.
- **Transaction logs do not confirm** that the operations were initiated via the Metamask plugin.
- Backups of private keys were stored as **mnemonic and hex seed** in plaintext on the developer's laptop file system.
- The primary hypothesis is a leak of private keys caused by malware running on the system with user-level privileges. However, neither **Malwarebytes** nor **ClamAV** detected any malicious code on the system.

## Preceding Events

The developer reported the following events prior to the theft:

- Interaction with **ENS DApp** during the preceding week.
- Installation and usage of **new VSCode plugins** previously unfamiliar to the user.
- Installation of **Oh My Zsh** on the system.

Currently, the **laptop’s file system is being scanned** with anti-malware software, but no detections have been reported.

## Connection to Fake_Phishing927630

To obscure the investigation, the attacker executed a transaction with a **synthetic USDT token deployed on a separate contract** immediately after the theft.
The token **contract creator** [0x0C0b9e3A2daefC4731826C5D877eBc0324F72bb9](https://etherscan.io/address/0x0c0b9e3a2daefc4731826c5d877ebc0324f72bb9) is tagged on **Etherscan** as `Fake_Phishing927630` so the incident is related to the mentioned account.


## Transaction Analysis

- The stolen funds were **sent to an EOA address** that appears to be used by the attacker for **fund aggregation** [0x69Cc0a141D89d5a776861e7E03aC15Aa9aBf980b](https://etherscan.io/address/0x69Cc0a141D89d5a776861e7E03aC15Aa9aBf980b).
- To **obfuscate traces**, the attacker **initiated transfers of synthetic ERC-20 token named ETH** to **similar-looking inactive addresses**: [0x69c85A65359C6b283294708bDE7924cea1BF980b](https://etherscan.io/address/0x69c85a65359c6b283294708bde7924cea1bf980b#tokentxns) and [0x69cc63f13a45F5ABB3a0F63a54E664d297b6980b](https://etherscan.io/address/0x69cc63f13a45F5ABB3a0F63a54E664d297b6980b#tokentxns).
- Another involved token with similar behavior is **pseudo-WBTC** is [0xB488eB155D55ad54721E0495d17eF0593b28A845](https://etherscan.io/token/0xb488eb155d55ad54721e0495d17ef0593b28a845) which was Transfer'ed (technically, emitted Transfer events on behalf of the compromised addresses). These tokens are not actual ERC-20 tokens but merely emit events seem designed to mislead victims and investigators.
- The [deployer](https://etherscan.io/tx/0x80409c8a78aafae639f000c51fa8d65bf265550044bae7a727e988ddcbb0bce9) of this mock token [0x669507921B89C11536Fe28FB2b955fbC23Dbe86D](https://etherscan.io/token/0x669507921b89c11536fe28fb2b955fbc23dbe86d) marked by Etherscan as `Fake_Phishing927630`



---

⚠ **This document will be updated as new information becomes available.**
