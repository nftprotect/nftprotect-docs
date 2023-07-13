---
description: >-
  This smart contract is responsible for registering and managing users in the
  NFT Protect system and handling affiliate and partner payments.
---

# User Registry

{% hint style="info" %}
The contract code can be found [here](https://github.com/nftprotect/nftprotect-contracts/blob/main/contracts/userregistry.sol).
{% endhint %}

### Prerequisites

Before diving into each function's details, let's understand some of the key entities, variables, and concepts used in the contract:

1. **NFT Protect:** The main system or service that uses the UserRegistry contract.
2. **DID (Decentralized Identifier):** A new type of identifier that enables verifiable, decentralized digital identity.
3. **NFTP Coupons:** A contract managing coupons that users can use for specific actions.
4. **Successor:** A user designated to take over another user's account for specific events.
5. **Arbitrator:** A third-party entity or service used to resolve disputes.
6. **Referrer:** A user who refers another user to the platform.
7. **Partner:** A user or entity with a specific partnership agreement with the platform.

### Constructor

The contract's constructor sets initial values for several key variables and emits the `Deployed` event. It also calls the `setAffiliatePercent`, `setArbitratorRegistry`, and `registerDID` functions, establishes a new `NFTPCoupons` contract, and transfers ownership of the coupon contract to the message sender.

### Modifiers

The contract uses the `onlyNFTProtect` modifier to restrict certain function calls to the address stored in the `nftprotect` variable.

### Events

The contract emits several events to log significant actions, such as changing the arbitrator registry, setting a referrer, registering a DID, or requesting/approving/rejecting a successor.

### Variables

The contract uses a variety of variables to store data, including public addresses for various system components (like the `nftprotect` and `metaEvidenceLoader`), the `affiliatePercent` for referrers, a `numberOfRulingOptions` constant, and several mappings to store referrers, partners, successors, and requests for successors.

### Structs

The contract defines a `SuccessorRequest` struct to store information about a request for a successor, including the user, the successor, the arbitrator, and dispute IDs.

### Functions

#### constructor

{% code overflow="wrap" %}
```solidity
constructor(address areg, IUserDID did, address nftprotectaddr)
```
{% endcode %}

This is the contract's constructor function, which is executed once when the contract is deployed. It initializes the contract with the provided parameters:

* **`areg`**: The address of the arbitrator registry.
* **`did`**: The decentralized identifier (DID) of the user.
* **`nftprotectaddr`**: The address of the NFT Protect service.

#### setArbitratorRegistry

{% code overflow="wrap" %}
```solidity
setArbitratorRegistry(address areg)
```
{% endcode %}

Sets the arbitrator registry to a new address. This can only be called by the contract owner. It also emits the `ArbitratorRegistryChanged` event.

#### setAffiliatePercent

```solidity
setAffiliatePercent(uint256 percent)
```

Sets the percentage of affiliate commission. This function can only be called by the contract owner and emits an `AffiliatePercentChanged` event.

#### setPartner

{% code overflow="wrap" %}
```solidity
setPartner(address partner, uint256 percent)
```
{% endcode %}

Sets a partner with a specific commission percentage. Only the contract owner can call this function. It emits a `PartnerSet` event.

#### processPayment&#x20;

{% code overflow="wrap" %}
```solidity
processPayment(address user, address payable referrer, bool canUseCoupons, uint256 fee) 
```
{% endcode %}

This function is used to process payments from users. If the user has coupons and `canUseCoupons` is true, a coupon will be used. Otherwise, the function checks that the correct fee is paid and handles the affiliate payment if a referrer exists. The function can only be called by the NFT Protect service.&#x20;

#### registerDID&#x20;

{% code overflow="wrap" %}
```solidity
registerDID(IUserDID did) 
```
{% endcode %}

Registers a new decentralized identifier (DID) for a user. This function can only be called by the contract owner and emits a `DIDRegistered` event.&#x20;

#### unregisterDID&#x20;

```solidity
unregisterDID(IUserDID did) 
```

Unregisters a user's decentralized identifier (DID). This function can only be called by the contract owner and emits a `DIDUnregistered` event.&#x20;

#### isRegistered&#x20;

```solidity
isRegistered(address user) 
```

Checks whether a user is registered by iterating over all DIDs and checking if the user is identified by any of them.&#x20;

#### scores&#x20;

```solidity
scores(address user) 
```

Returns the maximum score among all DIDs for a user.&#x20;

#### isSuccessor&#x20;

```solidity
isSuccessor(address user, address successor) 
```

Checks if the given address is set as a successor for a user.&#x20;

#### hasSuccessor&#x20;

```solidity
hasSuccessor(address user) 
```

Checks if a user has a successor.&#x20;

#### successorRequest&#x20;

{% code overflow="wrap" %}
```solidity
successorRequest(address user, uint256 arbitratorId, string memory evidence) 
```
{% endcode %}

Allows a user to request a successor. It requires that the user is registered. The function creates a dispute with the arbitrator service, stores the request, and emits a `SuccessorRequested` event.&#x20;

#### fetchRuling&#x20;

```solidity
fetchRuling(uint256 requestId) 
```

Fetches the ruling of a dispute about a successor request. If the dispute is resolved, the function sets the successor or rejects the request, depending on the ruling, and deletes the request.
