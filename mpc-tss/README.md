# Multi-Party Computation (MPC) & Threshold Signature Scheme (TSS) <!-- omit in toc -->

[back](../README.md)

## Table of Contents <!-- omit in toc -->

- [Introduction](#introduction)
- [Key Concepts](#key-concepts)
- [CGGMP21 Protocol](#cggmp21-protocol)
- [Documentation](#documentation)

## Introduction

Multi-Party Computation (MPC) and Threshold Signature Schemes (TSS) are cryptographic protocols that enable multiple parties to jointly compute signatures without any single party having access to the complete private key. This is crucial for decentralized systems where security and trust distribution are paramount.

In the context of our bridge, these technologies allow validator nodes to collectively sign transactions without compromising security or requiring complete trust in any single validator.

## Key Concepts

- **MPC (Multi-Party Computation)**: A cryptographic technique allowing multiple parties to jointly compute a function over their inputs while keeping those inputs private.
- **TSS (Threshold Signature Scheme)**: A specific application of MPC that enables a group of n parties to collectively generate a signature, requiring t (threshold) parties to cooperate.
- **t-of-n Threshold**: Refers to requiring t participants out of n total participants to collaborate to generate a valid signature.

## CGGMP21 Protocol

The CGGMP21 protocol (Non-Interactive, Proactive, Threshold ECDSA with Identifiable Aborts) is a state-of-the-art implementation that offers several key advantages:

- Non-interactive signing process
- Proactive security features
- Identifiable aborts for accountability
- Efficient ECDSA threshold signatures

[Link to CGGMP21 Paper](https://eprint.iacr.org/2021/060.pdf)

## Documentation

- [Shared Key Management](shared-key-management.md)
- [Comparison of Decentralized Validation and Security Systems](./comparison-of-decentralized-validation-and-security-systems.md)
- [Implementation Guidelines](./implementation.md)
