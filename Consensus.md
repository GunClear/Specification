# Gunero Network Consensus

The Gunero network relies on a proof-of-authority (PoA) consensus mechanism, which allows a
trusted set of signers to propose and mine new blocks in a round-robin-style voting process
(see the [Parity wiki](https://wiki.parity.io/Proof-of-Authority-Chains) for more information).
This consensus mechanism ensures scalable and reliable chain operation, and the timely acceptance
of transactions. This mechanism has been proven in practice on several Ethereum test networks.

The set of signers is managed via an [Operator Registry](Components.md) contract on the Ethereum
main chain. Anyone can apply to become an Operator by staking a bond and registering with the
pool. This registration can be removed at any time until it is confirmed. Once confirmed, all
Operators are expected to perform the duty of securing the network, and their stake joins the
bond pool that the Plasma dispute mechanism is incentivized with.

The Operators can also propose a vote to remove one of the authorized signers if they are not
acting reliably, lost their keys, or are actively malicious. Their bond is returned in proportion
to the number of votes that elect to return it. For example, if there are 11 Operators, and they
wish to remove one of the signers, if 4 out of 10 elect to return the bond and 6 out of 10 do not,
then only 40% of the stake will be returned to the ejected signer (the rest is burned). Returning
in the event of key loss is only possible if the bond was original placed by a different account
on behalf of the signer, in which case the bond will be returned to the proposing account.

Lastly, the Operators have the ability to re-assign the GunClear Authority, who has access to
authorize Firearm Owners and mint new tokens on their behalf, if the Authority is found not
to be acting in the best interests of it's members, or if the Authority's keys are lost. The
Authority does not place a bond to be in this role, but loses complete control over their
administration of the network and suffers a significant reputation loss as a result.
