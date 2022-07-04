# Setting up your Development Environment for Local Subnet Development

## Introduction

Avalanche is an open-source platform for launching decentralized applications and enterprise blockchain deployments in one interoperable, highly scalable ecosystem. Avalanche is the first decentralized smart contracts platform built for the scale of global finance, with near-instant transaction finality. Avalanche is a blockchain that promises to combine scaling capabilities and quick confirmation times through its Avalanche Consensus Protocol. It can process 4,500 TPS (transactions per second). For Ethereum, that number is 14 TPS.

![avax](/images/1.jpeg "avax")

Blockchains have traditionally been referred to as being slow and unscalable. Avalanche embraces an innovative approach to concensus that solve these problems without compromising on security.

Avalanche is a high-performance, scalable, customizable, and secure blockchain platform. It targets three 15 broad use cases:

* Building application-specific blockchains, spanning permissioned (private) and permissionless (public)
deployments.
* Building and launching highly scalable and decentralized applications (Dapps).
* Building arbitrarily complex digital assets with custom rules, covenants, and riders (smart assets).

# Avalanche features 3 built-in blockchains: 
* Exchange Chain (X-Chain)
* Platform Chain (P-Chain)
* Contract Chain (C-Chain)

The P-chain is for platform management. It handles requests related to the validator, the subnet, and the blockchain. 
The C-chain is for contract management. It is based on EVM; hence its API is almost identical to other EVM protocols. It has both RPC and WebSocket endpoints, and it handles requests for smart contracts. 
The X-chain is for asset exchange. It is Avalanche’s native platform; it is used for creating and trading assets like AVAX and NFTs. 

These 3 blockchains are secured by the Avalanche Primary Network with is a special kind of subnet.

The Avalanche Architecture is composed of:
* Subnetworks
* Virtual Machines
