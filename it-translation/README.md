# Equality Project — documentazione per l'utente

La versione originale russa: [README.md](../README.md).

**Equality Project** è una piattaforma su cui una comunità lancia **la propria rete di fiducia isolata** sui telefoni dei membri: senza server, senza amministratore e senza costi operativi.

**DOI:** [10.5281/zenodo.23558900](https://doi.org/10.5281/zenodo.23558900)

> **Stato: versione di prova (pre-release).** L'app è interamente verificata nella rete di test su emulatori. La verifica su telefoni reali e i primi piloti restano a venire. La documentazione descrive il funzionamento del prodotto secondo la specifica v9.16 / protocol_version 3 (inclusa la rielezione dei guardiani `update_guardians`: finestra di 48 h, limite di 150 cambi entrati in vigore; l'ottavo scenario — una risorsa in abbonamento: reti in abbonamento (recurring) con quote per periodo ed estinzione).

> **Lingue.** La documentazione è disponibile in russo (l'originale, `docs/`) e nelle traduzioni:
> [questa directory](.) — italiano. Le lingue dell'interfaccia dell'app —
> ru, en, es, pt, zh, fr, de, it, ja (`app/lib/l10n` del repository principale).

© 2026 Kirill Lapchinsky · rumatakira74@gmail.com · Telegram [@rumatakira](https://t.me/rumatakira)

## Indice

1. [Informazioni sulla piattaforma](docs/01-about.md) — che cos'è, per chi è, gli otto scenari, i ruoli
2. [Primi passi](docs/02-getting-started.md) — installazione, creazione del portafoglio, avalli, accesso
3. [Operazioni quotidiane](docs/03-operations.md) — emissione, trasferimenti, commissione, demurrage, recupero
4. [Sicurezza del proprietario](docs/04-security.md) — PIN e biometria, PIN di coercizione, i limiti della protezione
5. [Domande e risposte, glossario](docs/05-faq-glossary.md)

## Altri repository del progetto

- [equality-trust-networks](https://github.com/rumatakira74/equality-trust-networks) — il codice sorgente e la specifica della piattaforma
- [equality-programming-docs](https://github.com/rumatakira74/equality-programming-docs) — la documentazione per i programmatori
- [equality-anti-farm-simulation](https://github.com/rumatakira74/equality-anti-farm-simulation) — il modello dell'economia delle fattorie (la giustificazione dei parametri)

## Avvertenza di non responsabilità

Il progetto è in stato di versione preliminare; i limiti delle garanzie e della responsabilità sono descritti in [DISCLAIMER.md](DISCLAIMER.md) (italiano e inglese).

## Licenza

Il codice sorgente è aperto per **l'uso non commerciale**; l'uso commerciale e le opere derivate commerciali — dietro una licenza a pagamento (le condizioni — nella specifica, sezione 16).

Il testo della licenza: [LICENSE](../LICENSE) (l'originale russo, giuridicamente prevalente) · [LICENSE-ENG.md](../LICENSE-ENG.md) (una traduzione inglese non ufficiale).
