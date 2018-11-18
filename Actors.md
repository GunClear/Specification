# System Actors

The GunClear system is made up of 3 principle actors:
1. Gunero Network Operators
2. The GunClear Authority
3. Firearm Owners

## Gunero Network operators

The network operators (the "Operators") are in charge of managing the Gunero network by proposing and mining
blocks via the [consensus](Consensus.md) mechanism. They are also in charge of  updating the rootchain contract
with state entry updates. Their goal is to drive the network towards consensus and transaction finality. They
also have the ability to reassign the GunClear Authority in case there is an abuse of Authority's power.

## GunClear Authority

The GunClear Authority (the "Authority") is in charge of proposing new Operators and authorizing Firearm Owners.
Their administration ensures the health of the network, and ensures their members are able to conduct safe,
private, and legally compliant transactions with each other. They investigate instances of fraud on the
platform, and ensure that all GunClear members are responsible firearm owners, protected from firearms
that are used in crimes and other abuses. In return for their proper stewardship, firearm owners allow
the Authority to continue their admininstration of the network, making it stronger and safer for it's members.

## Firearm Owners

Firearm Owners (aka "Members") are the end-users of the GunClear system. They exchange firearm ownership tokens
with each other, and rely on the Operators to facilitate the acceptance of those transactions. They also have
the duty to ensure that the Operators are performing their duties correctly and in a timely manner. They have
the ability to dispute the transaction history the operators upload through the [Plasma](Components.md) dispute
mechanism, and may earn an incentive for doing so. Finally, they ultimately exercise control over the network
by organizing and participating in a network upgrades. They can elect a new Authority and group of Operators
if the current ones are violating the trust of the network, ensuring that these parties act in accordance to
their responsibilities and earn the trust of their fellow Members.
