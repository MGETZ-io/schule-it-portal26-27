## Live-Ansicht mit SignalR

### Was ist SignalR?

**SignalR** ist eine Technologie von Microsoft für **Echtzeit-Kommunikation** zwischen dem Server und den verbundenen Geräten.

Normalerweise muss eine Webseite immer wieder beim Server nachfragen, ob es neue Daten gibt. Mit SignalR kann der Server neue Informationen **direkt an die verbundenen Nutzer senden**.

### Wie funktioniert das im Kompetenzspiegel?

Die Lehrkraft kann sehen, wie weit ein Schüler mit seiner Einschätzung ist.

Wenn der Schüler zum Beispiel eine Bewertung ändert oder eine Frage beantwortet, wird die Änderung an den Server gesendet.

Der Server gibt die Änderung anschließend über **SignalR** direkt an die Lehrkraft weiter.

```text
Schüler
   │
   │ Änderung
   ▼
ASP.NET Core Server
   │
   │ SignalR
   ▼
Lehrkraft
   │
   ▼
Ansicht wird automatisch aktualisiert
```

Dadurch muss die Lehrkraft **nicht ständig die Seite neu laden**.

### Beispiel

Max Mustermann bearbeitet gerade seine Selbsteinschätzung.

Er beantwortet eine weitere Frage.

```text
Max:
"Frage 8 beantwortet"
        │
        ▼
     Server
        │
        ▼
     SignalR
        │
        ▼
Lehrkraft:
"Max hat 8 von 15 Fragen beantwortet"
```

Die Anzeige bei der Lehrkraft aktualisiert sich dabei automatisch.

### Warum wird SignalR verwendet?

Ohne SignalR müsste die Webseite zum Beispiel alle paar Sekunden den Server fragen:

```text
Gibt es neue Daten?
Gibt es neue Daten?
Gibt es neue Daten?
Gibt es neue Daten?
```

Mit SignalR wartet die Verbindung auf neue Informationen:

```text
Schüler → Server → SignalR → Lehrkraft
```

Dadurch eignet sich SignalR besonders für die **Live-Ansicht des Bearbeitungsstands**.
