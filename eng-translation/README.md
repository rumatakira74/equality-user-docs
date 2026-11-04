# Equality Project — user documentation

**Equality Project** is a platform on which a community launches its **isolated trust network** on the members' phones: no servers, no administrator, and no operating costs.

**DOI:** [10.5281/zenodo.23558900](https://doi.org/10.5281/zenodo.23558900)

> **Status: test version (pre-release).** The app has been fully validated in the test network on emulators. The verification on live phones and the first pilots — ahead. The documentation describes the product's operation per specification v9.16 / protocol_version 3 (including guardian re-election `update_guardians`: a 48 h window, a limit of 150 effective changes; the eighth scenario — a subscription resource: subscription networks with periodic quotas and burning).

> **Languages.** The documentation is available in Russian (the original, `docs/`) and in translations:
> [this directory](.) — English. The app's interface languages —
> ru, en, es, pt, zh (`app/lib/l10n` of the main repository).

© 2026 Kirill Lapchinsky · rumatakira74@gmail.com · Telegram [@rumatakira](https://t.me/rumatakira)

## Contents

1. [About the platform](docs/01-about.md) — what it is, who needs it, the eight scenarios, the roles
2. [Getting started](docs/02-getting-started.md) — installation, wallet creation, vouches, sign-in
3. [Daily operations](docs/03-operations.md) — issuance, transfers, the fee, demurrage, recovery
4. [Owner security](docs/04-security.md) — PIN and biometrics, the duress PIN, the limits of the protection
5. [Questions and answers, glossary](docs/05-faq-glossary.md)

## Other repositories of the project

- [equality-trust-networks](https://github.com/rumatakira74/equality-trust-networks) — the platform's source code and specification
- [equality-programming-docs](https://github.com/rumatakira74/equality-programming-docs) — the documentation for programmers
- [equality-anti-farm-simulation](https://github.com/rumatakira74/equality-anti-farm-simulation) — the model of the farm economy (the justification of the parameters)

## Disclaimer

The project is in pre-release status; the boundaries of the warranties and liability are described in [DISCLAIMER.md](DISCLAIMER.md) (Russian and English).

## License

The source code is open for **non-commercial use**; commercial use and commercial derivative works — under a paid license (the terms — in the specification, section 16).

The license text: [LICENSE](../LICENSE) (the Russian original, legally governing) · [LICENSE-ENG.md](../LICENSE-ENG.md) (an unofficial English translation).
