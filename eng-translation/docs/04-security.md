# 4. Owner security

## PIN and biometrics: which one is for what

| Action | Confirmed by |
|--------|--------------|
| Signing in to the app | fingerprint **or** PIN |
| A transfer, issuance, starting a migration | **explicit PIN entry only** |
| Guardian re-election (publishing, canceling) | **explicit PIN entry only** |
| Unlocking the key inside an operation | biometrics after the PIN — "unlock" only |

Why so: a fingerprint is **physically coercible** — someone else's finger can be pressed to the sensor by force. A PIN cannot. That is why every operation capable of causing damage requires exactly the PIN, and every PIN entry screen is also an entry point into decoy mode (below).

Fingerprint sign-in is only a convenience for unlocking the interface; while the duress PIN is enabled, it is disabled completely.

## The duress PIN and decoy mode

The threat: you are being forced to open the app or send units.

During setup you set two PINs: the **ordinary** one and the **duress** one. The duress PIN opens **decoy mode**:

- the interface looks exactly the same, but shows a plausible **small balance** and history (showing zero is not an option — an active wallet regularly receives the issuance, and a zero balance would look suspicious);
- "transfers" from the decoy end with a plausible "awaiting confirmation" or a network error — no real transactions are published;
- the real wallet keeps working in the background;
- notifications contain no amounts: the app has no operation notifications; the only system notification is the node's foreground service ("The trust network node is running"), with no amounts or addresses;
- "guardian re-election" in the decoy plausibly "executes", but the real guardian list is untouched.

The two PINs are **indistinguishable**: the same opening time, the same interface, the same attempt limit. The duress PIN works on **any** PIN entry screen — a transfer, issuance, changing settings.

**You can hide it, you cannot zero it out:** the balance is the network's public state, and the key is not deleted. The local database can be deleted with the system's regular means — it will restore itself during reconciliation with the network.

## Delayed large transfers — the second layer

A transfer above the threshold (3000 units by default) executes after **48 hours**; at any moment before execution it can be canceled. The coercer gets "the transfer has been sent" instead of the units; you cancel it as soon as you are safe. The delay is fixed and cannot be swit
ched off.

## What the protection does not do (read honestly)

- **A public registry.** Anyone you have paid or received from knows your address; the history is public, and the balance is derivable from the network's state (the app's registry shows the address, status, and age; the balance — on the wallet and via a checkpoint's Merkle proof). The decoy is verifiable: its address will not match the real one on the network.
- **Against a prepared attacker the decoy is not guaranteed.** It works against quick coercion and robbery.
- **Against the theft of an unlocked phone** you are protected by the "signature on every operation": units cannot be spent just by having the phone in hand.
- **Against the loss of a phone** — guardians and migration (the [Recovery](03-operations.md#access-recovery) section). Without guardians the funds are lost.
- **A thief who knows your PIN can cancel the migration** within the 14-day window — a known v1 limitation: the right to cancel belongs to the old key. Mitigations — public guardians and restarting the migration.

## The safe-setup checklist

1. Set the PIN and the duress PIN at first launch.
2. Assign guardians (2 of 3 personal or 3 of 5 public) — immediately, at wallet creation.
3. Fill out the recovery card (the [Recovery](03-operations.md#recovery-card--fill-it-out-in-advance) section): the wallet's address, the guardians' addresses, the network's name — write them down and keep them off the phone. Do not hand the migration data (the nonce, the guardians' signatures) to anyone and do not publish them.
4. Do not tell anyone your PIN; the duress one — even more so (nobody should know it exists).
5. Remember: adding a new fingerprint in the system invalidates the key — that is protection against substitution, but also your risk of losing access.
6. Do not keep large sums "just in case" — demurrage in currency networks penalizes exactly that: holding.

→ Next: [FAQ and glossary](05-faq-glossary.md)
