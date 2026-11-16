# Anhang A — Installation des Stacks, Schritt für Schritt

Dieser Anhang ist die Installation ohne die Geschichte: dieselbe Prozedur wie Kapitel sieben, geschrieben als Liste, der Sie folgen können, während das Buch geschlossen ist. Sie setzt Windows 10 oder 11 voraus; die Linux-Prozedur ist dasselbe Skript mit einem anderen Namen, und der Installer ist so ausgelegt, dass er sich identisch verhält.

## Bevor Sie beginnt

| Anforderung | Warum | Wie man es prüft |
|---|---|---|
| Windows 10 oder 11, 64-Bit | die Datenbank-Engine und der Assistent sind Windows-Programme | Einstellungen → System → Informationen |
| Etwa 12 GB freier Speicherplatz | Datenbank, ERP-Quelle, Python-Pakete, Assistent | Datei-Explorer → Dieser PC |
| Ein Administrator-Konto | die Datenbank installiert einen Windows-Dienst | der Installer weist am Ende darauf hin, falls das richtige fehlt |
| Eine Internetverbindung | die Teile werden einmal heruntergeladen | ein beliebiger Browser |
| Ein Firmenname | er erscheint auf Ihren Dokumenten | entscheiden Sie ihn jetzt |

Sie benötigen **nicht**: ein Datenbank-Passwort, eine Port-Nummer, .NET, Git, Docker, eine Python-Installation oder irgendwelche Kenntnisse der Kommandozeile.

## Schritt 1 — Den Installer besorgen

Laden Sie `install.bat` von der OdooTool-Releases-Seite herunter und legen Sie sie in einen leeren Ordner, zum Beispiel `C:\Users\<you>\Downloads\odoo-install\`.

Die Datei ist ein paar Kilobytes groß. Sie lädt den Rest von sich selbst herunter, falls sie muss, so dass sie funktioniert, selbst wenn sie allein eintrifft.

## Schritt 2 — Sie ausführen

Doppelklicken Sie auf `install.bat`. Ein Konsolenfenster öffnet sich mit dem Titel *OdooTool-Installer*.

Falls Windows eine Genehmigung zur Durchführung von Änderungen verlangt, erteilen Sie sie: die Datenbank muss einen Dienst registrieren.

## Schritt 3 — Die Fragen beantworten

Bei einem normalen Lauf fragt der Installer nach dem **Firmennamen** und akzeptiert den vorgeschlagenen Standard für alles andere durch Drücken von Enter. Bei einem unbeaufsichtigten Lauf können die Antworten im Voraus über Umgebungsvariablen gegeben werden, und der Installer fragt überhaupt nichts.

Der Installer gibt eine Überschrift namens *Questions* mit den Antworten aus, die er verwenden wird, so dass Sie sehen können, was er entschieden hat, bevor er zu arbeiten beginnt.

## Schritt 4 — Die vier Phasen beobachten

Der Bildschirm gibt je Phase eine Überschrift aus. Jede Überschrift wird von Zeilen gefolgt, die angeben, was geschieht; es muss nichts eingegeben werden.

1. **Freier Speicherplatz.** Er verweigert den Start unterhalb von zwölf Gigabytes.
2. **Prüfung von PostgreSQL, Python und Git.** Es wird berichtet, was es gefunden hat und was es installieren wird.
3. **Installation.** Der lange Teil: die Datenbank, die Python-Laufzeitumgebung, falls nötig, die ERP-Quelle, die Python-Pakete, die Datenbank selbst, der Assistent, der Connector.
4. **Zusammenfassung.** Adressen, Zugangsdaten und was noch fehlt, falls etwas fehlt.

Zwei Nachrichten während der Phase 2 sind normal und sind keine Fehler:

- *TCP-Port 5432 ist bereits belegt; die neue PostgreSQL hört stattdessen auf 5433.* Etwas anderes auf der Maschine hält den Standard-Port. Der Installer wählt den nächsten freien und verwendet ihn überall.
- *PostgreSQL ist nicht installiert. Es wird jetzt mit dem 'postgres'-Superuser-Passwort installiert, das auf 'odoo' gesetzt ist.* Das Passwort wird vom Installer vergeben, ist auf diesen PC beschränkt und wird am Ende ausgegeben. Es muss nichts erinnert oder nachgeschabt werden.

## Schritt 5 — Wenn der Download langsam ist

Der Datenbank-Installer ist etwa 390 MB groß und stammt von der eigenen Seite des Herstellers. Bei einer langsamen Leitung kann der Download eine Stunde dauern oder fehlschlagen. Der Installer bewahrt die partielle Datei auf und setzt sie beim nächsten Lauf fort, so dass **das erneute Ausführen die richtige Reaktion ist**—es fährt dort fort, wo es aufgehört hat, und wiederverwendet, was bereits vorhanden ist.

Falls die Maschine den Hersteller überhaupt nicht erreichen kann, laden Sie den PostgreSQL 16 Windows-Installer selbst von enterprisedb.com herunter, legen Sie ihn in den Ordner, den der Installer angibt, und führen Sie `install.bat` erneut aus. Er wird sie finden und ihre Größe prüfen, bevor er sie verwendet.

## Schritt 6 — Die Zusammenfassung bewahren

Am Ende gibt das Fenster etwas wie dieses aus. Schreiben Sie es auf oder fotografieren Sie den Bildschirm.

```
Odoo:          http://localhost:8069
Administrator: admin@yourcompany.example
Password:      (das vom Installer erzeugte oder das von Ihnen angegebene)
Database:      odoo auf Port 5433
Assistant:     AI Odoo (Desktop-Symbol)
```

Der Browser öffnet die Erst-Schritte-Seite des ERP. Diese Seite ist der Beginn der Konfiguration, nicht das Ende der Installation.

## Schritt 7 — Der erste Start des Assistenten

Doppelklicken Sie auf das **AI Odoo**-Symbol auf dem Desktop. Zwei Dinge geschehen: das ERP startet (falls es nicht lief) und der Assistent öffnet sich in seinem eigenen Terminalfenster. Der Browser öffnet die ERP-Seite.

Bei seinem ersten Start fragt der Assistent nach dem AI-Anbieter: wählen Sie den Dienst, fügen Sie den Schlüssel ein, und er ruft die Modellliste dieses Dienstes ab. Sonst wird nichts benötigt—die Adresse des ERP und der Zugriffsschlüssel wurden vom Installer geschrieben.

## Schritt 8 — Prüfen, dass es funktioniert

Prüfungen, drei, in der Reihenfolge, und jede sagt Ihnen, welche der drei Maschinen unzufrieden ist, falls sie fehlschlägt.

1. **Das ERP.** Öffnen Sie `http://localhost:8069` in einem Browser und melden Sie sich an. Falls die Seite nicht lädt, läuft das ERP oder die Datenbank nicht; die Datei `odoo.log` im Installationsordner sagt, warum.
2. **Der Connector.** Fragen Sie im Assistenten: *prüfen Sie die Verbindung zu Odoo und sagen Sie mir, welche Version läuft.* Eine Versionsnummer bedeutet, dass der Schlüssel und die Adresse richtig sind.
3. **Das Modell.** Fragen Sie: *wie viele Kunden haben wir?* Eine Zahl bedeutet, dass der Assistent die Daten des ERP als dessen Benutzer lesen kann, mit den Berechtigungen dieses Benutzers.

Falls alle drei antworten, ist die Installation abgeschlossen.

## Deinstallation

Der Stack lebt in einem Ordner, `%LOCALAPPDATA%\odoo-tool-stack`, zuzüglich der Datenbank-Dienstes und der Benutzerdaten in `%LOCALAPPDATA%\agent`. Um ihn zu entfernen:

1. Stoppen Sie das ERP und den Assistenten (schließen Sie ihre Fenster).
2. Deinstallieren Sie PostgreSQL von *Apps & Funktionen* (oder führen Sie dessen Deinstallationsprogramm aus), und löschen Sie den Ordner, den es in `C:\Program Files\PostgreSQL` hinterläuft, falls etwas übrig bleibt.
3. Löschen Sie `%LOCALAPPDATA%\odoo-tool-stack` und `%LOCALAPPDATA%\agent`.
4. Löschen Sie das **AI Odoo**-Symbol vom Desktop und vom Startmenü.

Das ist die ganze Entfernung. Nirgendwo sonst wird etwas registriert, was einer der Vorteile eines Systems ist, das auf Ihrer eigenen Maschine läuft.
