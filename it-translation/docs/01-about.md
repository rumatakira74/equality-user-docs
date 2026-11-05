# 1. Informazioni sulla piattaforma

## Che cos'è

Equality Project è una piattaforma su cui una comunità (una scuola, una cooperativa, un gruppo di volontari, una diaspora, una fondazione, un organizzatore di eventi) lancia **la propria rete isolata** sui telefoni dei partecipanti:

- **senza server** — la rete vive sui telefoni stessi;
- **senza amministratore** — nessuno può «spegnere» la rete o modificarne le regole;
- **senza costi operativi** — non c'è nulla da pagare per hosting e manutenzione.

Ogni rete dà ai partecipanti tre cose:

1. **Una persona ≈ un portafoglio.** L'accesso avviene solo tramite gli avalli dei partecipanti attivi più la verifica hardware del telefono. È la barriera principale contro i falsi account.
2. **Diritto periodico uguale.** «L'unità» della rete (ore, quota, punti) viene emessa a tutti i partecipanti attivi **in parti uguali**, secondo un calendario.
3. **Storia pubblica verificabile.** La reputazione del partecipante — l'età del portafoglio, chi ha avallato chi, il contributo — è visibile a tutti i partecipanti della rete.

Cosa contare come «unità» e cosa se ne può fare lo definisce il **profilo della rete**: valuta interna, banca del tempo, quote su una risorsa comune, contabilizzazione del contributo volontario ecc.

La rete si assembla da un **modello pronto** per uno degli otto scenari: l'organizzatore sceglie il modello, imposta i parametri — e ottiene la propria rete con un'applicazione propria (APK).

## Non è una criptovaluta

- La piattaforma **non emette e non vende token**, non crea un mercato di scambio e non premia il mining nel senso consueto.
- Le unità esistono solo all'interno di una rete specifica e in alcuni profili non si trasferiscono affatto.
- Il valore è nell'uso (vedi gli scenari sotto), non nel cambio dell'unità.
- Le parole «portafoglio», «emissione», «checkpoint» sono il vocabolario tecnico del giornale delle registrazioni firmate, non il segno di uno strumento finanziario.

## Gli otto scenari d'uso

| № | Scenario | Unità |
|---|----------|-------|
| 1 | Istruzione e laboratori degli istituti (simulazioni incluse) | punti o valuta di gioco |
| 2 | Prova di umanità come servizio per altre applicazioni | «impulso» di attività non trasferibile |
| 3 | Quote uguali su una risorsa comune (acqua, internet, magazzino) | quota per periodo, senza accumulo |
| 4 | Programmi di volontariato e di strada (pasti, assistenza) | buoni del programma |
| 5 | Valuta interna o banca del tempo della comunità | ore o valuta, emissione uguale |
| 6 | Contabilizzazione del contributo volontario | punti per un contributo confermato |
| 7 | Cassa di mutuo soccorso | valuta, demurrage contro l'accaparramento |
| 8 | Risorsa in abbonamento — abbonamento a una risorsa ricorrente (commerciale) | quota per periodo, il non usato si estingue |

## Le reti sono isolate, ed è questa la proprietà principale

- Non una sola grande rete, ma **molte reti separate**. Ognuna ha la sua composizione, le sue regole (il suo profilo), le sue unità.
- Tra le reti non c'è scambio. Il saldo di una rete non significa nulla in un'altra.
- Le regole della rete sono scritte nel **manifesto** alla creazione e per default sono immutabili; l'hash del manifesto è fissato nel genesis. Se le regole non convincono più alla comunità — si lancia una nuova rete (è gratuito) e i partecipanti passano volontariamente.
- Il livello di garanzie della rete **si calcola dal manifesto**, non si dichiara: i partner vedono da quale rete, e con quali garanzie, arriva «la persona».
- Ogni rete si assembla con **la sua applicazione**: l'etichetta `Eq-<hash8>` (hash breve dell'identificatore della rete) nel nome dell'applicazione mostra che è installata proprio la vostra rete; nell'applicazione la rete è firmata con nome ed etichetta — per esempio, «cirrus · Eq-e5796f9c».
- Nelle reti in abbonamento (scenario 8) le quote non si accumulano: la parte non usata si estingue al limite del periodo, e l'eccedenza si può trasferire a chi ha bisogno della risorsa (più dettagli in [Operazioni quotidiane](03-operations.md)).

## I ruoli del partecipante

Ogni ruolo è un portafoglio ordinario; nessuno ha speciali «diritti di accesso»:

- **Partecipante** — un portafoglio registrato; dopo l'attivazione riceve l'emissione e trasferisce unità.
- **Avallante** — un partecipante attivo con un'età del portafoglio di almeno 3 mesi, che avalla una persona nuova con uno dei suoi slot di avallo limitati.
- **Guardiano** — una persona designata in anticipo per il ripristino dell'accesso in caso di perdita del telefono (guardiani personali — 2 su 3; oppure pubblici — 3 su 5).
- **Fornitore / destinatario del fondo comune** — un portafoglio indicato nei parametri della rete (per esempio, un punto partner che accetta buoni). Non può amministrare la rete.

## Onestamente sui limiti

- **Nessuno smartphone adatto — nessuna partecipazione.** Il protocollo richiede un telefono Android con un archivio protetto hardware per le chiavi. Non ci sono vie alternative (curatori, ricevute di carta).
- **L'anonimato non è l'obiettivo.** Il registro della rete è pubblico all'interno della rete: i partecipanti vedono gli indirizzi, gli stati e la storia gli uni degli altri; il saldo è deducibile dallo stato pubblico della rete.
- **La protezione dalle fattorie è economica, non assoluta.** Creare un portafoglio superfluo deve costare più di quanto rende; una garanzia piena «una persona — un portafoglio» senza un'ancora esterna è tecnicamente impossibile.

→ Avanti: [Primi passi](02-getting-started.md)
