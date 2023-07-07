---
description: >-
  This smart contract manages arbitrators in the NFT Protect system. It is
  responsible for adding, deleting, and managing arbitrators.
---

# Arbitrator Registry

{% hint style="info" %}
The contract code can be found [here](https://github.com/nftprotect/nftprotect-contracts/blob/main/contracts/arbitratorregistry.sol).
{% endhint %}

### Variables

* `counter`\
  This variable keeps track of the total number of arbitrators added to the registry.
* `arbitrators`\
  This is a mapping from an arbitrator's ID (a uint256) to an `Arbitrator` structure, which contains information about the arbitrator.

#### Arbitrator

The Arbitrator structure contains the following fields:

* `name`: The name of the arbitrator.
* `arbitrator`: An instance of the `IArbitrableProxy` interface representing the arbitrator.
* `extraData`: Additional data associated with the arbitrator, stored as bytes.

### Events

* `Deployed()`

This event is emitted when the contract is deployed.

* `ArbitratorAdded(uint256 indexed id, string name, IArbitrableProxy arbitratorProxy, bytes extraData)`

This event is emitted when a new arbitrator is added. It includes the ID, name, `IArbitrableProxy` instance, and extra data associated with the new arbitrator.

* `ExtraDataChanged(uint256 indexed id, bytes extraData)`

This event is emitted when the extra data of an arbitrator is changed. It includes the ID of the arbitrator and the new extra data.

* `ArbitratorDeleted(uint256 indexed id)`

This event is emitted when an arbitrator is deleted. It includes the ID of the deleted arbitrator.

### Functions

#### addArbitrator

{% code overflow="wrap" %}
```solidity
addArbitrator(string memory name, IArbitrableProxy arb, bytes calldata extraData)
```
{% endcode %}

This function adds a new arbitrator to the registry. It requires the name of the arbitrator, an instance of `IArbitrableProxy`, and any extra data to be associated with the arbitrator. This function can only be called by the owner of the contract.

#### setExtraData

{% code overflow="wrap" %}
```solidity
setExtraData(uint256 id, bytes calldata extraData)
```
{% endcode %}

This function changes the extra data associated with an arbitrator. It requires the ID of the arbitrator and the new extra data. This function can only be called by the owner of the contract.

#### deleteArbitrator

{% code overflow="wrap" %}
```solidity
deleteArbitrator(uint256 id)
```
{% endcode %}

This function deletes an arbitrator from the registry. It requires the ID of the arbitrator. This function can only be called by the owner of the contract.

#### checkArbitrator

{% code overflow="wrap" %}
```solidity
checkArbitrator(uint256 id)
```
{% endcode %}

This function checks if an arbitrator exists in the registry. It requires the ID of the arbitrator.

#### arbitrator

{% code overflow="wrap" %}
```solidity
arbitrator(uint256 id)
```
{% endcode %}

This function returns the `IArbitrableProxy` instance and extra data associated with an arbitrator. It requires the ID of the arbitrator.

#### arbitrationCost

{% code overflow="wrap" %}
```solidity
arbitrationCost(uint256 id)
```
{% endcode %}

This function returns the arbitration cost associated with an arbitrator. It requires the ID of the arbitrator​[1](https://raw.githubusercontent.com/nftprotect/nftprotect-contracts/main/contracts/arbitratorregistry.sol)​.
