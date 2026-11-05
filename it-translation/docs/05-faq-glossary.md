# 5. Domande e risposte · Glossario

## FAQ

**Serve internet?**
Per le operazioni ordinarie — sì, almeno una connessione periodica. Il Bluetooth permette di trasmettere direttamente al destinatario la transazione firmata, ma il pagamento avverrà solo dopo la pubblicazione e la conferma della rete.

**Non ho conoscenti nella rete. Come mi attivo?**
Tramite i canali pubblici della comunità: è lì che i principianti trovano avallanti. L'avallante risponde della scelta con uno slot limitato e con la ricompensa; distribuire avalli a chiunque non gli conviene. L'avallo lo si può formalizzare di persona tramite QR o Bluetooth.

**Ho perso il telefono. Che fine fanno le unità?**
La chiave non è esportabile, ma funziona il recupero sociale: i guardiani (personali 2 su 3 o pubblici 3 su 5) confermano la migrazione al nuovo telefono; dopo 14 giorni si trasferiscono età, storia, avalli e fondi. Senza guardiani designati — solo una nuova registrazione, e i fondi sul vecchio portafoglio si perdono.

**Si possono cambiare i guardiani?**
Sì. Se il guardiano è scomparso, è morto o è uscito dalla rete, rieleggetelo: i nuovi guardiani firmano di persona l'hash del cambio, il cambio si pubblica con inserimento esplicito del PIN ed entra in vigore dopo 48 ore (prima lo si può annullare). Limite — 150 cambi entrati in vigore durante la vita del portafoglio. In dettaglio — [«Cambio dei guardiani»](03-operations.md#cambio-dei-guardiani).

**Ho dimenticato entrambi i PIN.**
Il portafoglio diventa inaccessibile: la chiave non si può estrarre, il PIN non si può «ripristinare per posta» — tali canali in un sistema senza server non esistono. L'unica via — la migrazione tramite i guardiani.

**Qualcuno può falsificare il mio portafoglio?**
La chiave è nell'archivio protetto del telefono; solo essa può firmare un'operazione. La falsificazione è impossibile senza accesso fisico a un dispositivo sbloccato.

**E se qualcuno creasse centinaia di portafogli (una fattoria)?**
Barriere: 3 avalli per portafoglio (slot limitati), attestazione hardware (emulatori e dispositivi con root non passano, la catena di attestazione è legata alla chiave registrata), sfida computazionale nello slot del periodo in corso, moratoria, commissione e demurrage. Modello dell'economia delle fattorie: alla valutazione canonica di $120 per dispositivo una fattoria va in positivo non prima di ~3,5 anni (a $200 — dopo ~4,5 anni) e solo con un alto valore esterno dell'unità; più portafogli sullo stesso dispositivo rendono la fattoria meno costosa — la robustezza della conclusione è verificata con una griglia di sensibilità (costo del dispositivo × numero di portafogli per dispositivo). Orizzonte di verifica della metrica di sicurezza — non meno di 5 anni. La garanzia «una persona — un portafoglio» non la dà nessuno: la protezione è economica.

**Perché il saldo si è ridotto da solo?**
Nelle reti con valuta opera il demurrage — una piccola percentuale mensile oltre il minimo non imponibile. Si riflette alla successiva operazione; non c'è una transazione di storno separata.

**Il trasferimento «è bloccato» per 48 ore. È un attacco informatico?**
No, è un trasferimento differito: un importo sopra la soglia (per default 3000) si esegue sempre dopo 48 ore, e lo si può annullare prima dell'esecuzione.

**Si può votare segretamente all'interno della rete?**
Nella v1 — no: l'identificatore per l'applicazione di terzi è pubblicamente legato all'indirizzo. Le votazioni segrete saranno possibili solo nelle versioni future.

**L'applicazione scrive «l'unità si è estinta». Che significa?**
Siete in una rete in abbonamento (recurring): la quota è legata al periodo, e dopo il limite del periodo successivo trasferirla non si può più. Non è né una multa né una perdita di saldo — una nuova quota arriva nel nuovo periodo; l'eccedenza meglio darla via peer-redeem a chi ha bisogno della risorsa.

**Quanto costa partecipare?**
La rete non prende alcun compenso per la partecipazione. Costi operativi la piattaforma non ne ha affatto — i server non esistono. La commissione del trasferimento si brucia e non va a nessuno.

## Glossario

| Termine | Significato |
|---------|-------------|
| **Portafoglio** | Il conto del partecipante: indirizzo + catena di registrazioni firmate + saldo. Uno per dispositivo. |
| **Registro** | Il giornale pubblico di tutte le transazioni della rete; lo conserva e lo verifica ogni nodo. |
| **Genesis** | Il pacchetto di lancio della rete: parametri, manifesto, cerchio iniziale. |
| **Versione del protocollo (protocolVersion)** | Il numero di versione delle regole della rete (attuale — 3). Registrato in ogni transazione e checkpoint; l'applicazione e la rete devono coincidere per la versione del protocollo — una build di un'altra versione non è accettata dalla rete. |
| **Manifesto** | La descrizione pubblica delle regole della rete; il suo hash è fissato nel genesis. |
| **Cerchio iniziale** | I primi partecipanti dal genesis con diritti speciali temporanei; i diritti si autoliquidano (seed_sunset: 100 portafogli attivi o 24 epoche). |
| **Avallo (vouch)** | La garanzia firmata di un partecipante attivo per un nuovo. Tre di esse attivano il portafoglio. |
| **Slot di avallo** | Il posto limitato dell'avallante; si libera dopo 3 periodi di emissione dell'avallato o 90 giorni. |
| **Sfida di emissione** | Compito computazionale (PoW) nello slot del periodo in corso, calcolabile in anticipo; finestra ±48 h disponibile in ogni periodo, il suo stato lo mostra la schermata di emissione; una omissione si compensa entro la finestra di accumulo (6 periodi). |
| **Epoca** | L'intervallo del tempo di rete (per default 24 ore); ai limiti delle epoche si pongono i checkpoint. |
| **Checkpoint** | L'istantanea dello stato della rete firmata da una soglia di partecipanti; dà finalità e protezione dei nodi leggeri. |
| **Finalità** | Il momento dopo il quale una transazione non si può più annullare. |
| **Moratoria** | Il periodo dopo la registrazione (per default 14 giorni) in cui i trasferimenti in uscita non sono disponibili. |
| **Demurrage** | Una piccola percentuale mensile di detenzione oltre il minimo; ciò che viene stornato si brucia. |
| **Esca** | La modalità aperta dal PIN di coercizione: un'interfaccia plausibile con un piccolo saldo, nessuna operazione reale. |
| **Guardiano** | Il partecipante designato per confermare la migrazione in caso di perdita del telefono. |
| **Migrazione** | Il trasferimento del portafoglio a un nuovo dispositivo tramite i guardiani; ritardo di 14 giorni. |
| **Cambio dei guardiani** | La rielezione dei guardiani personali (fino a 3) con il loro consenso; finestra di 48 h, limite di 150 cambi entrati in vigore durante la vita del portafoglio. |
| **Flagged** | L'etichetta pubblica di una violazione provata (equivocazione). |
| **Pagamento BT** | La trasmissione della transazione firmata via Bluetooth; diventa un pagamento solo dopo la conferma della rete. |
| **Profilo della rete** | L'insieme dei parametri: unità, emissione, trasferimento, deflusso, accesso ecc. |
| **Eq-hash (`Eq-<hash8>`)** | L'etichetta breve della rete (i primi 8 caratteri del suo identificatore); visibile nel nome dell'applicazione e all'onboarding — con essa si verifica che sia installata la rete giusta. |
| **Recurring (rete in abbonamento)** | La rete della risorsa in abbonamento: quota uguale per periodo, il non usato si estingue al limite del periodo. |
| **Peer-redeem** | Il trasferimento partecipante → partecipante o partecipante → fornitore nelle reti recurring: l'eccedenza di quote defluisce a chi ha bisogno della risorsa (nell'interfaccia attuale dell'applicazione non ancora implementato). |
| **Estinzione della quota** | L'unità del periodo precedente cessa di essere trasferibile dopo il limite del periodo successivo; il saldo e la storia si conservano. |

---

[← Informazioni sulla piattaforma](01-about.md) · [Indice](../README.md)
