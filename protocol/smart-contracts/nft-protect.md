---
description: >-
  This smart contract implements security measures for Non-Fungible Tokens
  (NFTs). It provides mechanisms for owners to restore ownership if access to a
  protected token is lost or stolen,
---

# NFT Protect

{% hint style="info" %}
The contract code can be found [here](https://github.com/nftprotect/nftprotect-contracts/blob/main/contracts/nftprotect.sol).
{% endhint %}

### Variables

* `requestsCounter`: Tracks the total number of ownership requests.
* `requests`: Mapping of request numbers to `Request` struct instances.
* `disputeToRequest`: Mapping of dispute IDs to request numbers.
* `tokenToRequest`: Mapping of token IDs to request numbers.
* `metaEvidences`: Mapping of `MetaEvidenceType` to evidence strings.
* `metaEvidenceLoader`: Address allowed to submit meta evidence.
* `burnOnAction`: Boolean flag determining if tokens should be burned upon action.
* `arbitratorRegistry`: Instance of an `IArbitratorRegistry` contract.
* `userRegistry`: Instance of an `IUserRegistry` contract.

### Modifiers

* `onlyOwner`: Ensures that the caller is the owner of the contract.

### Events

* `OwnershipRestoreAsked`: Emitted when an ownership restoration request is made.
* `OwnershipAdjustmentAnswered`: Emitted when an ownership adjustment request is answered.
* `OwnershipRestoreAnswered`: Emitted when an ownership restoration request is answered.
* `BurnAnswered`: Emitted when a burn request is answered.

### Functions

#### askOwnershipRestoreArbitrate

{% code overflow="wrap" fullWidth="true" %}
```solidity
askOwnershipRestoreArbitrate(uint256 tokenId, address dst, uint256 arbitratorId, MetaEvidenceType metaEvidenceType, string memory evidence)
```
{% endcode %}

This function is called by the owner of the original token if they have lost access to the protected token or it was stolen. It creates a dispute on an external ERC-792 compatible arbitrator.

#### submitMetaEvidence

{% code overflow="wrap" %}
```solidity
submitMetaEvidence(MetaEvidenceType evidenceType, string memory evidence)
```
{% endcode %}

This function allows the `metaEvidenceLoader` to submit meta evidence.

#### fetchRuling

{% code overflow="wrap" %}
```solidity
fetchRuling(uint256 requestId)
```
{% endcode %}

Fetches the ruling that is stored in the arbitrable proxy.

#### \_isApprovedOrOwner

{% code overflow="wrap" %}
```solidity
_isApprovedOrOwner(address spender, uint256 tokenId)
```
{% endcode %}

Checks if the given address is an approved spender or the owner of the token.

#### \_beforeTokenTransfer

{% code overflow="wrap" %}
```solidity
_beforeTokenTransfer(address from, address to, uint256 tokenId, uint256 batchSize)
```
{% endcode %}

Runs checks before a token transfer.

#### rescueERC20

{% code overflow="wrap" %}
```solidity
rescueERC20(address erc20, uint256 amount, address receiver)ol
```
{% endcode %}

This function allows the contract owner to rescue any ERC20 tokens sent to the contract by mistake.

### Structs

* `Request`: Contains the details of an ownership request or dispute.

### Enums

* `MetaEvidenceType`: Defines the types of meta-evidence.
* `ReqType`: Defines the types of requests.
* `Status`: Defines the statuses of requests.
* `Security`: Defines the security levels of tokens.

### Notes

The function `askOwnershipRestoreArbitrate` requires the sender to be the original owner of the token and the token to exist. Additionally, it requires that the sender is not currently the owner or approved spender of the token, and that the specified `MetaEvidenceType` is valid.

The `fetchRuling` function fetches the ruling of a given request and updates the request's status based on the ruling. If the ruling is accepted, it carries out the corresponding action based on the request type, which could be an ownership adjustment, ownership restoration, or token burn.
