# 2. Premiers pas

> **Statut : version d'essai.** L'application a été vérifiée sur un réseau de test fermé via des émulateurs. La version publique et la publication sur les magasins d'applications — après les pilotes. Toutes les étapes ci-dessous décrivent le parcours d'onboarding complet.

## Ce qu'il faut

- Un smartphone Android avec une enclave matérielle sécurisée pour les clés (StrongBox / TEE) et une empreinte digitale configurée.
- Un appareil sans biométrie configurée n'est pas admis à l'enregistrement : l'application proposera de configurer la biométrie via l'écran système.
- Des connaissances dans le réseau : pour activer le portefeuille, il faut **3 parrainages** de membres actifs (voir ci-dessous).

## Installation

L'application est distribuée sous forme d'APK (la section sur la distribution via Google Play est en cours de vérification juridique). Installez le fichier APK de votre réseau : chaque réseau-instance peut distribuer sa propre version avec des paramètres incorporés. L'application du réseau est signée par le nom du réseau et l'étiquette `Eq-<hash8>` — vérifiez l'étiquette lors de l'installation pour ne pas installer un réseau étranger. L'application et le réseau doivent correspondre par la **version du protocole** (actuellement — 3) : le numéro est consigné dans chaque transaction et chaque checkpoint ; une version d'une autre version n'est pas acceptée par le réseau.

L'interface de l'application est disponible en neuf langues : russe, anglais, espagnol, portugais, chinois, français, allemand, italien, japonais.

## Création du portefeuille

1. L'application crée la paire de clés **à l'intérieur de l'enclave sécurisée du téléphone (Keystore)**. La clé privée est non exportable : elle ne peut être ni copiée, ni exportée, ni transmise — jamais.
2. Le téléphone passe une **attestation matérielle** : le réseau vérifie qu'il s'agit d'un appareil réel au démarrage intact et au matériel sécurisé, et que la chaîne d'attestation est délivrée précisément pour votre nouvelle clé (liaison de la clé au certificat — chaque nœud du réseau la vérifie lui-même ; impossible de substituer une chaîne étrangère). L'image de l'empreinte n'est transmise nulle part.
3. Une tâche calculatoire (proof-of-work) est exécutée — protection contre l'enregistrement automatique massif. Cela prend quelques secondes.
4. Le portefeuille reçoit le statut **registered** — il peut déjà recevoir des transferts, mais l'émission et l'envoi ne sont pas encore disponibles.

Une personne ≈ un portefeuille : un enregistrement répété depuis le même appareil est **rendu difficile** — il exige un travail calculatoire (PoW) nettement plus coûteux, et il n'existe pas de garantie matérielle stricte « un appareil — un portefeuille ».

## Les parrainages : le chemin vers le statut actif

Pour travailler pleinement, le portefeuille doit devenir **actif**. Pour cela, il faut **K = 3 parrainages** (`vouch`) de membres actifs différents.

**Qui peut garantir :**

- un membre au statut `active` et dont le portefeuille a au moins 3 mois ;
- disposant d'emplacements de parrainage libres (ils sont peu nombreux : 3 à 5 selon l'ancienneté) ;
- le parrainage peut être formalisé en personne via un code QR ou Bluetooth.

**Ce que signifie un parrainage.** Le parrain ne risque que son emplacement et sa part de récompense ; la perte d'unités ne le menace pas. Pour un débutant honnête, le parrain reçoit **10 % des 12 premières émissions** du filleul (payées sur l'émission du débutant lui-même, pas de rien). Si le débutant est convaincu de violation — le parrain perd la récompense.

**Si vous n'avez pas de connaissances dans le réseau :** utilisez les canaux publics de la communauté, où les débutants trouvent des garants. Le parrain répond de son choix par un emplacement limité — « distribuer » des parrainages à tout venant ne lui rapporte rien.

## Première connexion et PIN

Lors de la configuration, vous choisissez :

- le **PIN** — le moyen principal de confirmer les opérations dangereuses ;
- si vous le souhaitez — le **PIN de contrainte** (voir [Sécurité](04-security.md)) ;
- la connexion à l'application — par empreinte ou PIN.

Règles de sécurité essentielles :

- **La connexion** à l'application — empreinte ou PIN.
- **Les opérations dangereuses** (transfert, émission, lancement de la migration) — **uniquement saisie explicite du PIN**. L'empreinte n'est jamais utilisée pour leur confirmation : on peut forcer un doigt sur le capteur, pas un PIN.
- Si le PIN de contrainte est activé, la connexion par empreinte est désactivée.

L'ajout d'une nouvelle empreinte dans le système **invalide la clé** (plus sûr, mais signifie la perte d'accès) — c'est pourquoi assignez tout de suite des gardiens.

## Les gardiens : assignez-les tout de suite

Assignez les gardiens **dès la création du portefeuille**, pas quand le téléphone est déjà noyé :

- **gardiens personnels** — 2 personnes sur 3 au choix ;
- ou **gardiens publics** — des membres vérifiés ayant au moins 12 mois d'ancienneté ; seuil 3 sur 5 (combinaison possible).

Un gardien est mort, a disparu ou a quitté le réseau ? Les gardiens peuvent être **réélus plus tard** — avec le consentement des nouveaux (fenêtre de 48 heures, limite de 150 changements entrés en vigueur). Comment faire — dans la section [« Changement de gardiens »](03-operations.md#changement-de-gardiens). Ne reportez pas l'assignation elle-même : sans gardiens, la récupération est impossible.

En détail — dans la section [Récupération](03-operations.md#récupération-de-laccès).

Et remplissez tout de suite la **carte de récupération** (voir [Récupération](03-operations.md#carte-de-récupération--remplissez-la-à-lavance)) : l'adresse de votre portefeuille, les adresses des gardiens et le nom du réseau — notez-les et conservez-les hors du téléphone. En cas de perte du téléphone, on ne saura plus où prendre ces données. L'application les affiche sur l'écran « Carte de récupération » avec un code QR.

## Les statuts du portefeuille

| Statut | Comment il s'obtient | Ce qu'on peut faire |
|--------|----------------------|---------------------|
| `registered` | après l'enregistrement (attestation + PoW) | recevoir des transferts |
| `active` | 3 parrainages | émission, transferts, parrainages |
| `expired` | 3 ans en registered sans activation | les transferts vers l'adresse sont conservés ; pour l'émission, un nouvel enregistrement est nécessaire |
| la marque `flagged` | violation prouvée (double signature) | émission suspendue, impossible de garantir pour autrui |

→ Ensuite : [Opérations quotidiennes](03-operations.md)
