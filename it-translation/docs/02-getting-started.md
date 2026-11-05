# 2. Primi passi

> **Stato: versione di prova.** L'applicazione è stata verificata in una rete di test chiusa su emulatori. La build pubblica e la pubblicazione negli store — dopo i piloti. Tutti i passi sotto descrivono il percorso di onboarding completo.

## Cosa serve

- Uno smartphone Android con un archivio protetto hardware per le chiavi (StrongBox / TEE) e un'impronta digitale configurata.
- Un dispositivo senza biometria configurata non è ammesso alla registrazione: l'applicazione proporrà di configurare la biometria tramite la schermata di sistema.
- Conoscenti nella rete: per attivare il portafoglio servono **3 avalli** di partecipanti attivi (vedi sotto).

## Installazione

L'applicazione si distribuisce come APK (la sezione sulla distribuzione tramite Google Play — in verifica giuridica). Installate il file APK della vostra rete: ogni rete-istanza può distribuire una propria build con parametri incorporati. L'applicazione della rete è firmata con il nome della rete e l'etichetta `Eq-<hash8>` — verificate l'etichetta all'installazione, per non installare una rete altrui. L'applicazione e la rete devono coincidere per la **versione del protocollo** (attuale — 3): il numero è registrato in ogni transazione e checkpoint; una build di un'altra versione non è accettata dalla rete.

L'interfaccia dell'applicazione è disponibile in nove lingue: russo, inglese, spagnolo, portoghese, cinese, francese, tedesco, italiano, giapponese.

## Creazione del portafoglio

1. L'applicazione crea la coppia di chiavi **all'interno dell'archivio protetto del telefono (Keystore)**. La chiave privata non è esportabile: non si può copiare, esportare o inoltrare — mai.
2. Il telefono passa un'**attestazione hardware**: la rete verifica che si tratta di un dispositivo reale con avvio immutato e hardware protetto, e che la catena di attestazione sia emessa proprio per la vostra nuova chiave (il legame della chiave al certificato — ogni nodo della rete lo verifica da sé; una catena altrui non è sostituibile). L'immagine del dito non viene trasmessa da nessuna parte.
3. Si esegue un compito computazionale (proof-of-work) — protezione dalla registrazione automatica di massa. Richiede pochi secondi.
4. Il portafoglio riceve lo stato **registered** — può già ricevere trasferimenti, ma emissione e invio non sono ancora disponibili.

Una persona ≈ un portafoglio: una registrazione ripetuta dallo stesso dispositivo è **resi difficile** — richiede un lavoro computazionale (PoW) notevolmente più costoso, e una garanzia hardware rigorosa «un dispositivo — un portafoglio» non esiste.

## Gli avalli: la via allo stato attivo

Per il pieno funzionamento il portafoglio deve diventare **active**. Per questo servono **K = 3 avalli** (`vouch`) da parte di partecipanti attivi diversi.

**Chi può avallare:**

- un partecipante con lo stato `active` e un'età del portafoglio di almeno 3 mesi;
- con slot di avallo liberi (sono pochi: 3–5 a seconda dell'anzianità);
- l'avallo si può formalizzare di persona tramite codice QR o Bluetooth.

**Cosa significa un avallo.** L'avallante rischia solo il proprio slot e la propria quota di ricompensa; la perdita di unità non lo minaccia. Per un principiante onesto l'avallante riceve **il 10% delle prime 12 emissioni** dell'avallato (pagata dall'emissione del principiante stesso, non dal nulla). Se il principiante è colto in violazione — l'avallante perde la ricompensa.

**Se non avete conoscenti nella rete:** usate i canali pubblici della comunità, dove i principianti trovano avallanti. L'avallante risponde della scelta con uno slot limitato — «distribuire» avalli a chiunque non gli conviene.

## Primo accesso e PIN

Durante la configurazione scegliete:

- il **PIN** — il mezzo principale per confermare le operazioni pericolose;
- se lo desiderate — il **PIN di coercizione** (vedi [Sicurezza](04-security.md));
- l'accesso all'applicazione — con impronta o PIN.

Regole chiave di sicurezza:

- **L'accesso** all'applicazione — impronta o PIN.
- **Le operazioni pericolose** (trasferimento, emissione, avvio della migrazione) — **solo inserimento esplicito del PIN**. L'impronta per confermarle non si usa mai: un dito si può applicare con la forza, un PIN no.
- Se il PIN di coercizione è attivato, l'accesso con impronta viene disattivato.

L'aggiunta di una nuova impronta nel sistema **invalida la chiave** (più sicuro, ma significa la perdita dell'accesso) — perciò designate subito i guardiani.

## I guardiani: designateli subito

Designate i guardiani **alla creazione del portafoglio**, non quando il telefono è già annegato:

- **guardiani personali** — 2 persone su 3 a scelta;
- oppure **guardiani pubblici** — partecipanti verificati con un'anzianità di almeno 12 mesi; soglia 3 su 5 (combinabile).

Il guardiano è morto, è scomparso o è uscito dalla rete? I guardiani si possono **rieleggere più tardi** — con il consenso dei nuovi (finestra di 48 ore, limite di 150 cambi entrati in vigore). Come — nella sezione [«Cambio dei guardiani»](03-operations.md#cambio-dei-guardiani). Non rimandate la designazione in sé: senza guardiani il recupero è impossibile.

In dettaglio — nella sezione [Recupero](03-operations.md#recupero-dellaccesso).

E compilate subito la **scheda di recupero** (vedi [Recupero](03-operations.md#scheda-di-recupero--compilatela-in-anticipo)): l'indirizzo del vostro portafoglio, gli indirizzi dei vostri guardiani e il nome della rete — annotateli e conservateli fuori dal telefono. Se perdete il telefono, questi dati non ci sarà più modo di ricavarli. L'applicazione li mostra nella schermata «Scheda di recupero» con codice QR.

## Gli stati del portafoglio

| Stato | Come si ottiene | Cosa si può fare |
|-------|-----------------|------------------|
| `registered` | dopo la registrazione (attestazione + PoW) | ricevere trasferimenti |
| `active` | 3 avalli | emissione, trasferimenti, avalli |
| `expired` | 3 anni in registered senza attivazione | i trasferimenti all'indirizzo si conservano; per l'emissione serve una nuova registrazione |
| l'etichetta `flagged` | violazione provata (doppia firma) | emissione sospesa, avallare per altri vietato |

→ Avanti: [Operazioni quotidiane](03-operations.md)
