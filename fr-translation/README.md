# Equality Project — documentation utilisateur

**Equality Project** est une plateforme sur laquelle une communauté lance **son propre réseau de confiance isolé** sur les téléphones de ses membres : sans serveurs, sans administrateur et sans frais d'exploitation.

**DOI :** [10.5281/zenodo.23558900](https://doi.org/10.5281/zenodo.23558900)

> **Statut : version d'essai (pre-release).** L'application est entièrement vérifiée sur le réseau de test via des émulateurs. La vérification sur téléphones réels et les premiers pilotes restent à venir. La documentation décrit le fonctionnement du produit selon la spécification v9.16 / protocol_version 3 (y compris la réélection des gardiens `update_guardians` : fenêtre de 48 h, limite de 150 changements entrés en vigueur ; le huitième scénario — une ressource d'abonnement : des réseaux d'abonnement (recurring) avec quotas par période et extinction).

> **Langues.** La documentation est disponible en russe (l'original, `docs/`) et en traductions :
> [ce répertoire](.) — français. Les langues de l'interface de l'application —
> ru, en, es, pt, zh, fr, de, it, ja (`app/lib/l10n` du dépôt principal).

© 2026 Kirill Lapchinsky · rumatakira74@gmail.com · Telegram [@rumatakira](https://t.me/rumatakira)

## Sommaire

1. [À propos de la plateforme](docs/01-about.md) — ce que c'est, à qui cela s'adresse, les huit scénarios, les rôles
2. [Premiers pas](docs/02-getting-started.md) — installation, création du portefeuille, parrainages, connexion
3. [Opérations quotidiennes](docs/03-operations.md) — émission, transferts, frais, demurrage, récupération
4. [Sécurité du propriétaire](docs/04-security.md) — PIN et biométrie, PIN de contrainte, limites de la protection
5. [Questions et réponses, glossaire](docs/05-faq-glossary.md)

## Autres dépôts du projet

- [equality-trust-networks](https://github.com/rumatakira74/equality-trust-networks) — le code source et la spécification de la plateforme
- [equality-programming-docs](https://github.com/rumatakira74/equality-programming-docs) — la documentation pour les programmeurs
- [equality-anti-farm-simulation](https://github.com/rumatakira74/equality-anti-farm-simulation) — le modèle de l'économie des fermes (la justification des paramètres)

## Clause de non-responsabilité

Le projet est en statut de version préliminaire ; les limites des garanties et de la responsabilité sont décrites dans [DISCLAIMER.md](DISCLAIMER.md) (français et anglais).

## Licence

Le code source est ouvert pour **l'usage non commercial** ; l'usage commercial et les œuvres dérivées commerciales — sous une licence payante (les conditions — dans la spécification, section 16).

Le texte de la licence : [LICENSE](../LICENSE) (l'original russe, juridiquement prévalant) \
· [LICENSE-ENG.md](../LICENSE-ENG.md) (une traduction anglaise non officielle).
