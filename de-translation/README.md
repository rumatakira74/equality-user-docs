# Equality Project — Nutzerdokumentation

Die russische Originalversion: [README.md](../README.md).

**Equality Project** ist eine Plattform, auf der eine Gemeinschaft **ihr eigenes isoliertes Vertrauensnetz** auf den Telefonen der Mitglieder startet: ohne Server, ohne Administrator und ohne Betriebskosten.

**DOI:** [10.5281/zenodo.23558900](https://doi.org/10.5281/zenodo.23558900)

> **Status: Testversion (pre-release).** Die App ist im Testnetz auf Emulatoren vollständig geprüft. Die Prüfung auf echten Telefonen und die ersten Piloten stehen noch aus. Die Dokumentation beschreibt die Funktionsweise des Produkts gemäß Spezifikation v9.16 / protocol_version 3 (einschließlich der Neuwahl der Vormünde `update_guardians`: 48-h-Fenster, Limit von 150 wirksamen Wechseln; das achte Szenario — eine Abo-Ressource: Abo-Netze (recurring) mit periodischen Quoten und Erlöschen).

> **Sprachen.** Die Dokumentation ist auf Russisch (das Original, `docs/`) und in Übersetzungen verfügbar:
> [dieses Verzeichnis](.) — Deutsch. Die Sprachen der App-Oberfläche —
> ru, en, es, pt, zh, fr, de, it, ja (`app/lib/l10n` des Hauptrepositoriums).

© 2026 Kirill Lapchinsky · rumatakira74@gmail.com · Telegram [@rumatakira](https://t.me/rumatakira)

## Inhalt

1. [Über die Plattform](docs/01-about.md) — was es ist, für wen es gedacht ist, die acht Szenarien, die Rollen
2. [Erste Schritte](docs/02-getting-started.md) — Installation, Wallet-Erstellung, Bürgschaften, Zugang
3. [Tägliche Operationen](docs/03-operations.md) — Emission, Transfers, Gebühr, Demurrage, Wiederherstellung
4. [Sicherheit des Eigentümers](docs/04-security.md) — PIN und Biometrie, Zwangs-PIN, Grenzen des Schutzes
5. [Fragen und Antworten, Glossar](docs/05-faq-glossary.md)

## Andere Repositorien des Projekts

- [equality-trust-networks](https://github.com/rumatakira74/equality-trust-networks) — der Quellcode und die Spezifikation der Plattform
- [equality-programming-docs](https://github.com/rumatakira74/equality-programming-docs) — die Dokumentation für Programmierer
- [equality-anti-farm-simulation](https://github.com/rumatakira74/equality-anti-farm-simulation) — das Modell der Farm-Wirtschaft (die Begründung der Parameter)

## Haftungsausschluss

Das Projekt befindet sich im Status einer Vorabversion; die Grenzen der Garantien und der Haftung sind in [DISCLAIMER.md](DISCLAIMER.md) beschrieben (Deutsch und Englisch).

## Lizenz

Der Quellcode ist für die **nichtkommerzielle Nutzung** offen; die kommerzielle Nutzung und kommerzielle abgeleitete Werke — unter einer kostenpflichtigen Lizenz (die Bedingungen — in der Spezifikation, Abschnitt 16).

Der Lizenztext: [LICENSE](../LICENSE) (das russische Original, rechtlich maßgeblich) · [LICENSE-ENG.md](../LICENSE-ENG.md) (eine inoffizielle englische Übersetzung).
