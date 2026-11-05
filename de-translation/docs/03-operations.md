# 3. Tägliche Operationen

## Emission

In Netzen mit periodischer Emission erhält jedes aktive Mitglied einmal pro Periode (standardmäßig — jeden Monat) seinen **gleichen Anteil**: zum Beispiel 1000 Einheiten am 1. des Monats.

Besonderheiten:

- **Die Emissions-Challenge.** Um die Emission zu beanspruchen, löst die App eine Rechenaufgabe in **ihrem Slot der laufenden Periode** (Fenster von ±48 Stunden). Der Moment des Slots wird im Voraus aus der Adresse und der Periode berechnet und ist für alle Knoten identisch; der Slot liegt innerhalb seiner eigenen Periode, deshalb ist das Fenster **in jeder Periode verfügbar** (nach dem Mint-Fix — v9.14: früher konnte das Fenster auf eine un erreichbare Zeit fallen, und die Wallet verlor nach sechs verpassten Perioden in Folge die Emission für immer). Den Zustand des Fensters zeigt der Emissionsbildschirm („offen — man kann emittieren“ / „geschlossen — wann öffnet es sich“). Die verpasste Periode geht nicht verloren: Die Gutschrift wird innerhalb des **Ansammelfensters — 6 Perioden** verschoben; Mittel werden nicht blockiert; ein bewusster Sprung über das Fenster hinaus — die Emission erlischt.
- Die erste Emission ist nur in der Periode **nach** der Aktivierung möglich, ohne rückwirkende Gutschriften.
- Frisch emittierte Mittel sind nicht sofort übertragbar (Moratorium — siehe unten).

## Transfers

- **Die Gebühr wird verbrannt.** Jeder Transfer zahlt eine kleine Gebühr (`fee`), die vernichtet wird — der Empfänger erhält genau den angegebenen Betrag. Die Gebühr schützt das Netz vor Spam und bremst die Wertbewegung leicht.
- **Der Tarif ist adaptiv.** Den Prozentsatz der Gebühr berechnet das Netz an der Grenze jeder Epoche für alle Knoten identisch neu: Wenn das Angebot an Einheiten schneller wächst als das Zieltempo — steigt der Tarif, sonst sinkt er. Spanne — von 0,5 % bis 2 %, Minimum 0,01 Einheit; niemand kann den Tarif manuell festlegen.
- **Moratorium für frische Wallets:** Transfers sind 14 Tage nach der Registrierung verfügbar (Netzparameter; 14 Tage — der Standardwert). Das schneidet das Schema „registriert — abgezogen“ ab.
- **Die Zeit der Transaktion ist der Moment der Signatur.** Die Regeln des Netzes (Moratorium, Erlöschen der Quoten, Fristen verzögerter Transfers, Emissionsfenster) werden auf den Moment der Signatur der Transaktion angewandt, nicht auf den Moment ihrer Veröffentlichung: Ein offline signierter und später veröffentlichter Transfer wird von allen Knoten gleich bewertet. Die Uhr des Telefons darf vom Netz um höchstens ±30 Minuten abweichen — Transaktionen mit größerer Abweichung werden vom Netz nicht angenommen (wiederholen Sie die Veröffentlichung nach der Zeitsynchronisation).
- **Verzögerte große Transfers.** Ein Transfer über der Schwelle (standardmäßig **P = 3000 Einheiten**) wird erst nach **48 Stunden** ausgeführt. Während der Verzögerung können Sie ihn direkt aus der App annullieren — zum Beispiel unter Zwang oder wenn Sie es sich anders überlegen. Die Regel gilt in allen Netzen mit übertragbaren Einheiten und lässt sich nicht deaktivieren. Die Schwelle kann innerhalb des Maximums (30000) geändert werden; die Erhöhung tritt nach 48 Stunden in Kraft, die Senkung — sofort.

### Abo-Netze (recurring): periodische Quoten

In Abo-Netzen der Ressource (Szenario 8) sind die Einheiten **Quoten pro Periode**: Jedes aktive Mitglied erhält eine gleiche Quote, und der unbenutzte Teil **erlischt an der Grenze der nächsten Periode** — so wird das Abo nicht zur Thesaurierung. Eine Einheit der vergangenen Periode nach dieser Grenze zu übertragen oder einzulösen ist unmöglich: Die App zeigt einen verständlichen Fehler „die Einheit ist erloschen“. Der Saldo wird dabei von niemandem „genullt“ — die Geschichte ist für alle sichtbar, nur die alten Quoten werden nicht mehr übertragen.

Den Überschuss kann man denen überlassen, denen die Quoten fehlen: Transfers **Mitglied → Mitglied** und **Mitglied → Anbieter** (Modus peer-redeem; die Bestätigung — eine signierte Quittung). Anmerkung: Der Modus wird vom Kern und der Spezifikation unterstützt, ist aber in der aktuellen App-Oberfläche noch nicht implementiert.

### Bluetooth-Zahlung

Bluetooth wird **nur** für die direkte Übertragung der signierten Transaktion an den Empfänger benutzt, wenn es kein Internet gibt. Der Empfänger veröffentlicht die Transaktion im Netz, sobald die Verbindung erscheint.

**Wichtig:** Solange die Transaktion nicht veröffentlicht und vom Netz bestätigt ist, ist sie **keine Zahlung**. Der Absender kann denselben Betrag zwei Empfängern geben. Deshalb ist der Status in der Oberfläche „per Bluetooth empfangen — wartet auf Veröffentlichung“, und der Empfänger muss die Bestätigung des Netzes abwarten.

## Demurrage (in Netzen mit Währung)

In Profilen mit übertragbarem Wert (interne Währung, Kasse der Gegenseitigkeit) kann der **Demurrage** wirken — eine kleine monatliche „Lagersteuer“ über dem steuerfreien Minimum. Die Abbuchung wird nicht als separate Transaktion durchgeführt: Der effektive Saldo wird deterministisch bei der nächsten Operation neu berechnet.

Der Sinn: Der Wert liegt im Fluss, nicht in der Ansammlung. Demurrage und verbrannte Gebühr sind Teil des Schutzes gegen Farmen, kein Weg, Einheiten wegzunehmen: Den Demurrage kann man „umgehen“, indem man einfach nicht ansammelt.

## Bürgschaften

- Der Bürge bürgt für ein neues Mitglied und verbraucht einen seiner **Plätze** (3 bei einer Anciennität von 3–12 Monaten, 5 — darüber).
- Der Platz wird frei, wenn der Gebürgte 3 Emissionsperioden ohne Verletzungen durchgeführt hat, oder nach 90 Tagen, falls er sich nie aktiviert hat.
- Die Belohnung der Bürgen — **10 % der ersten 12 Emissionen** des Gebürgten, automatisch und zu gleichen Teilen zwischen allen drei.
- Wenn gegen den Gebürgten eine Verletzung nachgewiesen wird, endet die Belohnung; dem Bürgen wird kein Geld weggenommen.

## Verletzungen und das flagged-Label

Die einzige beweisbare Verletzung ist die **Äquivokation**: zwei vom selben Wallet signierte konfliktäre Transaktionen (Doppelausgabe, doppelte Emission). Den Beweis veröffentlicht jeder Knoten, alle prüfen identisch. Folgen: öffentliches Label `flagged`, Aussetzung der Emission für 3 Monate (bei Wiederholung — für immer), Verbot zu bürgen. „Sieht wie eine Farm aus“ ist kein Beweis — keine Urteile auf Verdacht.

## Wiederherstellung des Zugangs

Der Schlüssel ist nicht exportierbar; deshalb funktioniert bei Verlust des Telefons die **soziale Wiederherstellung** (Transaktion `migrate`):

1. Das neue Telefon durchläuft dieselbe Prüfung wie bei der Registrierung.
2. Die Vormünde bestätigen die Migration: **persönliche 2 von 3** oder **öffentliche 3 von 5** (kombinierbar).
3. **Verzögerung von 14 Tagen**, während derer der alte Schlüssel (falls er lebt) die Migration annullieren kann.
4. Alter, Geschichte, Bürgschaften, Emissionen **und Mittel (der Saldo)** werden auf die neue Wallet übertragen; der alte Fingerabdruck landet für immer auf der schwarzen Liste.

### Wiederherstellungskarte — füllen Sie sie im Voraus aus

Um die Migration zu starten, muss man auf dem neuen Telefon **die alte Adresse der Wallet** eingeben und danach den Nonce und die Signaturen der Vormünde. Diese Daten lassen sich nicht „aus dem Nichts wiederherstellen“: Auf dem verlorenen Telefon haben sie sich nicht erhalten.

**Im Voraus, solange das Telefon lebt:**

- notieren Sie **die Adresse Ihrer Wallet** (hex, in der App angezeigt) und bewahren Sie sie außerhalb des Telefons auf (nicht in die Cloud) — auf Papier oder als ausgedruckten QR-Code;
- notieren Sie **die Adressen Ihrer Vormünde** und den Weg, sie zu kontaktieren;
- notieren Sie **den Namen des Netzes** (in der App wird er mit dem Label `Eq-<hash8>` angezeigt) und wo man seinen APK bekommt (jedes Netz verbreitet einen eigenen Build).

Die App zeigt alle diese Daten auf dem Bildschirm **„Wiederherstellungskarte“** bei der Erstellung der Wallet (und später — in den Einstellungen und auf dem Migrationsbildschirm) mit QR-Code: Exportieren oder drucken Sie sie.

**Während der Migration:**

- der Nonce und die Signaturen der Vormünde sind die Schlüssel zur Wiederherstellung Ihrer Wallet: **geben Sie sie niemandem weiter und veröffentlichen Sie sie nicht**;
- übergeben Sie sie **nur direkt** zwischen Ihnen und Ihrem Vormund — persönlich oder über einen geschützten Kanal, nicht über Dritte;
- geben Sie sie nur in Ihre eigene App ein; nach Abschluss der Migration löschen Sie sie aus den Korrespondenzen.

Ein öffentlicher Vormund (Mitglied mit ≥ 12 Monaten Anciennität) erhält für eine erfolgreiche Migration seines Mündels eine feste Belohnung aus der Emission — nicht öfter als einmal in 12 Monaten pro Mündel.

**Wenn die Vormünde nicht benannt sind**, bleibt der Neustart: eine neue Registrierung mit neuem Schlüssel und drei neuen Bürgschaften. Die Mittel auf der alten Wallet gehen dabei verloren — benennen Sie Vormünde im Voraus.

### Vormundwechsel

Der Vormund ist gestorben, verschwunden oder hat das Netz verlassen — die Vormünde können **neu gewählt werden** (Transaktion `update_guardians`):

1. **Zustimmung der neuen Vormünde.** Jeder neue Vormund (bis zu 3) signiert den Hash des Wechsels persönlich — genauso wie bei der Bestätigung einer Migration: ohne ihre Signatur ist der Wechsel unmöglich.
2. **Veröffentlichung des Wechsels.** Einstellungen → Vormünde → „Neuwählen“; die Veröffentlichung und die Annullierung — nur nach ausdrücklicher PIN-Eingabe.
3. **Fenster von 48 Stunden.** Der Wechsel tritt 48 Stunden nach der Veröffentlichung in Kraft; bis dahin kann er annulliert werden (ebenfalls nur mit PIN).
4. **Limit — 150 Wechsel.** Nicht mehr als 150 wirksame Wechsel während der Lebensdauer der Wallet; annullierte und abgelaufene zählen nicht. Der Zähler der verbleibenden Wechsel ist in der App sichtbar.

Keine Gebühr für den Wechsel; jeder Wechsel wird in die Geschichte des Netzes veröffentlicht. Neue Vormünde müssen aktiv (`active`) und ohne das Label `flagged` sein. Im Ködermodus wird der „Vormundwechsel“ plausibel „ausgeführt“, aber die echte Liste der Vormünde wird nicht berührt.

→ Weiter: [Sicherheit des Eigentümers](04-security.md)
