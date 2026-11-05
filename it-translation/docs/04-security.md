# 4. Sicurezza del proprietario

## PIN e biometria: cosa serve a cosa

| Azione | Cosa la conferma |
|--------|------------------|
| Accesso all'applicazione | impronta **o** PIN |
| Trasferimento, emissione, avvio della migrazione | **solo inserimento esplicito del PIN** |
| Cambio dei guardiani (pubblicazione, annullamento) | **solo inserimento esplicito del PIN** |
| Sblocco della chiave all'interno dell'operazione | biometria dopo il PIN — solo «sblocco» |

Perché così: l'impronta si può **forzare fisicamente** — applicare il dito di un altro al sensore con la forza è possibile. Il PIN no. Perciò ogni operazione capace di arrecare un danno richiede proprio il PIN, e ogni schermata di inserimento del PIN è anche un punto di ingresso nella modalità esca (sotto).

L'accesso con impronta è solo una comodità di sblocco dell'interfaccia; con il PIN di coercizione attivato viene disattivato completamente.

## PIN di coercizione e modalità esca

La minaccia: vi costringono ad aprire l'applicazione o a inviare unità.

Durante la configurazione impostate due PIN: **ordinario** e **di coercizione**. Il PIN di coercizione apre la **modalità esca**:

- l'interfaccia appare esattamente uguale, ma viene mostrato un **piccolo saldo verosimile** e una storia (mostrare zero non si può — un portafoglio attivo riceve regolarmente emissioni, un saldo nullo sarebbe sospetto);
- i «trasferimenti» dall'esca terminano con un plausibile «in attesa di conferma» o con un errore di rete — le transazioni reali non vengono pubblicate;
- il portafoglio reale continua a lavorare in sottofondo;
- le notifiche non contengono importi: nell'applicazione non ci sono notifiche delle operazioni; l'unica notifica di sistema è quella del servizio in primo piano del nodo («Il nodo della rete di fiducia funziona»), senza importi né indirizzi;
- il «cambio dei guardiani» nell'esca si «esegue» in modo plausibile, ma la lista reale dei guardiani non si tocca.

Entrambi i PIN sono **indistinguibili**: stesso tempo di apertura, stessa interfaccia, stesso limite di tentativi. Il PIN di coercizione si applica su **qualsiasi** schermata di inserimento del PIN — trasferimento, emissione, modifica delle impostazioni.

**Nascondere si può, azzerare no:** il saldo è uno stato pubblico della rete, la chiave non si elimina. La base locale si può eliminare con i mezzi ordinari del sistema — si ripristinerà alla verifica con la rete.

## Trasferimenti grandi differiti — secondo strato

Un trasferimento sopra la soglia (per default 3000 unità) si esegue dopo **48 ore**; in qualsiasi momento prima dell'esecuzione lo si può annullare. Chi vi costringe riceve «trasferimento inviato», non le unità; voi lo annulate appena vi trovate al sicuro. Il ritardo è fisso e non si disattiva.

## Cosa la protezione non fa (leggete onestamente)

- **Registro pubblico.** Chiunque vi abbia pagato o da cui avete ricevuto conosce il vostro indirizzo; la storia è pubblica, il saldo è deducibile dallo stato della rete (il registro dell'applicazione mostra indirizzo, stato ed età; il saldo — sul portafoglio e per la prova Merkle del checkpoint). L'esca si verifica: l'indirizzo in essa non coinciderà con quello reale sulla rete.
- **Contro un attaccante preparato l'esca non è garantita.** Funziona contro la coercizione rapida e la rapina.
- **Contro il furto di un telefono sbloccato** protegge la firma «a ogni operazione»: spendere unità, avendo semplicemente il telefono in mano, è impossibile.
- **Contro la perdita del telefono** — i guardiani e la migrazione (sezione [Recupero](03-operations.md#recupero-dellaccesso)). Senza guardiani i fondi si perdono.
- **Un ladro che conosce il vostro PIN può annullare la migrazione** nella finestra di 14 giorni — una limitazione nota della v1: il diritto di annullamento appartiene alla vecchia chiave. Attenuazioni — guardiani pubblici e un nuovo avvio della migrazione.

## Lista di controllo di una configurazione sicura

1. Impostate il PIN e il PIN di coercizione al primo avvio.
2. Designate i guardiani (2 su 3 personali o 3 su 5 pubblici) — subito, alla creazione del portafoglio.
3. Compilate la scheda di recupero ([sezione «Recupero»](03-operations.md#scheda-di-recupero--compilatela-in-anticipo)): l'indirizzo del portafoglio, gli indirizzi dei guardiani, il nome della rete — annotate e conservate fuori dal telefono. I dati di migrazione (nonce, firme dei guardiani) non trasmetteteli a nessuno e non pubblicateli.
4. Non dite a nessuno il vostro PIN; quello di coercizione a maggior ragione (la sua esistenza non dovrebbe essere nota).
5. Ricordate: l'aggiunta di una nuova impronta nel sistema invalida la chiave — è una protezione dalla sostituzione, ma è anche il vostro rischio di perdere l'accesso.
6. Non tenete somme grandi «per ogni evenienza» — il demurrage nelle reti con valuta penalizza proprio l'accumulo.

→ Avanti: [FAQ e glossario](05-faq-glossary.md)
