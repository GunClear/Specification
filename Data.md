# Handling Your Data

The GunClear system manages several critical pieces of data representing digital ownership in our system.
"Ownership" is a controversial word to use in this context, because the leaking of this critical data gives
external actors the ability to monitor our Members and reconstruct their ownership history. It is therefore
of paramount importance that this data be handled appropiately, ensuring the privacy of this data even
against the corruption of the project maintainers and service providers (including GunClear) in our network.

To show that this data is correctly handled, first we will scope the layout of this data, who has access to
what pieces of data, and how it is used across our system architecture.

## GunClear Membership Card

When a member wants to be added to our network, they first go through a review process with the
[GunClear Authority](Actors.md#gunclear-authority). This process involves verification of the revelent
documentation required by your state of residence to be a legally compliant firearm owner. This identity
verification process may include opting in to the relevant background checks and other routine verifications
such that once you become an Member, you will not have to worry about keeping up to date in order to be
considered a legally compliant individual in the eyes of the law in your state.

Once you pass this identity verification, a psuedo-anonymous identifier derived from a secret you (and only
you!) control is then authorized in our network (see [here](https://github.com/GunClear/PlasmaRifle/wiki/Authlist)
for technical details), meaning your identity is now a GunClear Member.

As a Member, you have the ability to construct a Proof of Membership that completely hides your identity
but allows you to prove to others that you are indeed a legitimate Member of our network. An analogy for this
proof is that you are now granted a "Membership Card" with no information on it other than you are a legitimate
Member of the network. For more information about this proof, please read the technical overview of
the data in the [proof](https://github.com/GunClear/Specification/blob/master/Transaction.md#authorization-proof-both-parties-generate).

## GUN Token and the Lockbox

This "Membership Card" gives you several privledges in our network. First, you can present this card to the
GunClear Authority, along with releveant documentation, to have a digital record of your firearm called a
"Token" created, allowing it to be traded on the Gunero network. The documentation provided varies by state,
but typically includes the serial number. The Token we create has an identifier that you specify when you give
us the documentation, meaning it is encrypted and the serial number (if provided) is never made public.

When you provide us with this encrypted Token, you also provide us with a "Lockbox"
(see [here](https://github.com/GunClear/Specification/blob/master/Transaction.md#transaction-lock))
that we use when moving the Token to our Gunero trading network, ensuring your privacy as your identity
never makes a public transaction. The Lockbox ensures only the current owner can unlock the Token and
trade to a new owner without ever sharing personally identifiable information inside a transaction.

It is relevant to note that creating a Token is only conducted once. Once the Token has been created, it can be
traded without ever having to re-authorize it, as every trade is conducted between two qualified individuals
that present their Membership Cards, and convince the rest of the network to accept their trade. Every firearm
traded using our network has a chain of ownership back to when the Token was created, meaning there is a private
but verifiable chain of transactions between GunClear members were the Firearm has been in "good hands" the entire
way. In fact, if the Token were originally created at the first point of sale, it is possible to validate the
entire ownership history back to the point of origin, no many how many GunClear Members have owned it.
All without tracking anyone's identity!

---

# Your Privacy

These two pieces of information, the psuedo-anonymous account identifier that allows you to show your "Membership
Card" and the Token representing your firearm, are the only two pieces of information that are visible to anyone watching.
Both are encrypted pieces of data that are secured on the Member's device using a secret key that is never shared with
anyone, including the GunClear Authority. They are never made available in an unecrypted form, and they are never
transmitted together, not even to the GunClear Authority.

Your firearm ownership is yours, and yours alone. No one should have access to this data but you. Don't take us on our
word in that. The most important thing you can do, as a Member (or skeptic!), is to verify our claims in our code
and help us improve our privacy guarentees so that all firearm owners can realize the benefits of digital ownership
without the fear of digital surveilance.
