# Projektvorhaben: Kompetenzspiegel

**Informatik · Maxim · Jahrgang 10**

---

## Was habe ich vor?

Ich entwickle mit **C# und .NET 9** ein Webtool, in dem sich Schüler:innen selbst einschätzen und Lehrkräfte ihre Schüler:innen einschätzen. Am Ende sieht man beide Sichtweisen nebeneinander und erkennt sofort, wo Selbstbild und Fremdbild abweichen.

## Was soll das Tool können?

- **Login in zwei Schritten:** erst E-Mail, auf der nächsten Seite das Passwort
- **Klassen:** Lehrkräfte können Klassen erstellen, Schüler:innen werden danach sortiert
- **Schüler:innen:** sich selbst einschätzen und abgeben
- **Lehrkräfte:** Startseite „Deine Klasse“, Bereich „Hier bist du Fachkraft“, abgegebene Einschätzungen sehen (auch live, während noch ausgefüllt wird), Half/Half-Ansicht mit Selbst- und Lehrer-Einschätzung
- **Freigabe:** Die Lehrkraft klickt auf „Schüler informieren“. Erst dann sieht die Schüler:in beide Einschätzungen.
- **Design:** modern und auch am Handy nutzbar

## Warum kein IServ-SSO?

Eigentlich sollte die Anmeldung über IServ-SSO laufen. Dafür fehlt mir aber der Zugriff auf die IServ-Administration. Deshalb baue ich einen eigenen Login und halte ihn austauschbar, damit SSO später nachgerüstet werden kann.

## Wie setze ich es um?

| Bereich | Technik |
|---|---|
| Oberfläche | ASP.NET Core mit Blazor |
| Datenbank | SQLite mit Entity Framework Core |
| Login und Rollen | ASP.NET Core Identity |
| Live-Ansicht | SignalR |