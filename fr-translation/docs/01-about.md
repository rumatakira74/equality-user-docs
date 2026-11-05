# 1. À propos de la plateforme

## Ce que c'est

Equality Project est une plateforme sur laquelle une communauté (une école, une coopérative, un groupe de bénévoles, une diaspora, une fondation, un organisateur d'événement) lance **son propre réseau isolé** sur les téléphones de ses membres :

- **sans serveurs** — le réseau vit sur les téléphones eux-mêmes ;
- **sans administrateur** — personne ne peut « éteindre » le réseau ni modifier ses règles ;
- **sans frais d'exploitation** — il n'y a ni hébergement ni maintenance à payer.

Chaque réseau donne à ses membres trois choses :

1. **Une personne ≈ un portefeuille.** L'entrée passe uniquement par les parrainages de membres actifs, plus une vérification matérielle du téléphone. C'est la barrière principale contre les faux comptes.
2. **Un droit périodique égal.** « L'unité » du réseau (heures, quota, points) est émise pour tous les membres actifs **à parts égales**, selon un calendrier.
3. **Une histoire publique vérifiable.** La réputation d'un membre — l'âge du portefeuille, qui a garanti pour qui, la contribution — est visible de tous les membres du réseau.

Ce qu'il faut compter comme « unité » et ce qu'on peut en faire, c'est le **profil du réseau** qui le définit : monnaie interne, banque de temps, quotas sur une ressource commune, comptabilisation de la contribution bénévole, etc.

Le réseau s'assemble à partir d'un **modèle prêt à l'emploi** correspondant à l'un des huit scénarios : l'organisateur choisit le modèle, définit les paramètres — et obtient son réseau avec sa propre application (APK).

## Ce n'est pas une cryptomonnaie

- La plateforme **n'émet et ne vend aucun token**, ne crée pas de marché d'échange et ne récompense pas le minage au sens habituel.
- Les unités n'existent qu'à l'intérieur d'un réseau précis et, dans certains profils, ne se transfèrent pas du tout.
- La valeur est dans l'usage (voir les scénarios ci-dessous), pas dans un cours de l'unité.
- Les mots « portefeuille », « émission », « checkpoint » sont le vocabulaire technique du journal des enregistrements signés, et non le signe d'un instrument financier.

## Les huit scénarios d'usage

| № | Scénario | Unité |
|---|----------|-------|
| 1 | Enseignement et laboratoires d'instituts (simulations comprises) | points ou monnaie de jeu |
| 2 | Preuve d'humanité en tant que service pour d'autres applications | « pouls » d'activité non transférable |
| 3 | Quotas égaux sur une ressource commune (eau, internet, entrepôt) | quota par période, sans accumulation |
| 4 | Programmes bénévoles et de rue (repas, assistance) | bons du programme |
| 5 | Monnaie interne ou banque de temps de la communauté | heures ou monnaie, émission égale |
| 6 | Comptabilisation de la contribution bénévole | points pour une contribution confirmée |
| 7 | Caisse d'entraide | monnaie, demurrage contre l'accaparement |
| 8 | Ressource d'abonnement — abonnement à une ressource récurrente (commercial) | quota par période, le non-utilisé s'éteint |

## Les réseaux sont isolés, et c'est là la propriété principale

- Ce n'est pas un seul grand réseau, mais **beaucoup de réseaux séparés**. Chacun a sa composition, ses règles (son profil), ses unités.
- Entre les réseaux, il n'y a pas d'échange. Le solde d'un réseau ne signifie rien dans un autre.
- Les règles du réseau sont consignées dans le **manifeste** à la création et, par défaut, immuables ; le hash du manifeste est fixé dans le genesis. Si les règles cessent de convenir à la communauté — un nouveau réseau est lancé (c'est gratuit), et les membres passent volontairement.
- Le niveau de garanties du réseau **se calcule à partir du manifeste**, il n'est pas déclaré : les partenaires voient de quel réseau, et avec quelles garanties, arrive « la personne ».
- Chaque réseau est assemblé avec **sa propre application** : l'étiquette `Eq-<hash8>` (hash court de l'identifiant du réseau) dans le nom de l'application montre que c'est bien votre réseau qui est installée ; dans l'application, le réseau est signé par son nom et son étiquette — par exemple, « cirrus · Eq-e5796f9c ».
- Dans les réseaux d'abonnement (scénario 8), les quotas ne s'accumulent pas : la partie non utilisée s'éteint à la limite de la période, et l'excédent peut être transféré à ceux qui ont besoin de la ressource (plus de détails dans [Opérations quotidiennes](03-operations.md)).

## Les rôles des membres

Chaque rôle est un portefeuille ordinaire ; personne ne détient de « droits d'accès » particuliers :

- **Membre** — un portefeuille enregistré ; après l'activation, il reçoit l'émission et transfère des unités.
- **Parrain** — un membre actif ayant au moins 3 mois d'ancienneté, qui garantit pour une nouvelle personne avec l'un de ses emplacements de parrainage limités.
- **Gardien** — une personne désignée à l'avance pour restaurer l'accès en cas de perte du téléphone (gardiens personnels — 2 sur 3 ; ou publics — 3 sur 5).
- **Fournisseur / destinataire du fonds commun** — un portefeuille indiqué dans les paramètres du réseau (par exemple, un point partenaire acceptant les bons). Il ne peut pas administrer le réseau.

## Honnêtement sur les limites

- **Pas de smartphone adapté — pas de participation.** Le protocole exige un téléphone Android avec un enclave matérielle sécurisée pour les clés. Il n'existe pas de contournement (curateurs, reçus papier).
- **L'anonymat n'est pas le but.** Le registre du réseau est public à l'intérieur du réseau : les membres voient les adresses, les statuts et l'histoire les uns des autres ; le solde se déduit de l'état public du réseau.
- **La protection contre les fermes est économique, pas absolue.** Créer un portefeuille superflu doit coûter plus cher qu'il ne rapporte ; il est techniquement impossible de garantir pleinement « une personne — un portefeuille » sans ancre externe.

→ Ensuite : [Premiers pas](02-getting-started.md)
