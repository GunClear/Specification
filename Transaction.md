# Gunero Transaction Structure

## Definitions

### Account View Hash
In order to tie the authorization proof (which is generated once per Plasma cycle),
to the specific transaction in which a token is spent without incurring prohibitive
overhead on the transaction process, there is a need to define a public parameter that
is shared between the proofs verifying that the Account used to generate the authorization
proof is the same account specified in the transaction. It is re-computed every cycle,
and can be used multiple times.

This hash is computed as follows:
```
hash(public key + root hash + view randomizer)
```

### Token Unique Identifier
"Firearm View Randomizer" (random j) - randomly generated number shared between all owners of the firearm
```
hash(serial number + firearm view randomizer)
```

### Transaction Spend Nullifier
```
j*rho_old
```

### Transaction Hash
```
hash(s_S, A_R, T, W)
```

## Authorization Proof (Both Parties Generate)

### Public Parameters
* Authorization Root Hash (bytes32 hash)
* Account Status (uint2 plain)
* Account View Hash (bytes32 hash)

### Private Parameters
* Account Secret Key (uint252 plain)
* Authorization Merkle Path (160x bytes32 hash)
* Account View Randomizer (uint128 plain)

## Transaction Receive Proof (Receiver Generates)

### Public Parameters
* Authorization Root Hash (bytes32 hash)
* Token UID (bytes32 hash)
* Sender Account View Hash (bytes32 hash)
* Receiver Account View Hash (bytes32 hash)
* Current Transaction Hash (bytes32 hash)

### Private Parameters
* Receiver Private Key (uint252 plain)
* Receiver Account View Randomizer (uint128 plain)
* Sender Account Address (bytes20 hash)
* Sender Account View Randomizer (uint128 plain)
* Firearm Serial Number (bytes16 hash)
* Firearm View Randomizer (uint128 plain)

## Transaction Send Proof (Sender Generates)

### Public Parameters
* Current Authorization Root Hash (bytes32 hash)
* Token UID (bytes32 hash)
* Sender Account View Hash (bytes32 hash)
* Receiver Account View Hash (bytes32 hash)
* Previous Transaction Hash (bytes32 hash)

### Private Parameters
* Sender Private Key (uint252 plain)
* Sender Account View Randomizer (uint128 plain)
* Receiver Account View Randomizer (uint128 plain)
* Previous Sender Account Address (bytes20 hash)
* Previous Authorization Root Hash (bytes32 hash)

## Transaction Setup
In setting up a transaction, the sender must share the following with the receiver:
* Sender Account Address (bytes20 hash)
* Sender Account View Hash (bytes32 hash)
* Sender Account View Randomizer (uint128 plain)
* Firearm Serial Number (bytes16 hash)
* Firearm View Randomizer (uint128 plain)

The sender should share the following with the receiver (not strictly required):
* Sender Account Status (uint2 plain)
* Sender Authorization Proof

The receiver must share the following with the sender:
* Receiver Account Address (bytes20 hash)
* Receiver Account View Hash (bytes32 hash)
* Receiver Account View Randomizer (uint128 plain)
* Receiver Authorization Proof

## Network Format
### Provided with Transaction
This is the structure of the transaction communicated over the network:
* Token UID (bytes32 hash)
* Current Transaction Hash (bytes32 hash)
* Sender Account View Hash (bytes32 hash)
* Receiver Account View Hash (bytes32 hash)
* Sender Account Status (uint2 plain)
* Receiver Account Status (uint2 plain)
* Sender Authorization Proof
* Receiver Authorization Proof
* Transaction Receive Proof
* Transaction Send Proof

### Known Environment Parameters
The network operators and all other parties will know the following information,
given the information provided along with a transaction:
* Previous Transaction Hash (bytes32 hash)
* Current Authorization Root Hash (bytes32 hash)
