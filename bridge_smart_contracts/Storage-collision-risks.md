# Risk Management of Hash Collisions in Storage

## Introduction

In our current storage management approach, there is a risk of hash collisions. We utilize hashing in two places: for 'operation hash' and for entries in the storage mappings.

While the use of `keccak256` is said to be collision-resistant, in reality, collisions are highly improbable but still possible. When it comes to `operationHash`, the impact is minimal. If an attempt is made to create an operation that already exists, it will revert. Even in the unlikely event of a collision, it would only be beneficial to an attacker if they could use it to impersonate a user (e.g., unlocking funds through the bridge) with specific constraints on tokens, existing amounts, and a destination address corresponding to the attacker. Therefore, we consider this scenario to be negligible.

However, regarding the storage, which utilizes composite keys, even if we cast the inputs to have identical types, we are not immune to future usage where a set of two input keys before hashing could be equal to an existing entry, resulting in the same hash and thus creating a collision. The storage contract contains all configuration information, valid contract addresses, and more. A collision at this level could lead to unexpected and unpredictable behavior in the system. This could occur either by accidentally overwriting the address of one of the used contracts or by overwriting the data of a token, potentially leading to an involuntary loss of protocol functionality, which could be devastating.

## Storage Contract Overview

This storage contract contains the generic setters and getters for the bridge's configuration mappings. The risk primarily lies with the setters. Modifying the getters would significantly increase gas consumption, as they are often called. Moreover, only an admin role is authorized to add or modify data in this storage.

We are currently considering actions on the setters to prevent existing data from being overwritten in the event of a key collision when adding new data with a corresponding hash. The proposed solution is to split the setters into two categories: 'init' and 'update'.

### Proposed Solution

- **Init Functions**: These functions would be used to add new data. They would revert if the key already contains data (i.e., a value different from the default).
- **Update Functions**: These would serve to modify existing data and revert if there is currently nothing present.

The developer or admin adding the data would then be aware of the collision risk and could modify one of the inputs (e.g., since there is always a string label or a `bytes32`, we recommend altering this input by adding an underscore or an increment).

To better manage inputs, we propose having arrays of valid labels (mapping input keys) within the storage. These getters would not be used in contracts (due to the cost associated with searching through arrays) but could be utilized from the front end or back end to check available keys and verify the syntax of a label if it has already been modified.
