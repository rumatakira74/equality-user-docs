# 1. About the platform

## What it is

Equality Project is a platform on which a community (a school, a cooperative, a volunteer group, a diaspora, a foundation, an event organizer) launches **its own isolated network** on the members' phones:

- **no servers** — the network lives on the phones themselves;
- **no administrator** — there is nobody to "switch off" the network or change its rules;
- **no operating costs** — there is no hosting or maintenance to pay for.

Each network gives its members three things:

1. **One person ≈ one wallet.** Entry is only through vouches from existing members plus a hardware check of the phone. This is the main barrier against fake accounts.
2. **An equal periodic entitlement.** The network's "unit" (hours, a quota, points) is issued to all active members **equally**, on a schedule.
3. **A public, verifiable history.** A member's reputation — the wallet's age, who vouched for whom, contributions — is visible to every member of the network.

What counts as the "unit" and what can be done with it is defined by the **network profile**: an internal currency, a time bank, quotas for a shared resource, accounting for volunteer contributions, etc.

A network is assembled from a **ready-made template** for one of eight scenarios: the organizer picks a template, sets the parameters — and gets their own network with its own app (APK).

## This is not a cryptocurrency

- The platform **does not issue or sell tokens**, creates no exchange market, and does not reward mining in the usual sense.
- Units exist only within a specific network, and in some profiles they are not transferable at all.
- The value is in the use (see the scenarios below), not in a unit's exchange rate.
- The words "wallet", "emission", "checkpoint" are the technical vocabulary of a log of signed records, not signs of a financial instrument.

## Eight usage scenarios

| No. | Scenario | Unit |
|-----|----------|------|
| 1 | Education and a laboratory of institutions (including simulations) | points or a game currency |
| 2 | Proof of personhood as a service for other apps | a non-transferable activity `heartbeat` |
| 3 | Equal quotas for a shared resource (water, internet, storage) | a quota per period; does not accumulate |
| 4 | Volunteer and street programs (meals, aid) | the program's vouchers |
| 5
 | A community's internal currency or time bank | hours or a currency; equal emission |
| 6 | Accounting for volunteer contributions | points for verified contributions |
| 7 | A mutual aid fund | a currency; demurrage against hoarding |
| 8 | A subscription resource — a subscription to a recurring resource (commercial) | a quota per period; unused amounts burn |

## Networks are isolated, and that is the main property

- Not one big network, but **many separate ones**. Each has its own membership, its own rules (a profile), its own units.
- There is no exchange between networks. One network's balance means nothing in another.
- The network's rules are written into the **manifest** at creation and are immutable by default; the manifest hash is fixed in the genesis. If the rules stop fitting the community — a new network is launched (it is free), and the members move over voluntarily.
- The network's guarantee level is **computed from the manifest**, not declared: partners can see which network a "person" comes from and with what guarantees.
- Every network is assembled with **its own app**: the label `Eq-<hash8>` (a short hash of the network's identifier) in the app's name shows that it is exactly your network that is installed; inside the app the network is signed with a name and a label — for example, "cirrus · Eq-e5796f9c".
- In subscription networks (scenario 8), quotas do not accumulate: the unused portion burns at the period boundary, and the surplus can be handed to those who need the resource (more in [Daily operations](03-operations.md)).

## Member roles

Each role is an ordinary wallet; nobody has any special "access rights":

- **Member** — a registered wallet; after activation it receives the issuance and transfers units.
- **Vouching member** — an active member with at least 3 months of standing who stands for a new person with one of their limited vouching slots.
- **Guardian** — a person assigned in advance to restore access when a phone is lost (personal guardians — 2 of 3; or public ones — 3 of 5).
- **Provider / pool recipient** — a wallet named in the network's parameters (for example, a partner location accepting vouchers). It cannot govern the network.

## Honest about the limits

- **No suitable smartphone — no participation.** The protocol requires an Android phone with a hardware-protected key store. There are no workarounds (curators, paper receipts).
- **Anonymity is not the goal.** The network's registry is public within the network: members see each other's addresses, statuses, and history; a balance is derivable from the network's public state.
- **Farm protection is economic, not absolute.** Creating an extra wallet must cost more than it yields; a full guarantee of "one person — one wallet" without an external anchor is technically impossible to give.

→ Next: [
Getting started](02-getting-started.md)
