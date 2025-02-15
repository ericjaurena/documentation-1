---
layout: nodes.liquid
section: smartContract
date: Last Modified
title: "API Reference"
permalink: "docs/chainlink-vrf-api-reference/"
hidden: false
metadata: 
  title: "Chainlink VRF API Reference"
  description: "API reference for VRFConsumerBase."
  image: 
    0: "https://files.readme.io/b5afbbd-670379d-OpenGraph_V3.png"
    1: "670379d-OpenGraph_V3.png"
    2: 1459
    3: 1459
    4: "#dbe1f8"
---
API reference for <a href="https://github.com/smartcontractkit/chainlink/blob/master/evm-contracts/src/v0.6/VRFConsumerBase.sol" target="_blank">`VRFConsumerBase`</a>.

# Index

## Constructors

|Name|Description|
|---|---|
|[constructor](#constructor)|Initialize your consumer contract.|

## Functions

|Name|Description|
|---|---|
|[requestRandomness](#requestrandomness)|Make a request to the VRFCoordinator.|
|[fulfillRandomness](#fulfillrandomness)|Called by VRFCoordinator when it receives a valid VRF proof.|

___

# Constructor

Initialize your consumer contract.

```javascript Solidity
constructor(address _vrfCoordinator, address _link) public
```

* `_vrfCoordinator`: Address of the Chainlink VRF Coordinator. See [Chainlink VRF Addresses](../vrf-contracts/) for details.
* `_link`: Address of the LINK token. See [LINK Token Addresses](../link-token-contracts/) for details.

___

# Functions

## requestRandomness

Make a request to the VRF coordinator.

```javascript Solidity
function requestRandomness(bytes32 _keyHash, uint256 _fee, uint256 _seed)
    public returns (bytes32 requestId)
```

* `_keyHash`: The public key against which randomness is generated. See [Chainlink VRF Addresses](../vrf-contracts/) for details.
* `_fee`: The fee, in LINK, for the request. Specified by the oracle.
* `_seed`: This is the seed from which output randomness is determined. Provided by you.
* `RETURN`: The ID unique to a single request.

## fulfillRandomness

Called by VRFCoordinator when it receives a valid VRF proof. Override this function to act upon the random number generated by Chainlink VRF.

```javascript Solidity
function fulfillRandomness(bytes32 requestId, uint256 randomness)
    external virtual;
```

* `requestId`: The Id initially returned by `requestRandomness`.
* `randomness`: Random number generated by Chainlink VRF.
___

# Reference

## Choosing A Seed

Since the ultimate input to the VRF is mixed with the block hash of the block in which the request is made, user-provided seeds have no impact on its economic security properties. They are only included for API compatibility with previous versions of this contract.

## Maximizing security

Chainlink VRF provides powerful security guarantees and is easy to integrate. However, smart contract security is a nuanced topic. If you have specific questions about your integration, please contact [vrf@chain.link](mailto:vrf@chain.link)