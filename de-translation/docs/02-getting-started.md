# 2. Erste Schritte

> **Status: Testversion.** Die App wurde in einem geschlossenen Testnetz auf Emulatoren geprüft. Der öffentliche Build und die Veröffentlichung in den App-Stores — nach den Piloten. Alle Schritte unten beschreiben den vollständigen Onboarding-Weg.

## Was man braucht

- Ein Android-Smartphone mit hardwareseitigem geschütztem Schlüsselspeicher (StrongBox / TEE) und eingerichtetem Fingerabdruck.
- Ein Gerät ohne eingerichtete Biometrie wird zur Registrierung nicht zugelassen: Die App wird vorschlagen, die Biometrie über den Systembildschirm einzurichten.
- Bekannte im Netz: zur Aktivierung der Wallet braucht man **3 Bürgschaften** aktiver Mitglieder (siehe unten).

## Installation

Die App wird als APK verbreitet (die Abteilung zur Verbreitung über Google Play — in juristischer Prüfung). Installieren Sie die APK-Datei Ihres Netzes: Jede Netz-Instanz kann einen eigenen Build mit eingebrannten Parametern verbreiten. Die App des Netzes ist mit dem Netznamen und dem Label `Eq-<hash8>` signiert — prüfen Sie das Label bei der Installation, um nicht ein fremdes Netz zu installieren. App und Netz müssen in der **Protokollversion** übereinstimmen (aktuelle — 3): Die Nummer ist in jeder Transaktion und jedem Checkpoint verzeichnet; ein Build einer anderen Version wird vom Netz nicht angenommen.

Die Oberfläche der App ist in neun Sprachen verfügbar: Russisch, Englisch, Spanisch, Portugiesisch, Chinesisch, Französisch, Deutsch, Italienisch, Japanisch.

## Erstellung der Wallet

1. Die App erzeugt das Schlüsselpaar **innerhalb des geschützten Speichers des Telefons (Keystore)**. Der private Schlüssel ist nicht exportierbar: Er kann nicht kopiert, exportiert oder weitergeleitet werden — niemals.
2. Das Telefon durchläuft eine **Hardware-Attestierung**: das Netz prüft, dass es ein echtes Gerät mit unveränderter Bootkette und geschützter Hardware ist und dass die Attestierungskette genau für Ihren neuen Schlüssel ausgestellt wurde (die Bindung des Schlüssels an das Zertifikat — jeder Knoten des Netzes prüft sie selbst; eine fremde Kette ist nicht unterschiebbar). Das Bild des Fingers wird nirgendwohin übertragen.
3. Eine Rechenaufgabe (proof-of-work) wird ausgeführt — Schutz gegen eine massenhafte automatische Registrierung. Das dauert Sekunden.
4. Die Wallet erhält den Status **registered** — sie kann bereits Transfers empfangen, aber Emission und Versand sind noch nicht verfügbar.

Ein Mensch ≈ eine Wallet: Eine wiederholte Registrierung vom selben Gerät aus ist **erschwert** — sie erfordert wesentlich teurere Rechenarbeit (PoW), und eine strenge Hardware-Garantie „ein Gerät — eine Wallet“ gibt es nicht.

## Bürgschaften: der Weg zum aktiven Status

Für die volle Arbeitsfähigkeit muss die Wallet **active** werden. Dafür braucht man **K = 3 Bürgschaften** (`vouch`) von verschiedenen aktiven Mitgliedern.

**Wer bürgen kann:**

- ein Mitglied mit dem Status `active` und einem Wallet-Alter von mindestens 3 Monaten;
- mit freien Bürgschaftsplätzen (es gibt wenige davon: 3–5 je nach Anciennität);
- die Bürgschaft kann bei einem persönlichen Treffen über QR-Code oder Bluetooth ausgestellt werden.

**Was eine Bürgschaft bedeutet.** Der Bürge riskiert nur seinen Platz und seinen Anteil an der Belohnung; der Verlust von Einheiten droht ihm nicht. Für einen ehrlichen Neuling erhält der Bürge **10 % der ersten 12 Emissionen** des Gebürgten (ausgezahlt aus der Emission des Neulings selbst, nicht aus dem Nichts). Wenn der Neuling bei einer Verletzung ertappt wird — der Bürge verliert die Belohnung.

**Wenn Sie keine Bekannten im Netz haben:** Benutzen Sie die öffentlichen Kanäle der Gemeinschaft, wo Neulinge Bürgen finden. Der Bürge antwortet für seine Wahl mit einem begrenzten Platz — eine „Verteilung“ von Bürgschaften an jedermann ist für ihn nicht vorteilhaft.

## Erster Zugang und PIN

Bei der Einrichtung wählen Sie:

- den **PIN** — die Hauptmethode zur Bestätigung gefährlicher Operationen;
- bei Wunsch — den **Zwangs-PIN** (siehe [Sicherheit](04-security.md));
- den Zugang zur App — per Fingerabdruck oder PIN.

Wichtige Sicherheitsregeln:

- **Der Zugang** zur App — Fingerabdruck oder PIN.
- **Gefährliche Operationen** (Transfer, Emission, Start der Migration) — **nur ausdrückliche PIN-Eingabe**. Der Fingerabdruck wird zu ihrer Bestätigung nie verwendet: Ein Finger lässt sich mit Gewalt auflegen, ein PIN nicht.
- Wenn der Zwangs-PIN aktiviert ist, wird der Zugang per Fingerabdruck deaktiviert.

Das Hinzufügen eines neuen Fingerabdrucks im System **invalidiert den Schlüssel** (sicherer, bedeutet aber den Verlust des Zugangs) — deshalb benennen Sie sofort Vormünde.

## Vormünde: benennen Sie sie sofort

Benennen Sie Vormünde **bei der Erstellung der Wallet**, nicht wenn das Telefon schon untergegangen ist:

- **persönliche Vormünde** — 2 von 3 Personen zur Wahl;
- oder **öffentliche Vormünde** — geprüfte Mitglieder mit mindestens 12 Monaten Anciennität; Schwelle 3 von 5 (kombinierbar).

Der Vormund ist gestorben, verschwunden oder hat das Netz verlassen? Vormünde können **später neu gewählt werden** — mit Zustimmung der neuen (48-Stunden-Fenster, Limit von 150 wirksamen Wechseln). Wie — im Abschnitt [„Vormundwechsel“](03-operations.md#vormundwechsel). Verschieben Sie nicht die Benennung selbst: Ohne Vormünde ist die Wiederherstellung unmöglich.

Ausführlich — im Abschnitt [Wiederherstellung](03-operations.md#wiederherstellung-des-zugangs).

Und füllen Sie sofort die **Wiederherstellungskarte** aus (siehe [Wiederherstellung](03-operations.md#wiederherstellungskarte--füllen-sie-sie-im-voraus-aus)): die Adresse Ihrer Wallet, die Adressen Ihrer Vormünde und den Namen des Netzes — notieren und außerhalb des Telefons aufbewahren. Bei Verlust des Telefons wird es diese Daten nicht mehr hergeben. Die App zeigt sie auf dem Bildschirm „Wiederherstellungskarte“ mit QR-Code.

## Die Statusse der Wallet

| Status | Wie er erhalten wird | Was man machen kann |
|--------|----------------------|---------------------|
| `registered` | nach der Registrierung (Attestierung + PoW) | Transfers empfangen |
| `active` | 3 Bürgschaften | Emission, Transfers, Bürgschaften |
| `expired` | 3 Jahre in registered ohne Aktivierung | Transfers an die Adresse bleiben erhalten; für die Emission ist eine neue Registrierung nötig |
| Label `flagged` | nachgewiesene Verletzung (doppelte Signatur) | Emission ausgesetzt, Bürgen für andere verboten |

→ Weiter: [Tägliche Operationen](03-operations.md)
