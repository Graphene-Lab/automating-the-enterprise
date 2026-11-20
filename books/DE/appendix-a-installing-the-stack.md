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

Am Ende druckt das Fenster etwa Folgendes. Schreiben Sie es auf, oder fotografieren Sie den
Bildschirm.

```
  Odoo (der ERP, im Browser):  http://localhost:8069
  Anmeldung: admin@yourcompany.example
  Passwort: (das vom Installer erzeugte, oder das, das Sie ihm gegeben haben)
  Assistent (hier sprechen Sie mit ihm):  http://localhost:5290/OfficeManager
```

Wenn das Administratorkonto aus einem früheren Lauf schon existierte, druckt der Installer die
Anmeldung, die wirklich in der Datenbank steht, und sagt, dass das Passwort unverändert ist, statt
ein neues zu erfinden, das nicht funktionieren würde.

Der Browser öffnet die **Startseite**: eine Datei auf diesem Rechner mit der Adresse, dem Konto und
einem Link. Diese Seite ist der Anfang der Konfiguration, nicht das Ende der Installation.

## Schritt 7 — Das Symbol, und die drei Fenster

Doppelklicken Sie auf das Symbol **AI Odoo** auf dem Desktop. Drei Dinge geschehen:

1. der ERP startet, wenn er nicht lief;
2. die Startseite öffnet sich im Browser;
3. der Assistent öffnet sich in seinem eigenen schwarzen Fenster.

*Odoo öffnen* auf der Startseite führt zur Anmeldeseite unter
`http://localhost:8069/web/login?db=odoo_agent`. Der Assistent ist das schwarze Fenster, und dort
wird getippt; es sollte offen bleiben, während Sie arbeiten, denn Schließen stoppt den Assistenten,
während Odoo weiterläuft.

Beim ersten Start fragt der Assistent nach dem KI-Anbieter: Dienst wählen, Schlüssel einfügen, und er
holt die Modellliste dieses Dienstes. Mehr ist nicht nötig—die Adresse des ERP und der Zugangs
schlüssel wurden vom Installer geschrieben.

## Schritt 8 — Prüfen, dass es funktioniert

Drei Prüfungen, in dieser Reihenfolge, und jede sagt Ihnen, welche der drei Maschinen unzufrieden
ist, wenn sie scheitert.

1. **Der ERP.** Klicken Sie auf *Odoo öffnen* auf der Startseite, oder öffnen Sie
   `http://localhost:8069/web/login?db=odoo_agent` in einem Browser, und melden Sie sich an. Lädt
   die Seite nicht, laufen ERP oder Datenbank nicht; die Datei `odoo.log` im Installationsordner
   sagt warum.
2. **Der Connector.** Fragen Sie im Assistenten: *prüfe die Verbindung zu Odoo und sag mir, welche
   Version läuft.* Eine Versionsnummer bedeutet, dass Schlüssel und Adresse stimmen.
3. **Das Modell.** Fragen Sie: *wie viele Kunden haben wir?* Eine Zahl bedeutet, dass der Assistent
   die Daten des ERP als sein Benutzer lesen kann, mit dessen Berechtigungen.

Wenn alle drei antworten, ist die Installation vollständig.

## Deinstallation

Zwei Skripte machen die Installation rückgängig, und sie sind der unterstützte Weg: `uninstall.bat`
unter Windows und `uninstall.sh` unter Linux. Sie liegen neben dem Installer in derselben
Veröffentlichung, und jedes lässt sich allein herunterladen und ausführen.

Was sie entfernen:

- die Odoo-Datenbank, mit jedem Kunden, Produkt, Auftrag, jeder Rechnung und jeder Lagerbewegung;
- den Installationsordner (`%LOCALAPPDATA%\odoo-tool-stack`, oder `~/odoo-tool-stack`);
- die **AI Odoo**-Verknüpfungen und die Firewall-Regel.

Sie fragen zweimal, und die zweite Frage ist keine Formalität. Die erste ist ein Ja/Nein, das
auflistet, was verschwindet. Die zweite verlangt den Satz **DESTROY ALL**, in Großbuchstaben getippt.
Ist der Satz nicht exakt, wird nichts angefasst—keine Datei, keine Zeile. Das Löschen ist
unwiderruflich, und der Deinstaller macht keine Sicherung; eine vorher genommene Kopie der Datenbank
ist der einzige Weg zurück.

AgentBridge wird getrennt gefragt, weil es andere Werkzeuge beherbergen kann und eigene Einstellungen
und API-Schlüssel hält: ein *Nein* behält es und entfernt nur die Odoo-Hälfte.

PostgreSQL bleibt installiert. Es ist ein Dienst, den andere Programme teilen können, und es wird in
*Apps und Features* entfernt wie jedes andere Programm, wenn nichts anderes es mehr braucht. Die
Datenbankrolle `odoo` bleibt zurück und ist harmlos: eine künftige Installation benutzt sie wieder.
