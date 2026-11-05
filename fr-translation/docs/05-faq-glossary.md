# 5. Questions et réponses · Glossaire

## FAQ

**Faut-il internet ?**
Pour les opérations ordinaires — oui, une liaison au moins périodique. Bluetooth permet de transmettre directement au destinataire la transaction signée, mais le paiement n'aura lieu qu'après la publication et la confirmation par le réseau.

**Je n'ai pas de connaissances dans le réseau. Comment m'activer ?**
Via les canaux publics de la communauté : c'est là que les débutants trouvent des garants. Le parrain répond de son choix par un emplacement limité et par la récompense ; distribuer des parrainages à tout venant ne lui rapporte rien. Le parrainage peut être formalisé en personne via QR ou Bluetooth.

**J'ai perdu mon téléphone. Qu'en est-il des unités ?**
La clé est non exportable, mais la récupération sociale fonctionne : les gardiens (personnels 2 sur 3 ou publics 3 sur 5) confirment la migration vers le nouveau téléphone ; après 14 jours, l'âge, l'histoire, les parrainages et les fonds sont transférés. Sans gardiens assignés — uniquement un nouvel enregistrement, et les fonds de l'ancien portefeuille sont perdus.

**Peut-on changer de gardiens ?**
Oui. Si le gardien a disparu, est mort ou a quitté le réseau, réélisez-le : les nouveaux gardiens signent en personne le hash du changement, le changement est publié avec saisie explicite du PIN et entre en vigueur après 48 heures (avant cela, on peut l'annuler). Limite — 150 changements entrés en vigueur pendant la vie du portefeuille. En détail — [« Changement de gardiens »](03-operations.md#changement-de-gardiens).

**J'ai oublié les deux PIN.**
Le portefeuille devient inaccessible : la clé ne peut être extraite, le PIN ne peut être « réinitialisé par courriel » — de tels canaux n'existent pas dans un système sans serveurs. Le seul chemin — la migration via les gardiens.

**Quelqu'un peut-il falsifier mon portefeuille ?**
La clé est dans l'enclave sécurisée du téléphone ; seule elle peut signer une opération. La falsification est impossible sans accès physique à un appareil déverrouillé.

**Et si quelqu'un créait des centaines de portefeuilles (une ferme) ?**
Barrières : 3 parrainages par portefeuille (emplacements limités), attestation matérielle (les émulateurs et les appareils rootés ne passent pas, la chaîne d'attestation est liée à la clé enregistrée), défi calculatoire dans le créneau de la période en cours, moratoire, frais et demurrage. Modèle de l'économie des fermes : à l'estimation canonique de 120 $ par appareil, une ferme ne devient rentable pas avant ~3,5 ans (à 200 $ — après ~4,5 ans) et seulement avec une forte valeur externe de l'unité ; plusieurs portefeuilles sur un même appareil rendent la ferme moins chère — la robustesse de la conclusion a été vérifiée par une grille de sensibilité (coût de l'appareil × nombre de portefeuilles par appareil). Horizon de vérification de la métrique de sécurité — au moins 5 ans. Personne ne garantit « une personne — un portefeuille » : la protection est économique.

**Pourquoi le solde a-t-il diminué tout seul ?**
Dans les réseaux à monnaie fonctionne le demurrage — un petit pourcentage mensuel au-dessus du minimum non imposable. Il se reflète lors de l'opération suivante ; il n'y a pas de transaction de prélèvement séparée.

**Le transfert « est bloqué » pendant 48 heures. Est-ce un piratage ?**
Non, c'est un transfert différé : un montant au-dessus du seuil (par défaut 3000) s'exécute toujours après 48 heures, et on peut l'annuler avant l'exécution.

**Peut-on voter secrètement au sein du réseau ?**
En v1 — non : l'identifiant pour l'application tierce est publiquement lié à l'adresse. Les votes secrets ne seront possibles que dans les versions futures.

**L'application écrit « l'unité s'est éteinte ». Qu'est-ce que cela signifie ?**
Vous êtes dans un réseau d'abonnement (recurring) : le quota est lié à la période, et après la limite de la période suivante, on ne peut plus le transférer. Ce n'est ni une amende ni une perte de solde — un nouveau quota arrive dans la nouvelle période ; il vaut mieux donner l'excédent via peer-redeem à ceux qui ont besoin de la ressource.

**Combien coûte la participation ?**
Le réseau ne prend pas de frais de participation. Il n'y a aucun frais d'exploitation — les serveurs n'existent pas. Les frais de transfert sont brûlés et ne reviennent à personne.

## Glossaire

| Terme | Signification |
|-------|---------------|
| **Portefeuille** | Le compte du membre : adresse + chaîne d'enregistrements signés + solde. Un par appareil. |
| **Registre** | Le journal public de toutes les transactions du réseau ; chaque nœud le conserve et le vérifie. |
| **Genesis** | Le paquet de lancement du réseau : paramètres, manifeste, cercle initial. |
| **Version du protocole (protocolVersion)** | Le numéro de version des règles du réseau (actuellement — 3). Consigné dans chaque transaction et chaque checkpoint ; l'application et le réseau doivent correspondre par la version du protocole — une version d'une autre version n'est pas acceptée par le réseau. |
| **Manifeste** | La description publique des règles du réseau ; son hash est fixé dans le genesis. |
| **Cercle initial** | Les premiers membres du genesis avec des droits spéciaux temporaires ; les droits s'autoliquident (seed_sunset : 100 portefeuilles actifs ou 24 époques). |
| **Parrainage (vouch)** | La garantie signée d'un membre actif pour un nouveau. Trois d'entre elles activent le portefeuille. |
| **Emplacement de parrainage** | La place limitée du parrain ; se libère après 3 périodes d'émission du filleul ou 90 jours. |
| **Défi d'émission** | Tâche calculatoire (PoW) dans le créneau de la période en cours, calculable à l'avance ; fenêtre ±48 h disponible à chaque période, son état est affiché sur l'écran d'émission ; une omission est compensée dans les limites de la fenêtre d'accumulation (6 périodes). |
| **Époque** | L'intervalle du temps réseau (par défaut 24 heures) ; des checkpoints sont posés aux limites des époques. |
| **Checkpoint** | L'instantané de l'état du réseau signé par un seuil de membres ; il donne la finalité et la protection des nœuds légers. |
| **Finalité** | Le moment après lequel une transaction ne peut plus être annulée. |
| **Moratoire** | La période après l'enregistrement (par défaut 14 jours) où les transferts sortants sont indisponibles. |
| **Demurrage** | Un petit pourcentage mensuel de détention au-dessus du minimum ; ce qui est prélevé est brûlé. |
| **Leurre** | Le mode ouvert par le PIN de contrainte : une interface plausible avec un petit solde, aucune opération réelle. |
| **Gardien** | Le membre assigné pour confirmer la migration en cas de perte du téléphone. |
| **Migration** | Le transfert du portefeuille vers un nouvel appareil via les gardiens ; délai de 14 jours. |
| **Changement de gardiens** | La réélection des gardiens personnels (jusqu'à 3) avec leur consentement ; fenêtre de 48 h, limite de 150 changements entrés en vigueur pendant la vie du portefeuille. |
| **Flagged** | La marque publique d'une violation prouvée (équivocation). |
| **Paiement BT** | La transmission de la transaction signée par Bluetooth ; elle ne devient un paiement qu'après confirmation par le réseau. |
| **Profil du réseau** | L'ensemble des paramètres : unité, émission, transfert, extinction, entrée, etc. |
| **Eq-hash (`Eq-<hash8>`)** | L'étiquette courte du réseau (les 8 premiers caractères de son identifiant) ; visible dans le nom de l'application et à l'onboarding — c'est par elle qu'on vérifie que le bon réseau est installé. |
| **Recurring (réseau d'abonnement)** | Le réseau de ressource d'abonnement : quota égal par période, le non-utilisé s'éteint à la limite de la période. |
| **Peer-redeem** | Le transfert membre → membre ou membre → fournisseur dans les réseaux recurring : l'excédent de quotas s'écoule vers ceux qui ont besoin de la ressource (pas encore implémenté dans l'interface actuelle de l'application). |
| **Extinction du quota** | L'unité de la période précédente cesse d'être transférable après la limite de la période suivante ; le solde et l'histoire sont conservés. |

---

[← À propos de la plateforme](01-about.md) · [Sommaire](../README.md)
