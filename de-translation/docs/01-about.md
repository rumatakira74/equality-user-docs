# 1. Über die Plattform

## Was es ist

Equality Project ist eine Plattform, auf der eine Gemeinschaft (eine Schule, eine Genossenschaft, eine Freiwilligengruppe, eine Diaspora, eine Stiftung, ein Veranstalter) **ihr eigenes isoliertes Netz** auf den Telefonen der Mitglieder startet:

- **ohne Server** — das Netz lebt auf den Telefonen selbst;
- **ohne Administrator** — niemand kann das Netz „abschalten“ oder seine Regeln ändern;
- **ohne Betriebskosten** — für Hosting und Wartung muss nichts gezahlt werden.

Jedes Netz gibt seinen Mitgliedern drei Dinge:

1. **Ein Mensch ≈ eine Wallet.** Der Zugang erfolgt nur über Bürgschaften aktiver Mitglieder plus eine Hardware-Prüfung des Telefons. Das ist die Hauptschranke gegen Fake-Konten.
2. **Gleiches periodisches Recht.** Die „Einheit“ des Netzes (Stunden, Quote, Punkte) wird an alle aktiven Mitglieder **zu gleichen Teilen** nach einem Zeitplan emittiert.
3. **Öffentlich überprüfbare Geschichte.** Der Ruf des Mitglieds — das Alter der Wallet, wer für wen gebürgt hat, der Beitrag — ist für alle Mitglieder des Netzes sichtbar.

Was als „Einheit“ zählt und was man damit machen kann, bestimmt das **Netzprofil**: interne Währung, Zeitbank, Quoten auf eine gemeinsame Ressource, Erfassung des Freiwilligenbeitrags usw.

Das Netz wird aus einer **fertigen Vorlage** für eines der acht Szenarien zusammengesetzt: Der Organisator wählt die Vorlage, legt die Parameter fest — und erhält sein Netz mit einer eigenen App (APK).

## Das ist keine Kryptowährung

- Die Plattform **emittiert und verkauft keine Token**, schafft keinen Tauschmarkt und belohnt Mining im herkömmlichen Sinne nicht.
- Einheiten existieren nur innerhalb eines konkreten Netzes und sind in manchen Profilen überhaupt nicht übertragbar.
- Der Wert liegt in der Anwendung (siehe die Szenarien unten), nicht im Kurs der Einheit.
- Die Wörter „Wallet“, „Emission“, „Checkpoint“ sind das technische Vokabular des Journals signierter Einträge, nicht das Zeichen eines Finanzinstruments.

## Die acht Anwendungsszenarien

| № | Szenario | Einheit |
|---|----------|---------|
| 1 | Bildung und Laboratorien von Instituten (einschließlich Simulationen) | Punkte oder Spielwährung |
| 2 | Menschlichkeitsnachweis als Dienst für andere Apps | nicht übertragbarer Aktivitäts-„Puls“ |
| 3 | Gleiche Quoten auf eine gemeinsame Ressource (Wasser, Internet, Lager) | Quote pro Periode, ohne Ansammlung |
| 4 | Freiwilligen- und Straßenprogramme (Verpflegung, Hilfe) | Gutscheine des Programms |
| 5 | Interne Währung oder Zeitbank der Gemeinschaft | Stunden oder Währung, gleiche Emission |
| 6 | Erfassung des Freiwilligenbeitrags | Punkte für einen bestätigten Beitrag |
| 7 | Kasse der Gegenseitigkeit | Währung, Demurrage gegen die Ansammlung |
| 8 | Abo-Ressource — ein Abo auf eine wiederkehrende Ressource (kommerziell) | Quote pro Periode, Unbenutztes erlischt |

## Die Netze sind isoliert, und das ist die Haupteigenschaft

- Nicht ein einziges großes Netz, sondern **viele getrennte**. Jedes hat seine Zusammensetzung, seine Regeln (sein Profil), seine Einheiten.
- Zwischen den Netzen gibt es keinen Austausch. Der Saldo eines Netzes bedeutet in einem anderen nichts.
- Die Regeln des Netzes werden bei der Erstellung im **Manifest** festgelegt und sind standardmäßig unveränderlich; der Hash des Manifests ist im Genesis fixiert. Wenn die Regeln der Gemeinschaft nicht mehr passen — wird ein neues Netz gestartet (das ist kostenlos), und die Mitglieder wechseln freiwillig.
- Das Garantieniveau des Netzes **wird aus dem Manifest berechnet**, nicht behauptet: Partner sehen, aus welchem Netz und mit welchen Garantien „der Mensch“ kommt.
- Jedes Netz wird mit **seiner eigenen App** zusammengesetzt: das Label `Eq-<hash8>` (kurzer Hash des Netzidentifikators) im Namen der App zeigt, dass genau Ihr Netz installiert ist; in der App ist das Netz mit Name und Label signiert — zum Beispiel „cirrus · Eq-e5796f9c“.
- In Abo-Netzen (Szenario 8) sammeln sich die Quoten nicht an: Der unbenutzte Teil erlischt an der Periodengrenze, der Überschuss kann an die übertragen werden, die die Ressource brauchen (mehr dazu in [Tägliche Operationen](03-operations.md)).

## Die Rollen der Mitglieder

Jede Rolle ist eine gewöhnliche Wallet; niemand hat besondere „Zugriffsrechte“:

- **Mitglied** — eine registrierte Wallet; nach der Aktivierung erhält sie die Emission und überträgt Einheiten.
- **Bürge** — ein aktives Mitglied mit einem Wallet-Alter von mindestens 3 Monaten, das für einen neuen Menschen mit einem seiner begrenzten Bürgschaftsplätze bürgt.
- **Vormund** — eine Person, die im Voraus für die Wiederherstellung des Zugangs bei Verlust des Telefons benannt wird (persönliche Vormünde — 2 von 3; oder öffentliche — 3 von 5).
- **Anbieter / Empfänger des Gemeinschaftsfonds** — eine Wallet, die in den Netzparametern angegeben ist (zum Beispiel ein Partnerstandort, der Gutscheine annimmt). Das Netz kann er nicht verwalten.

## Ehrlich über die Grenzen

- **Kein passendes Smartphone — keine Teilnahme.** Das Protokoll verlangt ein Android-Telefon mit hardwareseitigem geschütztem Schlüsselspeicher. Umwege (Kuratoren, Papierquittungen) gibt es nicht.
- **Anonymität ist nicht das Ziel.** Das Register des Netzes ist innerhalb des Netzes öffentlich: Die Mitglieder sehen die Adressen, Status und die Geschichte voneinander; der Saldo ist aus dem öffentlichen Zustand des Netzes ableitbar.
- **Der Schutz vor Farmen ist ökonomisch, nicht absolut.** Eine überzählige Wallet zu erstellen muss mehr kosten, als sie einbringt; eine volle Garantie „ein Mensch — eine Wallet“ ohne externen Anker ist technisch unmöglich.

→ Weiter: [Erste Schritte](02-getting-started.md)
