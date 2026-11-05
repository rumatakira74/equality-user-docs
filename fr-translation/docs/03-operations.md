# 3. Opérations quotidiennes

## Émission

Dans les réseaux à émission périodique, chaque membre actif reçoit une fois par période (par défaut — chaque mois) sa **part égale** : par exemple, 1000 unités le 1er du mois.

Particularités :

- **Le défi d'émission.** Pour déclarer l'émission, l'application résout une tâche calculatoire dans **son créneau de la période en cours** (fenêtre de ±48 heures). Le moment du créneau est calculé à l'avance à partir de l'adresse et de la période, et il est identique pour tous les nœuds ; le créneau se trouve à l'intérieur de sa propre période, donc la fenêtre **est disponible à chaque période** (après la correction du mint — v9.14 : auparavant, la fenêtre pouvait tomber sur un moment inaccessible, et le portefeuille, après six périodes manquées consécutives, perdait l'émission pour toujours). L'état de la fenêtre est affiché sur l'écran d'émission (« ouverte — on peut émettre » / « fermée — quand s'ouvrira-t-elle »). La période manquée n'est pas perdue : l'apport est reporté dans les limites de la **fenêtre d'accumulation — 6 périodes**, les fonds ne sont pas bloqués ; un saut conscient au-delà de la fenêtre — l'émission s'éteint.
- La première émission n'est possible que dans la période **postérieure** à l'activation, sans reports rétroactifs.
- Les fonds tout juste émis ne sont transférables immédiatement (moratoire — voir plus bas).

## Transferts

- **Les frais sont brûlés.** Chaque transfert paie de petits frais (`fee`) qui sont détruits — le destinataire reçoit exactement le montant indiqué. Les frais protègent le réseau contre le spam et freinent légèrement le mouvement de la valeur.
- **Le tarif est adaptatif.** Le pourcentage des frais est recalculé par le réseau à la limite de chaque époque, identiquement pour tous les nœuds : si l'offre d'unités croît plus vite que le rythme cible — le tarif monte, sinon il baisse. Fourchette — de 0,5 % à 2 %, minimum 0,01 unité ; personne ne peut fixer le tarif manuellement.
- **Moratoire pour les portefeuilles récents :** les transferts deviennent disponibles 14 jours après l'enregistrement (paramètre du réseau ; 14 jours — la valeur par défaut). Cela coupe le schéma « enregistré — vidé ».
- **Le moment de la transaction, c'est le moment de la signature.** Les règles du réseau (moratoire, extinction des quotas, délais des transferts différés, fenêtre d'émission) s'appliquent au moment de la signature de la transaction, et non au moment de sa publication : un transfert signé hors ligne et publié plus tard est évalué identiquement par tous les nœuds. L'horloge du téléphone ne doit pas diverger du réseau de plus de ±30 minutes — les transactions avec un écart plus grand ne sont pas acceptées par le réseau (répétez la publication après la synchronisation de l'heure).
- **Transferts importants différés.** Un transfert au-dessus du seuil (par défaut **P = 3000 unités**) n'est exécuté qu'après **48 heures**. Pendant le délai, vous pouvez l'annuler directement depuis l'application — par exemple, sous la contrainte ou si vous changez d'avis. La règle vaut dans tous les réseaux à unités transférables et ne se désactive pas. Le seuil peut être modifié dans les limites du maximum (30000) ; l'augmentation entre en vigueur après 48 heures, la diminution — immédiatement.

### Réseaux d'abonnement (recurring) : quotas par période

Dans les réseaux de ressource d'abonnement (scénario 8), les unités sont des **quotas par période** : chaque membre actif reçoit un quota égal, et la partie non utilisée **s'éteint à la limite de la période suivante** — ainsi l'abonnement ne se transforme pas en thésaurisation. Transférer ou rembourser une unité de la période précédente après cette limite est impossible : l'application affichera une erreur compréhensible « l'unité s'est éteinte ». Personne ne « remet » le solde à zéro pour autant — l'histoire reste visible de tous ; simplement, les anciens quotas ne se transfèrent plus.

L'excédent peut être transmis à ceux à qui les quotas manquent : des transferts **membre → membre** et **membre → fournisseur** (mode peer-redeem ; la confirmation — un reçu signé). Remarque : le mode est pris en charge par le cœur et la spécification, mais il n'est pas encore implémenté dans l'interface actuelle de l'application.

### Paiement Bluetooth

Bluetooth est utilisé **uniquement** pour transmettre directement au destinataire la transaction signée, quand il n'y a pas d'internet. Le destinataire publie la transaction dans le réseau dès que la liaison réapparaît.

**Important :** tant que la transaction n'est pas publiée et confirmée par le réseau, elle **ne constitue pas un paiement**. L'expéditeur peut remettre la même somme à deux destinataires. C'est pourquoi, dans l'interface, le statut est « reçu par Bluetooth — en attente de publication », et le destinataire est tenu d'attendre la confirmation du réseau.

## Demurrage (dans les réseaux à monnaie)

Dans les profils à valeur transférable (monnaie interne, caisse d'entraide), peut fonctionner le **demurrage** — un petit « impôt de détention » mensuel au-dessus du minimum non imposable. Le prélèvement ne passe pas par une transaction séparée : le solde effectif est recalculé de manière déterministe lors de l'opération suivante.

Le sens : la valeur est dans le flux, pas dans l'accumulation. Le demurrage et les frais brûlés font partie de la protection contre les fermes, pas un moyen de prendre des unités : on peut « contourner » le demurrage simplement en ne thésaurisant pas.

## Parrainages

- Le parrain garantit pour un nouveau membre en dépensant l'un de ses **emplacements** (3 pour une ancienneté de 3 à 12 mois, 5 — au-delà).
- L'emplacement se libère quand le filleul a effectué 3 périodes d'émission sans violation, soit après 90 jours s'il ne s'est jamais activé.
- La récompense des parrains — **10 % des 12 premières émissions** du filleul, automatiquement et à parts égales entre les trois.
- Si une violation est prouvée contre le filleul, la récompense cesse ; on ne retire pas d'argent au parrain.

## Violations et la marque flagged

La seule violation démontrable est **l'équivocation** : deux transactions conflictuelles signées par le même portefeuille (double dépense, double émission). La preuve est publiée par n'importe quel nœud, tous la vérifient identiquement. Conséquences : marque publique `flagged`, suspension de l'émission pendant 3 mois (en cas de répétition — pour toujours), interdiction de garantir. « Ressemble à une ferme » n'est pas une preuve — aucun verdict sur des soupçons.

## Récupération de l'accès

La clé est non exportable ; c'est pourquoi, en cas de perte du téléphone, fonctionne la **récupération sociale** (transaction `migrate`) :

1. Le nouveau téléphone passe la même vérification que lors de l'enregistrement.
2. Les gardiens confirment la migration : **personnels 2 sur 3** ou **publics 3 sur 5** (combinaison possible).
3. **Délai de 14 jours**, pendant lequel l'ancienne clé (si elle est vivante) peut annuler la migration.
4. L'âge, l'histoire, les parrainages, les émissions **et les fonds (le solde)** sont transférés sur le nouveau portefeuille ; l'ancienne empreinte finit définitivement dans la liste noire.

### Carte de récupération — remplissez-la à l'avance

Pour lancer la migration, il faudra, sur le nouveau téléphone, saisir **l'ancienne adresse du portefeuille**, puis le nonce et les signatures des gardiens. Ces données ne se « restaurent pas de rien » : sur le téléphone perdu, elles ne se sont pas conservées.

**À l'avance, tant que le téléphone est vivant :**

- notez **l'adresse de votre portefeuille** (hex, affichée dans l'application) et conservez-la hors du téléphone (pas dans le cloud) — sur papier ou sous forme de QR-code imprimé ;
- notez **les adresses de vos gardiens** et le moyen de les contacter ;
- notez **le nom du réseau** (l'application l'affiche avec l'étiquette `Eq-<hash8>`) et où prendre son APK (chaque réseau distribue sa propre version).

L'application affiche toutes ces données sur l'écran **« Carte de récupération »** à la création du portefeuille (et plus tard — dans les réglages et sur l'écran de migration) avec un code QR : exportez-les ou imprimez-les.

**Pendant la migration :**

- le nonce et les signatures des gardiens sont les clés de la récupération de votre portefeuille : **ne les transmettez à personne et ne les publiez pas** ;
- transmettez-les **uniquement en direct** entre vous et votre gardien — en personne ou via un canal sécurisé, pas via des tiers ;
- saisissez-les uniquement dans votre propre application ; après la fin de la migration, supprimez-les des correspondances.

Un gardien public (membre ayant ≥ 12 mois d'ancienneté) reçoit, pour une migration réussie de son pupille, une récompense fixe prélevée sur l'émission — pas plus d'une fois tous les 12 mois par pupille.

**Si les gardiens ne sont pas assignés**, il reste la réinitialisation : un nouvel enregistrement avec une nouvelle clé et trois nouveaux parrainages. Les fonds de l'ancien portefeuille sont alors perdus — assignez les gardiens à l'avance.

### Changement de gardiens

Le gardien est mort, a disparu ou a quitté le réseau — les gardiens peuvent être **réélus** (transaction `update_guardians`) :

1. **Consentement des nouveaux gardiens.** Chaque nouveau gardien (jusqu'à 3) signe en personne le hash du changement — de la même manière que pour confirmer une migration : sans leur signature, le changement est impossible.
2. **Publication du changement.** Réglages → Gardiens → « Réélire » ; la publication et l'annulation — uniquement après saisie explicite du PIN.
3. **Fenêtre de 48 heures.** Le changement entre en vigueur 48 heures après la publication ; jusque-là, il peut être annulé (également uniquement avec le PIN).
4. **Limite — 150 changements.** Pas plus de 150 changements entrés en vigueur pendant la vie du portefeuille ; les annulés et expirés ne comptent pas. Le compteur des changements restants est visible dans l'application.

Aucun frais pour le changement ; chaque changement est publié dans l'histoire du réseau. Les nouveaux gardiens doivent être actifs (`active`) et sans la marque `flagged`. En mode leurre, le « changement de gardiens » s'exécute de manière plausible, mais la liste réelle des gardiens n'est pas touchée.

→ Ensuite : [Sécurité du propriétaire](04-security.md)
