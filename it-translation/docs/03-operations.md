# 3. Operazioni quotidiane

## Emissione

Nelle reti con emissione periodica ogni partecipante attivo riceve una volta per periodo (per default — ogni mese) la sua **parte uguale**: per esempio, 1000 unità il 1° del mese.

Particolarità:

- **La sfida di emissione.** Per dichiarare l'emissione, l'applicazione risolve un compito computazionale nel **suo slot del periodo in corso** (finestra di ±48 ore). Il momento dello slot è calcolato in anticipo dall'indirizzo e dal periodo ed è identico per tutti i nodi; lo slot si trova all'interno del proprio periodo, quindi la finestra **è disponibile in ogni periodo** (dopo la correzione del mint — v9.14: prima la finestra poteva cadere in un tempo irraggiungibile, e il portafoglio, dopo sei periodi mancati di fila, perdeva l'emissione per sempre). Lo stato della finestra lo mostra la schermata di emissione («aperta — si può emettere» / «chiusa — quando si aprirà»). Il periodo mancato non si perde: l'accredito si riporta entro la **finestra di accumulo — 6 periodi**, i fondi non sono bloccati; un salto consapevole oltre la finestra — l'emissione si estingue.
- La prima emissione è possibile solo nel periodo **successivo** all'attivazione, senza accrediti retroattivi.
- I fondi appena emessi non sono trasferibili subito (moratoria — vedi sotto).

## Trasferimenti

- **La commissione si brucia.** Ogni trasferimento paga una piccola commissione (`fee`) che viene distrutta — il destinatario riceve esattamente l'importo indicato. La commissione protegge la rete dallo spam e frena leggermente il movimento del valore.
- **La tariffa è adattiva.** La percentuale della commissione viene ricalcolata dalla rete al limite di ogni epoca in modo identico per tutti i nodi: se l'offerta di unità cresce più in fretta del ritmo obiettivo — la tariffa sale, altrimenti scende. Intervallo — dallo 0,5% al 2%, minimo 0,01 unità; nessuno può fissare la tariffa manualmente.
- **Moratoria per i portafogli recenti:** i trasferimenti diventano disponibili 14 giorni dopo la registrazione (parametro della rete; 14 giorni — il valore di default). Questo taglia lo schema «registrato — svuotato».
- **Il tempo della transazione è il momento della firma.** Le regole della rete (moratoria, estinzione delle quote, termini dei trasferimenti differiti, finestra di emissione) si applicano al momento della firma della transazione, non al momento della sua pubblicazione: un trasferimento firmato offline e pubblicato più tardi lo valutano identicamente tutti i nodi. L'orologio del telefono non deve discostarsi dalla rete più di ±30 minuti — le transazioni con uno scarto maggiore non sono accettate dalla rete (ripetete la pubblicazione dopo la sincronizzazione dell'ora).
- **Trasferimenti grandi differiti.** Un trasferimento sopra la soglia (per default **P = 3000 unità**) si esegue solo dopo **48 ore**. Durante il ritardo potete annullarlo direttamente dall'applicazione — per esempio, sotto coercizione o se avete cambiato idea. La regola vale in tutte le reti con unità trasferibili e non si disattiva. La soglia si può cambiare entro il massimo (30000); l'aumento entra in vigore dopo 48 ore, l'abbassamento — subito.

### Reti in abbonamento (recurring): quote per periodo

Nelle reti della risorsa in abbonamento (scenario 8) le unità sono **quote per periodo**: ogni partecipante attivo riceve una quota uguale, e la parte non usata **si estingue al limite del periodo successivo** — così l'abbonamento non si trasforma in accaparramento. Trasferire o riscattare un'unità del periodo precedente dopo questo limite è impossibile: l'applicazione mostrerà un errore comprensibile «l'unità si è estinta». Il saldo però nessuno lo «azzera» — la storia è visibile a tutti; semplicemente le vecchie quote non si trasferiscono più.

L'eccedenza si può dare a chi le quote non gli bastano: trasferimenti **partecipante → partecipante** e **partecipante → fornitore** (modalità peer-redeem; la conferma — una ricevuta firmata). Nota: la modalità è supportata dal core e dalla specifica, ma nell'interfaccia attuale dell'applicazione non è ancora implementata.

### Pagamento Bluetooth

Il Bluetooth si usa **solo** per trasmettere direttamente al destinatario la transazione firmata, quando manca l'internet. Il destinatario pubblica la transazione nella rete appena la connessione ricompare.

**Importante:** finché la transazione non è pubblicata e confermata dalla rete, essa **non è un pagamento**. Il mittente può consegnare la stessa somma a due destinatari. Perciò, nell'interfaccia, lo stato è «ricevuto via Bluetooth — in attesa di pubblicazione», e il destinatario deve attendere la conferma della rete.

## Demurrage (nelle reti con valuta)

Nei profili con valore trasferibile (valuta interna, cassa di mutuo soccorso) può operare il **demurrage** — una piccola «tassa di detenzione» mensile oltre il minimo non imponibile. La stornatura non passa per una transazione separata: il saldo effettivo si ricalcola in modo deterministico alla successiva operazione.

Il senso: il valore è nel flusso, non nell'accumulo. Il demurrage e la commissione bruciata fanno parte della protezione dalle fattorie, non un modo per togliere unità: il demurrage lo si può «aggirare» semplicemente non accumulando.

## Avalli

- L'avallante garantisce per un nuovo partecipante spendendo uno dei suoi **slot** (3 con un'anzianità di 3–12 mesi, 5 — oltre).
- Lo slot si libera quando l'avallato ha condotto 3 periodi di emissione senza violazioni, oppure dopo 90 giorni, se non si è mai attivato.
- La ricompensa agli avallanti — **il 10% delle prime 12 emissioni** dell'avallato, automaticamente e in parti uguali fra tutti e tre.
- Se contro l'avallato è provata una violazione, la ricompensa cessa; all'avallante non si toglie denaro.

## Violazioni e l'etichetta flagged

L'unica violazione dimostrabile è **l'equivocazione**: due transazioni conflittuali firmate dallo stesso portafoglio (doppia spesa, doppia emissione). La prova la pubblica qualsiasi nodo, tutti la verificano identicamente. Conseguenze: etichetta pubblica `flagged`, sospensione dell'emissione per 3 mesi (in caso di ripetizione — per sempre), divieto di avallare. «Sembra una fattoria» non è una prova — nessun verdetto sui sospetti.

## Recupero dell'accesso

La chiave non è esportabile; perciò, in caso di perdita del telefono, funziona il **recupero sociale** (transazione `migrate`):

1. Il nuovo telefono passa la stessa verifica che alla registrazione.
2. I guardiani confermano la migrazione: **personali 2 su 3** oppure **pubblici 3 su 5** (combinabili).
3. **Ritardo di 14 giorni**, durante il quale la vecchia chiave (se è viva) può annullare la migrazione.
4. L'età, la storia, gli avalli, le emissioni **e i fondi (il saldo)** si trasferiscono al nuovo portafoglio; la vecchia impronta finisce per sempre nella lista nera.

### Scheda di recupero — compilatela in anticipo

Per avviare la migrazione, sul nuovo telefono bisognerà inserire **il vecchio indirizzo del portafoglio**, poi il nonce e le firme dei guardiani. Questi dati non si «recuperano dal nulla»: sul telefono perduto non si sono conservati.

**In anticipo, finché il telefono è vivo:**

- annotate **l'indirizzo del vostro portafoglio** (hex, mostrato nell'applicazione) e conservatelo fuori dal telefono (non nel cloud) — sulla carta o come codice QR stampato;
- annotate **gli indirizzi dei vostri guardiani** e il modo di contattarli;
- annotate **il nome della rete** (nell'applicazione è mostrato con l'etichetta `Eq-<hash8>`) e dove prendere il suo APK (ogni rete distribuisce una propria build).

L'applicazione mostra tutti questi dati nella schermata **«Scheda di recupero»** alla creazione del portafoglio (e più tardi — nelle impostazioni e nella schermata di migrazione) con codice QR: esportateli o stampateli.

**Durante la migrazione:**

- il nonce e le firme dei guardiani sono le chiavi del recupero del vostro portafoglio: **non trasmetteteli a nessuno e non pubblicateli**;
- trasmetteteli **solo di persona** fra voi e il vostro guardiano — di persona o tramite un canale protetto, non tramite terzi;
- inseriteli solo nella vostra applicazione; dopo il completamento della migrazione cancellateli dalle corrispondenze.

Un guardiano pubblico (partecipante con ≥ 12 mesi di anzianità) riceve per una migrazione riuscita del suo tutelato una ricompensa fissa dall'emissione — non più di una volta ogni 12 mesi per tutelato.

**Se i guardiani non sono designati**, resta il riavvio: una nuova registrazione con una nuova chiave e tre nuovi avalli. I fondi sul vecchio portafoglio si perdono — designate i guardiani in anticipo.

### Cambio dei guardiani

Il guardiano è morto, è scomparso o è uscito dalla rete — i guardiani si possono **rieleggere** (transazione `update_guardians`):

1. **Consenso dei nuovi guardiani.** Ogni nuovo guardiano (fino a 3) firma l'hash del cambio di persona — nello stesso modo della conferma di una migrazione: senza la loro firma il cambio è impossibile.
2. **Pubblicazione del cambio.** Impostazioni → Guardiani → «Rieleggere»; la pubblicazione e l'annullamento — solo dopo inserimento esplicito del PIN.
3. **Finestra di 48 ore.** Il cambio entra in vigore 48 ore dopo la pubblicazione; prima si può annullare (anch'esso solo con PIN).
4. **Limite — 150 cambi.** Non più di 150 cambi entrati in vigore durante la vita del portafoglio; gli annullati e gli scaduti non contano. Il contatore dei cambi rimanenti è visibile nell'applicazione.

Nessuna commissione per il cambio; ogni cambio si pubblica nella storia della rete. I nuovi guardiani devono essere attivi (`active`) e senza l'etichetta `flagged`. In modalità esca il «cambio dei guardiani» si «esegue» in modo plausibile, ma la lista reale dei guardiani non si tocca.

→ Avanti: [Sicurezza del proprietario](04-security.md)
