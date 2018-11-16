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

## Authorization Proof

### Public Parameters
* Authorization Root Hash (bytes32 hash)
* Account Status (uint2 plain)
* Account View Hash (bytes32 hash)

### Private Parameters
* Account Secret Key (uint252 plain)
* Authorization Merkle Path (160x bytes32 hash)
* Account View Randomizer (uint128 plain)

## Transaction Spend Proof

### Public Parameters
* Authorization Root Hash (bytes32 hash)
* Token UID (bytes32 hash)
* Firearm Spend Nullifier
* Firearm Receive Commitment
* Sender Account View Hash (bytes32 hash)
* Receiver Account View Hash (bytes32 hash)

### Private Parameters
* Sender Private Key (uint252 plain)
* Sender Account View Randomizer (uint128 plain)
* Receiver Account Address (bytes20 hash)
* Receiver Account View Randomizer (uint128 plain)
* Firearm Serial Number (bytes16 hash)
* Firearm View Randomizer (uint128 plain) - shared with
* Firearm Spend Key (uint128 plain) - rho_1
* Firearm Receive Key (uint128 plain) - rho_2

## Transaction Structure
* Firearm Spend Commitment
