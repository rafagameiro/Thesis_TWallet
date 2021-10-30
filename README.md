# TWallet - ARM TrustZone Enabled Trustable Mobile Wallet: A Case for Cryptocurrency Wallets

The purpose of this repository is to provide a simple explanation of the work done during my MSc thesis [[1]](#references). With that in mind, this repository also contains a set of sublinks that point to the different components that were essential throughout this project development.


## Abstract

With the increasing popularity of Blockchains, and their support for virtual cryptocurrencies and related blockchains, it has become more important to have highly secure devices running trustable cryptocurrency wallets, in which users can store sensitive information and trust management mechanisms to manage trusted storage, and to support secure processing of client-side transactions under sound trustability assumptions. 

ARM TrustZone technology has made available an extension of ARM architectures, which allows for the isolation of trusted and non-trusted environments, and related software services. This allows that critical components are booted and running backed in isolation, using the ARM-Hardware level as its minimal trust computing base. ARM TrustZone provides the enforcement of security and privacy conditions for applications, ensuring privacy and containment of sensitive components against possible OS-level intrusion attacks. 

In this dissertation the goal is to propose a solution for a generic model, for secure and trustable Mobile Client Wallets backed by the ARM TrustZone technology as a secure, flexible and reliable way for clients to manage transactions. We believe that our approach can be used as a framework model that can be applied to a variety of applications that can benefit from the proposed solution. As a proof of concept we will use our TWallet framework model to implement a trusted wallet application, targeting an Ethereum wallet as a candidate application.

## Architecture

The following figure describes the architecutre of our solution

![architecture figure](figures/twallet_architecture.PNG?raw=true)

Our solution is built on different components splitted in two main parts:

- The Secure World Part that contains a set of small components, which are the basis for the TWallet System:
    - The TEE Adaptation and Isolation layer is responsible for intercepting the requests done to the secure components, and perform some validations and sub operations before and after redirecting them into the specific components.
    - The Logging Services generates a log of the operations executed in the different secure components.
    - The Monitoring Service is responsible for the monitoring and filtering of operations requested to the other secure components.
    - The Secure Storage is responsible for the storage of data regarding the logged wallet account.
    - The Authentication Service provides a storage for sets of credentials, needed for wallet sign in.
    - The Attestation Service, based on TPM Attestion Process [[2]](#references), must provide and integrity hash check regarding our secure components. 
- The Normal World Part correspondes to the TWallet Framework, which is the service responsible for enabling communication between the applications that run on the Normal World side, and all secure components located in the Secure World.
- Not shown in this figure, we also developed a benchmark to properly evaluate an measure the performance of specific operations performed by the TWallet System

## Link to Components

To properly analyse and if possible experiment my developed solution and proptotype, the following repositories contain the segments of my thesis.

- TWallet System - link TBD
- TWallet Developed Prototypes - link TBD
- TWallet Benchmark - link TBD
- TWallet Thesis Report - link TBD

## Pre-requisites

In order to properly observe or evaluate the TWallet system, must meet this requirements:

- It is highly recommended to have an Hikey960 Board [[3]](#references), as this was the board used during the entire design, implementation, and evaluation of the solution
- The System setup inside the Hikey board must be an AOSP + OP-TEE configuration [[4]](#references). The steps for its installation can be found in OP-TEE Official Documentation and my MSc Thesis Report Annex "_Hikey960 AOSP+OP-TEE Setup_"

## References

1. R. Gameiro. _TWallet - ARM TrustZone Enabled Trustable Mobile Wallet: A Case for Cryptocurrency Wallets_. Nova University of Lisbon. 2021.
2. H. Raj et al. "fTPM: A Software-Only Implementation of a TPM Chip". In:USENIXSecurity Symposium. 2016 
3. 96Boards.HiKey960. 2021. url:https://www.96boards.org/product/hikey960/
4. Linaro. AOSP in OP-TEE: Open Portable Trusted Execution Environment. 2021. url:https://optee.readthedocs.io/en/latest/building/aosp/aosp.html