# 2. Getting started

> **Status: test version.** The app has been validated in a closed test network on emulators. A public build and app-store publication — after the pilots. All the steps below describe the full onboarding path.

## What you need

- An Android smartphone with a hardware-protected key store (StrongBox / TEE) and a configured fingerprint.
- A device without configured biometrics is not admitted to registration: the app will offer to set up biometrics through the system screen.
- Acquaintances in the network: activating a wallet takes **3 vouches** from existing members (see below).

## Installation

The app is distributed as an APK (the section on distribution through Google Play — under legal review). Install the APK file of your network: each network instance may distribute its own build with the parameters baked in. A network's app is signed with the network's name and the `Eq-<hash8>` label — check the label at installation so as not to install someone else's network. The app and the network must match on the **protocol version** (currently 3): the number is written in every transaction and checkpoint, and a build of a different version is not accepted by the network.

The app's interface is available in five languages: Russian, English, Spanish, Portuguese, Chinese.

## Creating a wallet

1. The app creates the key pair **inside the phone's protected storage (Keystore)**. The private key is non-exportable: it cannot be copied, exported, or forwarded — ever.
2. The phone goes through **hardware attestation**: the network verifies that this is a real device with unmodified boot and protected hardware, and that the attestation chain was issued specifically for your new key (the key is bound to the certificate — every node of the network verifies it itself; nobody can substitute someone else's chain). The fingerprint image is not transmitted anywhere.
3. A computational task (proof-of-work) is performed — protection against mass automated registration. It takes seconds.
4. The wallet gets the status **registered** — it can already receive transfers, but issuance and sending are not yet available.

One person ≈ one wallet: re-registering from the same device is **made difficult** — it requires substantially more expensive computational work (PoW), and there is no strict hardware guarantee of "one device — one wallet".

## Vouches: the path to active status

For full operation the wallet must become **active**. For that it needs **K = 3 vouches** (`vouch`) from different active members.

**Who can vouch:**

- a member with the `active` status and a wallet age of 3 months or more;
- one who has free vouching slots (there are few of them: 3–5 depending on standing);
- a vouch can be arranged in person via a QR code or Bluetooth.

**Wh
at a vouch means.** The vouching member risks only their slot and their share of the reward; losing units is not something they face. For an honest newcomer the vouching member receives **10% of the first 12 issuances** of the vouched-for member (paid out of the newcomer's own issuance, not out of thin air). If the newcomer is found in violation — the vouching member loses the reward.

**If you have no acquaintances in the network:** use the community's public channels, where newcomers find vouching members. The vouching member answers for their choice with a limited slot — "handing out" vouches to just anyone is against their own interest.

## First sign-in and the PIN

During setup you choose:

- a **PIN** — the main way to confirm dangerous operations;
- optionally — a **duress PIN** (see [Security](04-security.md));
- signing in to the app — by fingerprint or PIN.

The key security rules:

- **Sign-in** to the app — fingerprint or PIN.
- **Dangerous operations** (a transfer, issuance, starting a migration) — **explicit PIN entry only**. A fingerprint is never used to confirm them: a finger can be applied by force, a PIN cannot.
- If the duress PIN is enabled, fingerprint sign-in is disabled.

Adding a new fingerprint in the system **invalidates the key** (safer, but it means losing access) — so assign guardians right away.

## Guardians: assign them right away

Assign guardians **when you create the wallet**, not when the phone is already drowned:

- **personal guardians** — 2 of 3 people of your choice;
- or **public guardians** — verified members with at least 12 months of standing; the threshold is 3 of 5 (you can combine).

Has a guardian died, disappeared, or left the network? Guardians can be **re-elected later** — with the consent of the new ones (a 48-hour window, a limit of 150 effective changes). How — in the section [Guardian re-election](03-operations.md#guardian-re-election). Do not postpone the assignment itself: without guardians, recovery is impossible.

In detail — in the section [Recovery](03-operations.md#access-recovery).

And immediately fill out the **recovery card** (see [Recovery](03-operations.md#recovery-card--fill-it-out-in-advance)): your wallet's address, the guardians' addresses, and the network's name — write them down and keep them off the phone. When the phone is lost, there will be nowhere to take this data from. The app shows it on the "Recovery card" screen with a QR code.

## Wallet statuses

| Status | How it is obtained | What is allowed |
|--------|--------------------|-----------------|
| `registered` | after registration (attestation + PoW) | receiving transfers |
| `active` | 3 vouches | issuance, transfers, vouching |
| `expired` | 3 years as registered without activation | transfers to the address keep arriving; issuance requires a new registration |
| the `flagged` mark | a proven violation (double signing) |
 issuance suspended, cannot vouch for others |

→ Next: [Daily operations](03-operations.md)
