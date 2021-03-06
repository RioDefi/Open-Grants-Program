# Open Grant Proposal

> This document is referenced in the terms and conditions and therefore needs to contain all the required information. Don't remove any of the mandatory parts presented in bold letters or as headlines! See the [Open Grants Program Process](https://github.com/w3f/Open-Grants-Program/blob/master/README_2.md) on how to submit a proposal.

> This page is also available in [Chinese (中文)](./application-template-cn.md).

* **Project Name:** substrate-bip32
* **Team Name:** RioDeFi
* **Payment Address:** B3G7UcwR5nVQZSDNDTRKELxeZ7zbMpAmwEe

*The above combination of your GitHub account submitting the application and payment address will be your unique identifier during the program. Please keep them safe.*

## Project Overview :page_facing_up: 
If this application in response to an RFP then please indicate this on the first line of this section.

### Overview

The purpose of this project is trying to implement HD Wallet with rust for substrate. The wallet should support multiple secp256k1 based crypto currencies and particularly Ed25519 or SR25519. This wallet will allow anyone to generate Polkadot address in a format official hd wallet path like P//hard//soft (where P is mnemonic)

A standard setup for a wallet user is to provide a single seed(mnemonic) and uses the functions provide by this project to derive a tree of key pairs.

The master private/public pair is derived by gen_master_keys_from_seed and a parent level private_key can be used to derive next level public/private keys while parent public_key can only be used to derive next level public keys.

Wallet users can generate public/private keys by specifying a wallet path like P//hard//soft and each account of the wallet is bind to menemonic P. To ease the integration effort between wallet and other substrate applications, we will implemented it in rust with no-std config so that it can potentially run in a wasm environment (browser for example).

### Ecosystem Fit 
No similar project

## Team :busts_in_silhouette:

### Team members
* Sen Ni
* David Ding, Binker Cao, Yan Shen	

### Contact
* **Contact Name:** Sen Ni
* **Contact Email:** phyrex@riodefi.com

### Legal Structure 
* **Registered Address:** Unit Level 9F(2), Main Office Tower, Financial Park Labuan, Jalan Merdeka, 87000 Federal Territory of Labuan, Malaysia
* **Registered Legal Entity:** RIODEFI INC.

### Team's experience
The team has been deeply involved in the blockchain field for many years and has rich research on Polkadot. The project is led by Phyrex (Sen Ni) and consists of a wallet developer, a blockchain developer and a security engineer.  

### Team LinkedIn Profiles
* https://www.linkedin.com/in/%E6%A3%AE-%E5%80%AA-626b8275/

## Development Roadmap :nut_and_bolt: 
 
1. Develop a standard BIP32 key generator from scrach.
   The newly implemented BIP32 library should be written in rust and can compile with no_std library. The reason of doing this is that we would like to compile int into wasm code so that it can also run as a web application. We start the library using secp256k1 so that we can test is using exsiting bip32 test suite.

2. Test it in a web environment.
   Once wasm-pack was installed via the following,
   `curl https://rustwasm.github.io/wasm-pack/installer/init.sh -sSf | sh`

   We should be able to test the code using the following script:
   `wasm-pack test --chrome`

3. Replace the secp256k1 with sr25519. This requires us to integrate substrate's sr25519 package with this BIP32 style wallet. From this point, this package will no longer generate Bitcoin keys but substrate keys. (This mile-stone has not been achieved yet). After this stage we can deliver the cli command.

4. Providing an web user interface so that any substrate-ui can integrate our wallet in their web interface.



### Overview
* **Total Estimated Duration:** 1 months
* **Full-time equivalent (FTE):**  3 FTE
* **Total Costs:** 0.5 BTC

### Milestone 1
* **Estimated Duration:** 1 month
* **FTE:**  3
* **Costs:** 23000 USD

| Number | Deliverable | Specification |
| ------------- | ------------- | ------------- |
| 0a. | License | Unlicense |
| 0b. | Documentation | We will provide full inline documentation of the code. |
| 0c. | Testing Guide | The code will have unit-test coverage to ensure functionality and robustness. All test vectors from bip32 specification will be implemented. In the guide we will describe how to run these tests. | 
| 0d. | Article/Tutorial | We will write an article or tutorial that explains the work done as part of the grant. 
| 1. | Rust library: bip32 | We will create a Rust library implementing bip32 specification |  

