# 4. Sicherheit des Eigentümers

## PIN und Biometrie: was wofür dient

| Aktion | Womit sie bestätigt wird |
|--------|--------------------------|
| Zugang zur App | Fingerabdruck **oder** PIN |
| Transfer, Emission, Start der Migration | **nur ausdrückliche PIN-Eingabe** |
| Vormundwechsel (Veröffentlichung, Annullierung) | **nur ausdrückliche PIN-Eingabe** |
| Schlüsselentsperrung innerhalb der Operation | Biometrie nach dem PIN — nur „Entsperren“ |

Warum so: Der Fingerabdruck kann **physisch erzwungen** werden — den Finger eines anderen mit Gewalt auf den Sensor zu legen ist möglich. Ein PIN nicht. Deshalb verlangt jede Operation, die Schaden anrichten kann, genau den PIN, und jeder PIN-Eingabebildschirm ist zugleich ein Eingangspunkt in den Ködermodus (unten).

Der Zugang per Fingerabdruck ist nur ein Komfort zum Entsperren der Oberfläche; bei aktiviertem Zwangs-PIN wird er vollständig deaktiviert.

## Zwangs-PIN und Ködermodus

Die Bedrohung: Man zwingt Sie, die App zu öffnen oder Einheiten zu senden.

Bei der Einrichtung legen Sie zwei PINs fest: **gewöhnlich** und **Zwangs-PIN**. Der Zwangs-PIN öffnet den **Ködermodus**:

- die Oberfläche sieht genau gleich aus, aber ein plausibler **kleiner Saldo** und eine Geschichte werden angezeigt (Null anzuzeigen ist unmöglich — eine aktive Wallet erhält regelmäßig Emissionen, ein Nullsaldo wäre verdächtig);
- „Transfers“ aus dem Köder enden mit einem plausiblen „wartet auf Bestätigung“ oder einem Netzfehler — echte Transaktionen werden nicht veröffentlicht;
- die echte Wallet arbeitet weiter im Hintergrund;
- die Benachrichtigungen enthalten keine Beträge: Die App hat keine Benachrichtigungen über Operationen; die einzige Systembenachrichtigung ist die des Vordergrunddienstes des Knotens („Der Knoten des Vertrauensnetzes läuft“), ohne Beträge und Adressen;
- der „Vormundwechsel“ im Köder wird plausibel „ausgeführt“, aber die echte Liste der Vormünde wird nicht berührt.

Beide PINs sind **ununterscheidbar**: gleiche Öffnungszeit, gleiche Oberfläche, gleiches Limit an Versuchen. Der Zwangs-PIN wird auf **jedem** PIN-Eingabebildschirm angewandt — Transfer, Emission, Einstellungsänderung.

**Verbergen kann man, auf null setzen nicht:** der Saldo ist ein öffentlicher Zustand des Netzes, der Schlüssel wird nicht gelöscht. Die lokale Datenbank kann mit den ordentlichen Mitteln des Systems gelöscht werden — sie wird sich beim Abgleich mit dem Netz wiederherstellen.

## Verzögerte große Transfers — zweite Schicht

Ein Transfer über der Schwelle (standardmäßig 3000 Einheiten) wird nach **48 Stunden** ausgeführt; jederzeit vor der Ausführung kann man ihn annullieren. Der Erzwingende erhält „Transfer gesendet“, aber keine Einheiten; Sie annullieren ihn, sobald Sie in Sicherheit sind. Die Verzögerung ist fest und lässt sich nicht deaktivieren.

## Was der Schutz nicht tut (lesen Sie ehrlich)

- **Öffentliches Register.** Jeder, dem Sie gezahlt haben oder von dem Sie empfangen haben, kennt Ihre Adresse; die Geschichte ist öffentlich, der Saldo ist aus dem Zustand des Netzes ableitbar (das Register der App zeigt Adresse, Status und Alter; der Saldo — auf der Wallet und per Merkle-Beweis des Checkpoints). Der Köder wird geprüft: Die Adresse in ihm wird mit der echten im Netz nicht übereinstimmen.
- **Gegen einen vorbereiteten Angreifer ist der Köder nicht garantiert.** Er wirkt gegen schnelle Erzwingung und Überfall.
- **Gegen den Diebstahl eines entsperrten Telefons** schützt die Signatur „bei jeder Operation“: Einheiten auszugeben, indem man das Telefon einfach in den Händen hält, ist unmöglich.
- **Gegen den Verlust des Telefons** — die Vormünde und die Migration (Abschnitt [Wiederherstellung](03-operations.md#wiederherstellung-des-zugangs)). Ohne Vormünde gehen die Mittel verloren.
- **Ein Dieb, der Ihren PIN kennt, kann die Migration** im 14-Tage-Fenster annullieren — eine bekannte Einschränkung der v1: Das Recht der Annullierung gehört dem alten Schlüssel. Milderungen — öffentliche Vormünde und ein erneuter Start der Migration.

## Checkliste einer sicheren Einrichtung

1. Legen Sie den PIN und den Zwangs-PIN beim ersten Start fest.
2. Benennen Sie die Vormünde (2 von 3 persönlichen oder 3 von 5 öffentlichen) — sofort, bei der Erstellung der Wallet.
3. Füllen Sie die Wiederherstellungskarte aus ([Abschnitt „Wiederherstellung“](03-operations.md#wiederherstellungskarte--füllen-sie-sie-im-voraus-aus)): die Adresse der Wallet, die Adressen der Vormünde, den Namen des Netzes — notieren und außerhalb des Telefons aufbewahren. Die Migrationsdaten (Nonce, Signaturen der Vormünde) geben Sie niemandem weiter und veröffentlichen sie nicht.
4. Sagen Sie niemandem Ihren PIN; den Zwangs-PIN erst recht (dass er existiert, sollte niemand wissen).
5. Denken Sie daran: Das Hinzufügen eines neuen Fingerabdrucks im System invalidiert den Schlüssel — das ist ein Schutz gegen Unterschiebung, aber auch Ihr Risiko, den Zugang zu verlieren.
6. Halten Sie große Summen nicht „für alle Fälle“ — der Demurrage in Währungsnetzen bestraft genau die Ansammlung.

→ Weiter: [FAQ und Glossar](05-faq-glossary.md)
