---
description: >-
  This smart contract represents an ERC20 token with unique properties and
  functionalities specific to the NFT Protect platform.
---

# NFTP Coupons

{% hint style="info" %}
The contract code can be found [here](https://github.com/nftprotect/nftprotect-contracts/blob/main/contracts/nftpcoupons.sol).
{% endhint %}

### Variables

* `transferrable`\
  A boolean that indicates whether the tokens are transferrable.
* `nftprotect`\
  An address variable that holds the address of the NFT Protect contract.

### Events

*   `Deployed()`

    This event is emitted when the contract is deployed.
*   `TransferrableSet(bool state)`

    This event is emitted when the `transferrable` state of the contract is set.

### Modifiers

*   `onlyOwner()`

    This modifier ensures that the wrapped method can only be executed by the owner of the contract.

### Functions

#### constructor

```solidity
constructor(address nftp)
```

This is the constructor function which is called when the contract is deployed. It sets the initial state of the contract, including the name of the token, the symbol of the token, the address of the NFT Protect contract, and makes the token transferrable.

#### decimals

```solidity
decimals()
```

This function overrides the `decimals()` function from the ERC20 token standard to return 0. This means that the token has no decimal places.

#### setTransferrable

```solidity
setTransferrable(bool state)
```

This function allows the owner of the contract to set the `transferrable` state of the contract. When `transferrable` is true, tokens can be transferred between addresses. When `transferrable` is false, tokens cannot be transferred.

#### mint

```solidity
mint(address account, uint256 amount)
```

This function allows the owner of the contract to mint new tokens to a specified account.

#### burnFrom

```solidity
burnFrom(address account, uint256 amount)
```

This function allows the NFT Protect contract to burn tokens from a specified account.
