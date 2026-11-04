# 5. Questions and answers · Glossary

## FAQ

**Is internet needed?**
For ordinary operations — yes, connectivity at least from time to time. Bluetooth lets you hand a signed transaction directly to the recipient, but the payment only happens after publication and confirmation by the network.

**I don't know anyone in the network. How do I get activated?**
Through the community's public channels: newcomers find vouching members there. The vouching member answers with a limited slot and a reward — handing out vouches to just anyone is against their own interest. A vouch can be arranged in person via a QR code or Bluetooth.

**I lost my phone. What happens to the units?**
The key is non-exportable, but social recovery works: guardians (personal 2 of 3 or public 3 of 5) confirm the migration to the new phone; after 14 days the age, history, vouches, and funds are carried over. Without assigned guardians — only a new registration, and the funds on the old wallet are lost.

**Can I change guardians?**
Yes. If a guardian has disappeared, died, or left the network, re-elect them: the new guardians sign the hash of the change in person, the change is published with explicit PIN entry, and it takes effect after 48 hours (until then it can be canceled). The limit is 150 effective changes over the wallet's lifetime. In detail — [Guardian re-election](03-operations.md#guardian-re-election).

**I forgot both PINs.**
The wallet becomes inaccessible: the key cannot be extracted, and the PIN cannot be "reset by email" — there are no such channels in a system without servers. The only path is migration through guardians.

**Can someone forge my wallet?**
The key is in the phone's protected storage; only it can sign an operation. Forgery is impossible without physical access to the unlocked device.

**What if someone creates hundreds of wallets (a farm)?**
The barriers: 3 vouches per wallet (slots are limited), hardware attestation (emulators and rooted devices do not pass, and the attestation chain is bound to the key being registered), the computational challenge in the slot of the current period, the transfer moratorium, the fee, and demurrage. The farm economy model: at the canonical estimate of $120 per device, a farm turns a profit no earlier than in ~3.5 years (at $200 — in ~4.5 years) and only at a high external value of the unit; several wallets on one device make a farm cheaper — the sustainability of the conclusion was verified with a sensitivity grid (device cost × the number of wallets per device). The verification horizon for the security metric — at least 5 years. Nobody gives a guarantee of "one person — one wallet": the protection is economic.

**Why did the balance decrease on its own?**
Demurrage operates in currency networks — a small monthly percentage above the exempt minimum. It is reflected at the next operation; there is no separate charge transaction.

**A transfer is "stuck" for 48 hours. Is this a ha
ck?**
No, it is a delayed transfer: an amount above the threshold (3000 by default) always executes after 48 hours, and you can cancel it before execution.

**Can voting be secret inside the network?**
In v1 — no: the identifier for a third-party app is publicly linked to the address. Secret voting is possible only in future versions.

**The app says "the unit has burned". What is that?**
You are in a subscription network (recurring): the quota is bound to the period, and after the boundary of the next period it can no longer be transferred. This is not a fine and not a loss of balance — the new quota arrives in the new period; it is better to hand the surplus via peer-redeem to those who need the resource.

**How much does participation cost?**
The network charges nothing for participation. The platform has no operating costs at all — there are no servers. The transfer fee is burned, it does not go to anyone.

## Glossary

| Term | Meaning |
|------|---------|
| **Wallet** | A member's account: an address + a chain of signed records + a balance. One per device. |
| **Registry** | The public journal of all the network's transactions; every node stores and verifies it. |
| **Genesis** | The network launch package: the parameters, the manifest, the seed circle. |
| **Protocol version (`protocolVersion`)** | The version number of the network's rules (currently 3). It is written in every transaction and checkpoint; the app and the network must match on the protocol version — a build of a different version is not accepted by the network. |
| **Manifest** | The public description of the network's rules; its hash is fixed in the genesis. |
| **Seed circle** | The first members from the genesis with temporary special rights; the rights self-liquidate (seed_sunset: 100 active wallets or 24 epochs). |
| **Vouch** | A signed handle of an existing member vouching for a newcomer. Three of them activate a wallet. |
| **Vouching slot** | A limited place of a vouching member; it is freed after 3 issuance periods of the vouched-for member or 90 days. |
| **Issuance challenge** | A computational task (PoW) in the slot of the current period, computable in advance; the ±48 h window is available in every period, and its state is shown by the issuance screen; a missed one is compensated within the accrual window (6 periods). |
| **Epoch** | An interval of network time (24 hours by default); checkpoints are placed at epoch boundaries. |
| **Checkpoint** | A snapshot of the network's state signed by a threshold of members; it gives finality and protection for light nodes. |
| **Finality** | The moment after which a transaction cannot be rolled back. |
| **Moratorium** | The period after registration (14 days by default) when outgoing transfers are unavailable. |
| **Demurrage** | A monthly percentage on holding above the minimum; the charged amount is burned. |
| **Decoy mode** | The mode opened by the duress PIN: a plausible interface with a small balance, and no real operations h
appen. |
| **Guardian** | A member assigned to confirm the migration when a phone is lost. |
| **Migration** | Carrying the wallet over to a new device through the guardians; a 14-day delay. |
| **Guardian re-election** | Re-election of personal guardians (up to 3) with their consent; a 48 h window, a limit of 150 effective changes over the wallet's lifetime. |
| **Flagged** | A public mark of a proven violation (equivocation). |
| **BT payment** | Handing a signed transaction over Bluetooth; it becomes a payment only after confirmation by the network. |
| **Network profile** | A set of parameters: the unit, issuance, transfer, the sink, entry, etc. |
| **Eq-hash (`Eq-<hash8>`)** | A short label of the network (the first 8 characters of its identifier); visible in the app's name and on onboarding — it is used to check that the right network is installed. |
| **Recurring (subscription network)** | A network of a subscription resource: an equal quota per period, and unused amounts burn at the period boundary. |
| **Peer-redeem** | A transfer member → member or member → provider in recurring networks: quota surpluses flow to those who need the resource (not yet implemented in the current app interface). |
| **Quota burn** | A unit of a past period stops being transferable after the boundary of the next period; the balance and history are preserved. |

---

[← About the platform](01-about.md) · [Contents](../README.md)
