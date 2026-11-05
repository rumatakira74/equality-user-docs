# 5. Fragen und Antworten · Glossar

## FAQ

**Braucht man Internet?**
Für gewöhnliche Operationen — ja, zumindest eine periodische Verbindung. Bluetooth erlaubt es, die signierte Transaktion direkt an den Empfänger zu übergeben, aber die Zahlung findet erst nach der Veröffentlichung und der Bestätigung durch das Netz statt.

**Ich habe keine Bekannten im Netz. Wie aktiviere ich mich?**
Über die öffentlichen Kanäle der Gemeinschaft: Dort finden Neulinge Bürgen. Der Bürge antwortet für seine Wahl mit einem begrenzten Platz und der Belohnung; Bürgschaften an jedermann zu verteilen, ist für ihn nicht vorteilhaft. Die Bürgschaft kann bei einem persönlichen Treffen über QR oder Bluetooth ausgestellt werden.

**Ich habe mein Telefon verloren. Was ist mit den Einheiten?**
Der Schlüssel ist nicht exportierbar, aber die soziale Wiederherstellung funktioniert: Die Vormünde (persönliche 2 von 3 oder öffentliche 3 von 5) bestätigen die Migration auf das neue Telefon; nach 14 Tagen werden Alter, Geschichte, Bürgschaften und Mittel übertragen. Ohne benannte Vormünde — nur eine neue Registrierung; die Mittel auf der alten Wallet gehen verloren.

**Kann man die Vormünde wechseln?**
Ja. Wenn der Vormund verschwunden, gestorben ist oder das Netz verlassen hat, wählen Sie ihn neu: Die neuen Vormünde signieren den Hash des Wechsels persönlich, der Wechsel wird mit ausdrücklicher PIN-Eingabe veröffentlicht und tritt nach 48 Stunden in Kraft (bis dahin kann man ihn annullieren). Limit — 150 wirksame Wechsel während der Lebensdauer der Wallet. Ausführlich — [„Vormundwechsel“](03-operations.md#vormundwechsel).

**Ich habe beide PINs vergessen.**
Die Wallet wird unzugänglich: Der Schlüssel lässt sich nicht extrahieren, der PIN lässt sich nicht „per Post zurücksetzen“ — solche Kanäle gibt es in einem System ohne Server nicht. Der einzige Weg — die Migration über die Vormünde.

**Kann jemand meine Wallet fälschen?**
Der Schlüssel ist im geschützten Speicher des Telefons; nur er kann eine Operation signieren. Eine Fälschung ist ohne physischen Zugang zu einem entsperrten Gerät unmöglich.

**Was, wenn jemand Hunderte von Wallets erschafft (eine Farm)?**
Schranken: 3 Bürgschaften pro Wallet (begrenzte Plätze), Hardware-Attestierung (Emulatoren und gerootete Geräte bestehen nicht, die Attestierungskette ist an den registrierten Schlüssel gebunden), Rechenaufgabe im Slot der laufenden Periode, Moratorium, Gebühr und Demurrage. Modell der Farm-Wirtschaft: Bei der kanonischen Schätzung von 120 $ pro Gerät geht eine Farm nicht früher als nach ~3,5 Jahren in Plus (bei 200 $ — nach ~4,5 Jahren) und nur bei hohem externem Wert der Einheit; mehrere Wallets auf einem Gerät verbilligen die Farm — die Robustheit der Schlussfolgerung ist mit einem Sensitivitätsraster geprüft (Gerätekosten × Zahl der Wallets pro Gerät). Der Prüfungshorizont der Sicherheitsmetrik — mindestens 5 Jahre. Die Garantie „ein Mensch — eine Wallet“ gibt niemand: Der Schutz ist ökonomisch.

**Warum ist der Saldo von selbst gesunken?**
In Währungsnetzen wirkt der Demurrage — ein kleiner monatlicher Prozentsatz über dem steuerfreien Minimum. Er spiegelt sich bei der nächsten Operation wider; es gibt keine separate Abbuchungstransaktion.

**Der Transfer „hängt“ 48 Stunden. Ist das ein Hack?**
Nein, das ist ein verzögerter Transfer: Ein Betrag über der Schwelle (standardmäßig 3000) wird immer nach 48 Stunden ausgeführt, und man kann ihn vor der Ausführung annullieren.

**Kann man im Netz geheim abstimmen?**
In v1 — nein: Der Identifikator für die Drittanbieter-App ist öffentlich mit der Adresse verknüpft. Geheime Abstimmungen werden erst in zukünftigen Versionen möglich sein.

**Die App schreibt „die Einheit ist erloschen“. Was bedeutet das?**
Sie sind in einem Abo-Netz (recurring): Die Quote ist an die Periode gebunden, und nach der Grenze der nächsten Periode kann man sie nicht mehr übertragen. Das ist weder eine Strafe noch ein Saldo-Verlust — eine neue Quote kommt in der neuen Periode; den Überschuss gibt man besser über peer-redeem denen, die die Ressource brauchen.

**Was kostet die Teilnahme?**
Das Netz nimmt keine Teilnahmegebühr. Betriebskosten hat die Plattform überhaupt nicht — Server existieren nicht. Die Transfergebühr wird verbrannt und kommt niemandem zugute.

## Glossar

| Begriff | Bedeutung |
|---------|-----------|
| **Wallet** | Das Konto des Mitglieds: Adresse + Kette signierter Einträge + Saldo. Eine pro Gerät. |
| **Register** | Das öffentliche Journal aller Transaktionen des Netzes; jeder Knoten bewahrt und prüft es. |
| **Genesis** | Das Startpaket des Netzes: Parameter, Manifest, Seed-Kreis. |
| **Protokollversion (protocolVersion)** | Die Versionsnummer der Netzregeln (aktuelle — 3). In jeder Transaktion und jedem Checkpoint verzeichnet; App und Netz müssen in der Protokollversion übereinstimmen — ein Build einer anderen Version wird vom Netz nicht angenommen. |
| **Manifest** | Die öffentliche Beschreibung der Netzregeln; sein Hash ist im Genesis fixiert. |
| **Seed-Kreis** | Die ersten Mitglieder aus dem Genesis mit zeitweiligen Sonderrechten; die Rechte selbstliquidieren sich (seed_sunset: 100 aktive Wallets oder 24 Epochen). |
| **Bürgschaft (vouch)** | Die signierte Garantie eines aktiven Mitglieds für einen Neuen. Drei davon aktivieren die Wallet. |
| **Bürgschaftsplatz** | Der begrenzte Platz des Bürgen; wird nach 3 Emissionsperioden des Gebürgten oder 90 Tagen frei. |
| **Emissions-Challenge** | Rechenaufgabe (PoW) im Slot der laufenden Periode, im Voraus berechenbar; Fenster ±48 h in jeder Periode verfügbar, sein Zustand zeigt der Emissionsbildschirm; eine Versäumnis wird innerhalb des Ansammelfensters (6 Perioden) kompensiert. |
| **Epoche** | Das Intervall der Netzzeit (standardmäßig 24 Stunden); an den Epochengrenzen werden Checkpoints gesetzt. |
| **Checkpoint** | Der von einer Schwelle von Mitgliedern signierte Schnappschuss des Netz-Zustands; er gibt Finalität und den Schutz leichter Knoten. |
| **Finalität** | Der Moment, nach dem eine Transaktion nicht mehr zurückgerollt werden kann. |
| **Moratorium** | Die Periode nach der Registrierung (standardmäßig 14 Tage), in der ausgehende Transfers nicht verfügbar sind. |
| **Demurrage** | Ein kleiner monatlicher Prozentsatz auf die Lagerung über dem Minimum; Abgebuchtes wird verbrannt. |
| **Köder** | Der Modus, den der Zwangs-PIN öffnet: eine plausible Oberfläche mit kleinem Saldo, keine echten Operationen. |
| **Vormund** | Das Mitglied, das zur Bestätigung der Migration bei Verlust des Telefons benannt wird. |
| **Migration** | Die Übertragung der Wallet auf ein neues Gerät über die Vormünde; Verzögerung von 14 Tagen. |
| **Vormundwechsel** | Die Neuwahl der persönlichen Vormünde (bis zu 3) mit ihrer Zustimmung; 48-h-Fenster, Limit von 150 wirksamen Wechseln während der Lebensdauer der Wallet. |
| **Flagged** | Das öffentliche Label einer nachgewiesenen Verletzung (Äquivokation). |
| **Bluetooth-Zahlung** | Die Übertragung der signierten Transaktion per Bluetooth; zur Zahlung wird sie erst nach der Bestätigung durch das Netz. |
| **Netzprofil** | Der Parametersatz: Einheit, Emission, Transfer, Abfluss, Zugang usw. |
| **Eq-Hash (`Eq-<hash8>`)** | Das kurze Label des Netzes (die ersten 8 Zeichen seines Identifikators); sichtbar im Namen der App und beim Onboarding — daran prüft man, dass das richtige Netz installiert ist. |
| **Recurring (Abo-Netz)** | Das Netz der Abo-Ressource: gleiche Quote pro Periode, Unbenutztes erlischt an der Periodengrenze. |
| **Peer-redeem** | Der Transfer Mitglied → Mitglied oder Mitglied → Anbieter in recurring-Netzen: der Überschuss an Quoten fließt denen zu, die die Ressource brauchen (in der aktuellen App-Oberfläche noch nicht implementiert). |
| **Erlöschen der Quote** | Die Einheit der vergangenen Periode hört auf, nach der Grenze der nächsten Periode übertragbar zu sein; Saldo und Geschichte bleiben erhalten. |

---

[← Über die Plattform](01-about.md) · [Inhalt](../README.md)
