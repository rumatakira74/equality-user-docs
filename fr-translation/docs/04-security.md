# 4. Sécurité du propriétaire

## PIN et biométrie : qui sert à quoi

| Action | Ce qui la confirme |
|--------|--------------------|
| Connexion à l'application | empreinte **ou** PIN |
| Transfert, émission, lancement de la migration | **uniquement saisie explicite du PIN** |
| Changement de gardiens (publication, annulation) | **uniquement saisie explicite du PIN** |
| Déverrouillage de la clé au sein de l'opération | biométrie après le PIN — uniquement « déverrouillage » |

Pourquoi ainsi : l'empreinte peut être **forcée physiquement** — appliquer le doigt de quelqu'un d'autre sur le capteur est possible par la force. Le PIN, non. C'est pourquoi chaque opération susceptible de causer un dommage exige précisément le PIN, et chaque écran de saisie du PIN est aussi un point d'entrée dans le mode leurre (plus bas).

La connexion par empreinte n'est qu'un confort de déverrouillage de l'interface ; avec le PIN de contrainte activé, elle est entièrement désactivée.

## PIN de contrainte et mode leurre

La menace : on vous force à ouvrir l'application ou à envoyer des unités.

Lors de la configuration, vous définissez deux PIN : **ordinaire** et **de contrainte**. Le PIN de contrainte ouvre le **mode leurre** :

- l'interface paraît exactement pareille, mais un **petit solde plausible** et un historique sont affichés (zéro afficher est impossible — un portefeuille actif reçoit régulièrement des émissions, un solde nul serait suspect) ;
- les « transferts » depuis le leurre se terminent par un plausible « en attente de confirmation » ou par une erreur réseau — les transactions réelles ne sont pas publiées ;
- le portefeuille réel continue de fonctionner en arrière-plan ;
- les notifications ne contiennent pas de montants : l'application n'a pas de notifications d'opérations ; la seule notification système est celle du service de premier plan du nœud (« Le nœud du réseau de confiance fonctionne »), sans montants ni adresses ;
- le « changement de gardiens » dans le leurre s'exécute de manière plausible, mais la liste réelle des gardiens n'est pas touchée.

Les deux PIN sont **indiscernables** : même temps d'ouverture, même interface, même limite de tentatives. Le PIN de contrainte s'applique sur **n'importe quel** écran de saisie du PIN — transfert, émission, modification des réglages.

**On peut cacher, on ne peut pas remettre à zéro :** le solde est un état public du réseau, la clé ne se supprime pas. La base locale peut être supprimée par les moyens ordinaires du système — elle se restaurera lors de la vérification avec le réseau.

## Transferts importants différés — deuxième couche

Un transfert au-dessus du seuil (par défaut 3000 unités) s'exécute après **48 heures** ; à tout moment avant l'exécution, on peut l'annuler. Celui qui vous contraint reçoit « transfert envoyé », et non les unités ; vous l'annulez dès que vous êtes en sécurité. Le délai est fixe et ne se désactive pas.

## Ce que la protection ne fait pas (lisez honnêtement)

- **Registre public.** Quiconque vous a payé ou de qui vous avez reçu connaît votre adresse ; l'histoire est publique, le solde se déduit de l'état du réseau (le registre de l'application montre l'adresse, le statut et l'âge ; le solde — sur le portefeuille et par la preuve Merkle du checkpoint). Le leurre se vérifie : l'adresse qu'il contient ne correspondra pas à la réelle sur le réseau.
- **Contre un attaquant préparé, le leurre n'est pas garanti.** Il fonctionne contre la contrainte rapide et le braquage.
- **Contre le vol d'un téléphone déverrouillé** protègent la signature « à chaque opération » : dépenser des unités en ayant simplement le téléphone en main est impossible.
- **Contre la perte du téléphone** — les gardiens et la migration (section [Récupération](03-operations.md#récupération-de-laccès)). Sans gardiens, les fonds se perdent.
- **Un voleur connaissant votre PIN peut annuler la migration** dans la fenêtre de 14 jours — limitation connue de la v1. Les atténuations — gardiens publics et relance de la migration.

## Liste de contrôle d'une configuration sûre

1. Définissez le PIN et le PIN de contrainte au premier lancement.
2. Assignez les gardiens (2 sur 3 personnels ou 3 sur 5 publics) — tout de suite, dès la création du portefeuille.
3. Remplissez la carte de récupération ([section « Récupération »](03-operations.md#carte-de-récupération--remplissez-la-à-lavance)) : l'adresse du portefeuille, les adresses des gardiens, le nom du réseau — notez-les et conservez-les hors du téléphone. Les données de migration (nonce, signatures des gardiens) ne les transmettez à personne et ne les publiez pas.
4. Ne dites votre PIN à personne ; le PIN de contrainte — encore moins (son existence même ne devrait pas être connue).
5. Rappelez-vous : l'ajout d'une nouvelle empreinte dans le système invalide la clé — c'est une protection contre la substitution, mais c'est aussi votre risque de perdre l'accès.
6. Ne gardez pas de grosses sommes « au cas où » — le demurrage dans les réseaux à monnaie pénalise précisément la thésaurisation.

→ Ensuite : [FAQ et glossaire](05-faq-glossary.md)
