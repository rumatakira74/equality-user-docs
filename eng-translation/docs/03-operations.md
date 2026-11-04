# 3. Daily operations

## Issuance (emission)

In networks with periodic issuance, every active member once per period (a month by default) receives an **equal share**: for example, 1000 units on the 1st of the month.

Details:

- **The issuance challenge.** To claim the issuance, the app solves a computational task in **its own slot of the current period** (a window of ±48 hours). The moment of the slot is computed in advance from the address and the period and is the same for all nodes; the slot lies inside its own period, so the window is **reachable in every period** (after the mint fix — v9.14: earlier the window could fall at an unreachable time, and a wallet after six consecutive misses lost the issuance forever). The window state is shown by the issuance screen ("open — you can issue" / "closed — when it opens"). A missed period is not lost: the accrual moves within the **accrual window — 6 periods**, the funds are not locked; a deliberate skip longer than the window — the issuance burns.
- The first issuance is possible only in the period **after** activation, with no retroactive accruals.
- Freshly issued funds are not immediately transferable (the moratorium — see below).

## Transfers

- **The fee is burned.** Every transfer pays a small fee (`fee`) that is destroyed — the recipient receives exactly the stated amount. The fee protects the network from spam and only mildly "slows" the movement of value.
- **The rate is adaptive.** The fee percentage is recomputed by the network at the boundary of every epoch, identically for all nodes: if the supply of units grows faster than the target pace — the rate is raised, otherwise lowered. The range is 0.5% to 2%, with a minimum of 0.01 units; nobody can set the rate manually.
- **The moratorium for fresh wallets:** transfers become available 14 days after registration (a network parameter; 14 days is the default). This cuts off the "register — drain" scheme.
- **A transaction's time — the moment of signing.** The network's rules (the moratorium, quota burns, the deadlines of delayed transfers, the issuance window) apply to the moment the transaction was signed, not to the moment of its publication: a transfer signed offline and published later is evaluated identically by all nodes. The phone's clock must not diverge from the network by more than ±30 minutes — transactions with a greater divergence are not accepted by the network (republish after synchronizing the time).
- **Delayed large transfers.** A transfer above the threshold (by default **P = 3000 units**) is executed only after **48 hours**. During the delay you can cancel it right in the app — for example, under pressure or after changing your mind. The rule operates in all networks with transferable units and cannot be switched off. The threshold can be changed within the maximum (30000); a raise takes effect after 48 hours, a lowering — immediately.

### Subscription networks (recurring): periodic quotas

In subscription-resource networks (scenario 8) the units are **quotas per period**: every active member receives an equal quota, and the unused portion **burns at the boundary of the next period** — so a subscription does not turn into hoarding. Transferring or redeeming a unit of the past period after that boundary is impossible: the app shows a clear "the unit has burned" error. Nobody "zeroes out" the balance — the history is visible to everyone; the old quotas are simply no longer transferable.

The surplus can be handed to those who lack quota: transfers **member → member** and **member → provider** (the peer-redeem mode; the confirmation — a signed receipt). Note: the mode is supported by the core and the specification, but it is not yet implemented in the current app interface.

### Bluetooth payment

Bluetooth is used **only** for handing the signed transaction directly to the recipient when there is no internet. The recipient publishes the transaction into the network when connectivity appears.

**Important:** until the transaction is published and confirmed by the network, it **is not a payment**. The sender can hand the same amount to two recipients. That is why the interface shows the status "received over Bluetooth — awaiting publication", and the recipient must wait for the network's confir
mation.

## Demurrage (in currency networks)

In profiles with transferable value (an internal currency, a mutual aid fund) **demurrage** may operate — a small monthly "storage tax" above the exempt minimum. The charge is not carried out as a separate transaction: the effective balance is recomputed deterministically at the next operation.

The point: value is in the flow, not in accumulation. Demurrage and the burned fee are part of farm protection, not a way to take units away from you: demurrage can be "avoided" simply by not accumulating.

## Vouches

- A vouching member stands for a new member, spending one of their **slots** (3 at 3–12 months of standing, 5 beyond that).
- A slot is freed when the vouched-for member has completed 3 issuance periods without violations, or after 90 days if they never activated.
- The reward to vouching members — **10% of the first 12 issuances** of the vouched-for member, automatic and split equally among all three.
- If a violation is proven against the vouched-for member, the reward stops; no money is taken away from the vouching member.

## Violations and the flagged mark

The only provable violation is **equivocation**: two conflicting transactions signed by the same wallet (a double spend, a double issuance). The proof is published by any node, and everyone verifies it the same way. The consequences: the public `flagged` mark, issuance suspended for 3 months (on a repeat — forever), and a ban on vouching. "Looks like a farm" is not a proof — there are no verdicts based on suspicion.

## Access recovery

The key is non-exportable, so when a phone is lost, **social recovery** operates (the `migrate` transaction):

1. The new phone goes through the same check as at registration.
2. The guardians confirm the migration: **personal 2 of 3** or **public 3 of 5** (you can combine).
3. **A 14-day delay**, during which the old key (if it is alive) can cancel the migration.
4. The age, history, vouches, issuances **and the funds (the balance)** are carried over to the new wallet; the old fingerprint goes on the blacklist forever.

### Recovery card — fill it out in advance

To start a migration, the new phone will require entering the **old wallet address**, and then the nonce and the guardians' signatures. This data cannot be "restored out of thin air": it was not preserved on the lost phone.

**In advance, while the phone is alive:**

- write down **your wallet's address** (hex, shown in the app) and keep it off the phone (not in the cloud) — on paper or as a printed QR code;
- write down **your guardians' addresses** and how to contact them;
- write down **the network's name** (the app shows it with the `Eq-<hash8>` label) and where to get its APK (each network distributes its own build).

The app shows all this data on the **"Recovery card"** screen at wallet creation (and later — in the settings and on the migration screen) with a QR code: export or print it.

**During the migration:**

- the nonce and the guardians' signatures are the keys to recovering your wallet: **do not hand them to anyone and do not publish them**;
- hand them over **only directly** between yourself and your guardian — in person or over a secure channel, not through third parties;
- enter them only into your own app; after the migration completes, delete them from your message histories.

A public guardian (a member with ≥
 12 months of standing) receives a fixed reward from the emission for a ward's successful migration — no more than once per 12 months per ward.

**If no guardians were assigned**, what remains is a restart: a new registration with a new key and three new vouches. The funds on the old wallet are lost in that case — assign guardians in advance.

### Guardian re-election

Has a guardian died, disappeared, or left the network — the guardians can be **re-elected** (the `update_guardians` transaction):

1. **The consent of the new guardians.** Each new guardian (up to 3) signs the hash of the change in person — the same way as when confirming a migration: without their signatures the change is impossible.
2. **Publishing the change.** Settings → Guardians → "Re-elect"; publishing and canceling — only after explicit PIN entry.
3. **A 48-hour window.** The change takes effect 48 hours after publication; until then it can be canceled (also only with the PIN).
4. **The limit — 150 changes.** No more than 150 effective changes over the wallet's lifetime; canceled and expired ones do not count. The counter of the remaining changes is visible in the app.

There is no fee for the change; every change is published into the network's history. The new guardians must be active (`active`) and without the `flagged` mark. In decoy mode, "guardian re-election" plausibly "executes", but the real guardian list is untouched.

→ Next: [Owner security](04-security.md)
