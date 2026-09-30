## 🔐 Login

Der Login funktioniert für **Schüler und Lehrkräfte gleich**. Es gibt also keine getrennten Login-Seiten.

### 1. E-Mail eingeben

Auf der ersten Seite gibt man seine E-Mail-Adresse ein.

```text
┌─────────────────────────────────┐
│          Kompetenzspiegel       │
│                                 │
│  E-Mail                         │
│  ┌───────────────────────────┐  │
│  │ max.mustermann@...        │  │
│  └───────────────────────────┘  │
│                                 │
│            Weiter →             │
└─────────────────────────────────┘
```

Nach dem Klick auf **„Weiter“** wird geprüft, ob ein Benutzer mit dieser E-Mail-Adresse existiert.

### 2. Passwort eingeben

Wenn die E-Mail-Adresse gefunden wurde, kommt die zweite Seite.

```text
┌─────────────────────────────────┐
│          Kompetenzspiegel       │
│                                 │
│  Passwort                       │
│  ┌───────────────────────────┐  │
│  │ ••••••••••••              │  │
│  └───────────────────────────┘  │
│                                 │
│           Anmelden              │
└─────────────────────────────────┘
```

Das Passwort wird von **ASP.NET Core Identity** überprüft.

### 3. Rolle wird erkannt

Nach erfolgreichem Login wird anhand des Benutzerkontos die Rolle erkannt.

Es gibt zum Beispiel:

* `Schüler`
* `Lehrkraft`

Der Benutzer braucht sich dabei **nicht selbst auszusuchen**, welche Rolle er hat.

```text
Login
  │
  ▼
E-Mail prüfen
  │
  ▼
Passwort prüfen
  │
  ▼
Benutzer gefunden?
  │
  ├── Nein → Fehlermeldung
  │
  └── Ja
       │
       ▼
    Rolle prüfen
       │
       ├── Schüler ──────→ Schülerbereich
       │
       └── Lehrkraft ────→ Lehrkräftebereich
```

### 4. Schülerbereich

Ein Schüler wird nach dem Login zum Schülerbereich weitergeleitet.

Dort kann er zum Beispiel:

* seine Klasse sehen
* seine eigene Einschätzung ausfüllen
* seine Einschätzung abgeben
* nach der Freigabe durch die Lehrkraft Selbst- und Fremdeinschätzung vergleichen

### 5. Lehrkräftebereich

Eine Lehrkraft wird nach dem Login zum Lehrkräftebereich weitergeleitet.

Dort kann sie zum Beispiel:

* ihre Klassen verwalten
* Schüler sehen
* Einschätzungen abgeben
* den aktuellen Bearbeitungsstand sehen
* Selbst- und Fremdeinschätzungen vergleichen
* die Ergebnisse mit **„Schüler informieren“** freigeben

### 🔒 Technische Umsetzung

Der Login wird mit **ASP.NET Core Identity** umgesetzt.

Die Benutzer werden in der SQLite-Datenbank gespeichert. Das Passwort wird dabei **nicht im Klartext gespeichert**, sondern von ASP.NET Core Identity sicher gehasht.

Die Rolle wird ebenfalls am Benutzerkonto gespeichert.

Dadurch kann das System nach dem Login automatisch entscheiden, welcher Bereich angezeigt werden darf.

```text
SQLite
│
└── Benutzer
    ├── E-Mail
    ├── Passwort-Hash
    └── Rolle
         ├── Schüler
         └── Lehrkraft
```

Der Login bleibt außerdem so aufgebaut, dass später **IServ-SSO** ergänzt werden könnte, ohne den restlichen Aufbau der Anwendung komplett neu zu machen.
