# System Architecture and Components

The GunClear system is composed of 3 major software products:
1. The [PlasmaRifle](https://github.com/GunClear/PlasmaRifle) Rootchain library
2. The [Silencer](https://github.com/GunClear/Silencer) ZKP library
3. The [Gunero](https://github.com/GunClear/Gunero) network client

## PlasmaRifle

The PlasmaRifle library deals with managing the complexity of interacting with the Rootchain,
which is currently Ethereum. This includes functionality for each of the 3 [Actors](Actors.md)
to perform their relevant abilities and interact with the Rootchain network, as well as Private
Key management, Web3 provider networking, and transaction broadcasting.

More details about the architecture of PlasmaRifle is available in the project
[wiki](https://github.com/GunClear/PlasmaRifle/wiki).

## Silencer

The Silencer library deals with the proving and verification of the Zero Knowledge Proofs that
Gunero clients use to ensure the transactional privacy of all Members in the Gunero Network.
It also contains the method for generating keys used for proving and verification, which
are creating during an open participation ceremony inspired heavily by the Zcash
[MPC](https://z.cash/blog/completion-of-the-sapling-mpc/)  ceremony.
These keys are used to ensure that it is not possible to generate false proofs,
which is important in ensuring bad actors cannot use the system to facilitate
improper trades.

Please note that due to the structure of zero knowledge proofs, critical identity and ownership
information is never transmitted to anyone but the counterparty in a transaction. This is one of
the fundamental tenents of our system.

More technical details about Silencer proofs is available in the project
[wiki](https://github.com/GunClear/Silencer/wiki).

## Gunero

The Gunero network client integrates both of the libraries mentioned above and provides fully-
functioning full and light node clients for the Gunero network. Full node clients are used to
verify the integrity of the network, and can also service light client requests for critical
data required for Members to control their digital ownership. Light node clients are used by
our Membersto conduct transactions easily and safely in resource-constrained environments,
and is the node used in our mobile app to make our technology portable and user-friendly.

More details about the architecture of the Gunero client is available in the project
[wiki](https://github.com/GunClear/Gunero/wiki).
