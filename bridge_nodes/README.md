# Description of the Node Network within the Decentralized Bridge <!-- omit in toc -->

[back](../README.md)

## Overview <!-- omit in toc -->

## Table of Contents <!-- omit in toc -->

- [1. Relayer Nodes](#1-relayer-nodes)
  - [Relayer Node Network (Centralized)](#relayer-node-network-centralized)
- [2. Validator Nodes](#2-validator-nodes)
  - [Validator Node Network](#validator-node-network)
  - [Node Registration](#node-registration)
- [3. Functions to Implement](#3-functions-to-implement)
  - [Utility](#utility)
  - [Relayer Node](#relayer-node)
  - [Validator Node](#validator-node)

## 1. Relayer Nodes

### Relayer Node Network (Centralized)

- The network is centralized
- Relayer nodes are under `chaincraft`'s responsibility
- Relayer nodes ensure interaction with contracts on blockchains
- Relayer nodes communicate with validator nodes
- Relayer nodes must be fault-tolerant and provide permanent service
- Relayer nodes register validator nodes

## 2. Validator Nodes

### Validator Node Network

- The network is decentralized
- The network is limited to `n` nodes where `n` equals `20`
- All nodes communicate together via the `gossipsub` protocol
- Nodes listen to events emitted on the blockchain

### Node Registration

- The authority is a contract on the blockchain
- Nodes are registered with an authority
  - With a unique ID (peer ID)
  - With an IP address
- `chaincraft` is responsible for maintaining this list of validator nodes (addition/removal)

> The validator node must communicate with an RPC node

## 3. Functions to Implement

### Utility

- [x] Generate a peer ID based on a seed

### Relayer Node

- [x] Start a relayer node
- [ ] Relayer node cluster
- [ ] Add/Remove a validator node by peer ID on the blockchain
- [ ] Generate shared keys for MPC/TSS
- [ ] Distribute shared keys for MPC/TSS to validator nodes
- [ ] Execute bridge transactions on the blockchain

### Validator Node

- [x] Start a node using protocols [kademlia, QUIC, Gossipsub]
  - [x] Initialize p2p network with a bootstrap node
  - [x] Start nodes by connecting to bootstrap
  - [x] All network nodes discover each other [kademlia]
  - [x] All network nodes communicate [gossipsub]
  - [x] Network remains stable after bootstrap disconnection
  - [x] Reintegrate bootstrap into p2p network after disconnection
- [x] Relayer node communicates with a designated validator (request/response)
- [ ] Connect validator node to relayer node
- [ ] Listen to events from the blockchain
- [ ] Validate transactions via MPC/TSS
- [ ] Sign transactions via MPC/TSS
- [ ] Send transactions via MPC/TSS to other validator nodes
