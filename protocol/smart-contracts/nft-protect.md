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

**setFee**

{% code overflow="wrap" %}
```solidity
setFee(Security level, uint256 fw)
```
{% endcode %}

This function allows the contract owner to set the fee associated with a given security level. The fee is required for certain operations within the contract.

**setArbitratorRegistry**

{% code overflow="wrap" %}
```solidity
setArbitratorRegistry(address areg)
```
{% endcode %}

This function allows the contract owner to set the address of the arbitrator registry. The arbitrator registry is a contract that manages arbitrators who make decisions in disputes.

**setUserRegistry**

{% code overflow="wrap" %}
```solidity
setUserRegistry(address ureg)
```
{% endcode %}

This function allows the contract owner to set the address of the user registry. The user registry is a contract that manages the users of the system.

**setBurnOnAction**

{% code overflow="wrap" %}
```solidity
setBurnOnAction(bool boa)
```
{% endcode %}

This function allows the contract owner to set whether protected tokens should be burned when an action is taken. If set to true, the protected tokens will be destroyed, effectively reducing the total supply of tokens.

**setBase**

{% code overflow="wrap" %}
```solidity
setBase(string memory b)
```
{% endcode %}

This function allows the contract owner to set the base URI for all token metadata. The base URI is prepended to the token-specific identifiers to generate the full URI for each token.

**setScoreThreshold**

{% code overflow="wrap" %}
```solidity
setScoreThreshold(uint256 threshold)
```
{% endcode %}

This function allows the contract owner to set the threshold for user scores. This score threshold may be used in various operations within the contract, for example, to determine if a user can perform certain actions.

**setMetaEvidenceLoader**

{% code overflow="wrap" %}
```solidity
setMetaEvidenceLoader(address mel)
```
{% endcode %}

This function allows the contract owner to set the address of the meta evidence loader. The meta evidence loader is a contract that manages the submission of meta evidence.

**onERC721Received**

{% code overflow="wrap" %}
```solidity
onERC721Received(address /*operator*/, address /*from*/, uint256 /*tokenId*/, bytes calldata /*data*/)
```
{% endcode %}

This function is a standard interface for handling incoming ERC721 tokens. It's called by an ERC721 smart contract when a token is transferred to this contract.

**onERC1155Received**

{% code overflow="wrap" %}
```solidity
onERC1155Received(address /*operator*/, address /*from*/, uint256 /*id*/, uint256 /*value*/, bytes calldata /*data*/)
```
{% endcode %}

This function is a standard interface for handling incoming ERC1155 tokens. It's called by an ERC1155 smart contract when a token is transferred to this contract.

**onERC1155BatchReceived**

{% code overflow="wrap" %}
```solidity
onERC1155BatchReceived(address /*operator*/, address /*from*/, uint256[] calldata /*ids*/, uint256[] calldata /*values*/, bytes calldata /*data*/)
```
{% endcode %}

This function is a standard interface for handling incoming batches of ERC1155 tokens. It's called by an ERC1155 smart contract when multiple tokens are transferred to this contract at once.

**tokenURI**

{% code overflow="wrap" %}
```solidity
tokenURI(uint256 tokenId)
```
{% endcode %}

This function returns the full URI for the metadata associated with the token specified by `tokenId`. It's part of the standard interface for ERC721 tokens and is used to provide information about the token.

**originalOwnerOf**

{% code overflow="wrap" %}
```solidity
originalOwnerOf(uint256 tokenId)
```
{% endcode %}

This function is used to determine the original owner of the token specified by `tokenId`. This information can be used to track the provenance of tokens.

**isOriginalOwner**

{% code overflow="wrap" %}
```solidity
isOriginalOwner(uint256 tokenId, address candidate)
```
{% endcode %}

This function checks whether the given address is the original owner of the token with the specified `tokenId`. This can be useful in functions that need to validate the original owner.

**protect**

{% code overflow="wrap" %}
```solidity
protect(Standard std, address contr, uint256 tokenId, uint256 amount, Security level, address payable referrer)
```
{% endcode %}

This function allows a user to protect their token by transferring it to this contract. In return, the contract mints a protected token that represents the original token. The protected token can be transferred or sold independently of the original token.

**burn**

{% code overflow="wrap" %}
```solidity
burn(uint256 tokenId, address dst, uint256 arbitratorId, string memory evidence)
```
{% endcode %}

This function allows a user to burn their protected token and return the original token to the owner. If the token's security level is not Basic, a dispute is created and the evidence is passed to the arbitrator for resolution.

**adjustOwnership**

{% code overflow="wrap" %}
```solidity
adjustOwnership(uint256 tokenId, uint256 arbitratorId, string memory evidence)
```
{% endcode %}

This function allows a user to adjust the ownership of the original token to the current owner of the protected token. If the token's security level is not Basic, a dispute is created and the evidence is passed to the arbitrator for resolution.

**askOwnershipAdjustment**

{% code overflow="wrap" %}
```solidity
askOwnershipAdjustment(uint256 tokenId, address dst, uint256 arbitratorId)
```
{% endcode %}

This function allows a user to create a request for ownership adjustment. This can be useful if the ownership of the original token has become inconsistent with the ownership of the protected token.

**answerOwnershipAdjustment**

{% code overflow="wrap" %}
```solidity
answerOwnershipAdjustment(uint256 requestId, bool accept, string memory evidence)
```
{% endcode %}

This function allows the owner of the original token to confirm or reject a proposed ownership adjustment. The owner can provide evidence to support their decision.

**askOwnershipAdjustmentArbitrate**

{% code overflow="wrap" %}
```solidity
askOwnershipAdjustmentArbitrate(uint256 requestId, string memory evidence)
```
{% endcode %}

This function allows a user to escalate an unresolved ownership adjustment request to an external arbitrator. The user can provide additional evidence to support their case.

**askOwnershipRestoreArbitrate**

{% code overflow="wrap" %}
```solidity
askOwnershipRestoreArbitrate(uint256 tokenId, address dst, uint256 arbitratorId, MetaEvidenceType metaEvidenceType, string memory evidence)
```
{% endcode %}

This function allows the original owner of a token to open a dispute if they have lost access to their protected token. The dispute is passed to an ERC-792 compatible external arbitrator for resolution.

**submitMetaEvidence**

{% code overflow="wrap" %}
```solidity
submitMetaEvidence(MetaEvidenceType evidenceType, string memory evidence)
```
{% endcode %}

This function allows the meta evidence loader to submit meta evidence of a certain type. The evidence can be used in disputes to provide additional context or information.

**rescueERC20**

{% code overflow="wrap" %}
```solidity
rescueERC20(address erc20, uint256 amount, address receiver)
```
{% endcode %}

This function allows the contract owner to transfer a specified amount of any ERC20 token that has become stuck in the contract to a specified receiver.

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
