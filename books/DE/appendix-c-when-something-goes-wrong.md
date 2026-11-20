# Anhang C — Wenn etwas schiefgeht

Dieser Anhang ist nach Symptomen geordnet, denn so kommt die Störung. Jeder Eintrag sagt, was Sie sehen, was es üblicherweise bedeutet und was zu tun ist. Die mit *beobachtet* markierten Einträge sind Ausfälle, die beim Schreiben dieses Buches auf der Installation auftraten, die seine Screenshots erzeugt hat; sie sind hypothetisch.

Bevor irgendetwas anderes, eine Gewohnheit. Wenn etwas schiefgeht, installieren Sie nicht neu. Lesen Sie die letzten zwanzig Zeilen des Logs und schauen Sie, welche der drei Boxen auf dem Serviettenpapier unzufrieden ist: der Speicher (die Datenbank), das Modell (das ERP) oder der Assistent. Neunmal von zehn sagt Ihnen die Antwort, was zu tun ist, und das Neuinstallieren zerstört die Beweise.

---

## Der Installer stoppt mit "psql wurde nicht gefunden"

**Was Sie sehen.** Der Installer meldet, dass PostgreSQL nicht installiert ist, versucht `winget`, versucht dann, den offiziellen Installer direkt herunterzuladen und stopkt schließlich mit einer Meldung, dass `psql` nicht gefunden wurde und dass nichts nach diesem Schritt funktionieren würde.

**Was es bedeutet.** PostgreSQL ist nicht auf dem Rechner. Der Installer hat versucht, es zu installieren, und konnte nicht: entweder `winget` konnte seine Quelle nicht erreichen, oder der Download von der Site des Herstellers ist nicht fertig geworden. Bei einer langsamen oder instabilen Verbindung ist dies der häufigste Ausfall des ganzen Vorgangs.

**Was zu tun.** Lassen Sie den Installer erneut laufen. Er fährt dort fort, wo er aufgehört hat, und verwendet, was bereits da ist; ein unterbrochener Download wird fortgesetzt statt neu gestartet, so dass jeder Versuch weiter kommt als das letzte. Wenn Sie sich auf einer Verbindung befinden, die langsamer ist als etwa ein halbes Megabit pro Sekunde, laden Sie den PostgreSQL-Installer selbst mit einem Browser von der Site des Herstellers herunter und legen Sie ihn im Ordner ab, den der Installer meldet; der nächste Lauf findet ihn und verwendet ihn. Wenn Sie PostgreSQL lieber von Hand installieren möchten, funktioniert jede 16.x-Version, und der Installer erkennt sie beim nächsten Lauf—einschließlich des Ports, den er aus der eigenen Konfigurationsdatei des Servers liest.

*Beobachtet beim Schreiben dieses Buches:* der erste Lauf schlug genau an diesem Punkt fehl, nach drei Download-Versuchen, auf einer Verbindung mit etwa sechzig Kilobytes pro Sekunde. Der zweite Lauf setzte die unterbrochene Datei fort und wurde fertig.

---

## "TCP-Port 5432 wird bereits verwendet"

**Was Sie sehen.** Früh im Lauf eine Warnung, dass Port 5432 belegt ist und dass PostgreSQL stattdessen auf 5433 hören wird.

**Was es bedeutet.** Etwas anderes auf dem Rechner verwendet den Standard-Datenbankport. Sehr oft ist es eine Datenbank innerhalb des Windows-Subsystem für Linux, die auf die Windows-Seite weitergeleitet wird, oder ein Docker-Container.

**Was zu tun.** Nichts. Der Installer wählt den ersten freien Port und führt ihn durch den ganzen Stack—die Datenbankrolle, die Datenbank, das ERP und der Launcher. Dies ist kein Fehler; es ist der Installer, der auf einem ausgelasteten Rechner das Richtige tut. Schreiben Sie den Port auf, wenn Sie sich mit anderen Werkzeugen mit der Datenbank verbinden möchten.

---

## `winget` kann nichts installieren

**Was Sie sehen.** Eine Meldung, dass `winget` mit einer Verbindungsfehler beendet wurde, gefolgt vom Ausweichen des Installers auf einen direkten Download.

**Was es bedeutet.** Die Paketquelle konnte nicht erreicht werden. Firmennetze, Hotelnetze und einige Antivirenprodukte stören den Windows-Paketmanager.

**Was zu tun.** Lassen Sie das Ausweichen seine Arbeit tun. Wenn beide Wege fehlschlagen, installieren Sie die Komponente von Hand (PostgreSQL und Python sind die einzigen zwei, die der Installer von außen benötigt), dann lassen Sie den Installer erneut laufen.

---

## Die Seite, die sich öffnet, ist nicht die Anmeldeseite

**Was Sie sehen.** Sie doppelklicken auf **AI Odoo**, oder öffnen `http://localhost:8069`, und der
Browser zeigt etwas anderes als die weiße Anmeldekarte: eine Seite über Odoo, eine Website mit einem
Platzhalter-Logo, oder eine Liste von Datenbanken.

**Was es bedeutet.** Die verlangte Adresse ist nicht die Ihres ERP, oder es ist eine Adresse, auf die
mehrere Dinge antworten können. Es gibt genau drei Fälle, und jeder hat seine Ursache.

*Es ist die Dokumentation von Odoo, auf odoo.com, in der Sprache Ihres Browsers.* Das ist eine Seite
über das Produkt, nicht über Ihre Maschine: nichts davon sind Ihre Daten, und sie gehört nicht zur
Installation. Sie ist das, was eine frühere Version des Installers am Ende öffnete, und sie wird am
Ende noch als Link zum späteren Lesen gedruckt. Schließen Sie sie und öffnen Sie die Startseite über
das Symbol.

*Es ist eine Website mit einem Logo, das Sie nicht gewählt haben, einem Menü und einem kleinen Link
„Anmelden" in einer Ecke.* Das ist Odoos **website**-Anwendung: ein Modul, das unter der
Wurzeladresse eine öffentliche Seite ausliefert. Einmal installiert, zeigt `http://localhost:8069`
die Website statt der Anmeldeseite, und der ERP versteckt sich hinter dem kleinen Anmeldelink. Nichts
ist kaputt und keine Daten sind verloren. Die Anmeldeseite hat ihre eigene Adresse, und sie
funktioniert immer: `http://localhost:8069/web/login?db=odoo_agent`. Die Startseite und das Symbol
benutzen diese Adresse aus diesem Grund.

*Es ist eine Liste von Datenbanken, oder ein Formular, das fragt, welche Datenbank gemeint ist.* Die
Maschine hält mehr als eine Odoo-Datenbank—eine Testkopie, eine alte Installation—und die Adresse
nannte keine. Hängen Sie `?db=odoo_agent` an die Adresse, oder benutzen Sie die Startseite, die sie
nennt.

---

## Die am Ende gedruckte Anmeldung und das Passwort funktionieren nicht

**Was Sie sehen.** Die Zugangsdaten in der Zusammenfassung des Installers werden abgelehnt, und die
Anmeldeseite sagt, Benutzername oder Passwort seien falsch.

**Was es bedeutet.** Bei einer ersten Installation legt der Installer den Administrator an und druckt,
was er angelegt hat, also stimmen beide überein. Bei einem zweiten Lauf existiert das Konto bereits
und behält seine Anmeldung und sein Passwort: dort ein frisch erfundenes Passwort zu drucken, hieße
ein Passwort zu drucken, das nie gesetzt wurde. Jetzt liest der Installer das Konto aus der Datenbank
zurück und sagt entweder das Passwort, das er gesetzt hat, oder dass das Passwort seit der ersten
Installation unverändert ist.

**Was zu tun ist.** Steht in der Zusammenfassung *unverändert*, benutzen Sie das Passwort der ersten
Installation. Ist es verloren, setzen Sie bewusst ein neues: führen Sie den Installer erneut mit
`ADMIN_PASS` in der Umgebung aus, und er wird dieses Passwort anwenden und drucken. Sonst wird nichts
in der Datenbank angefasst.

---

## Das schwarze Fenster ist verschwunden

**Was Sie sehen.** Odoo antwortet weiter im Browser, aber es gibt kein Fenster zum Tippen.

**Was es bedeutet.** Das schwarze Fenster *ist* der Assistent: es zu schließen stoppt den Assistenten,
und nur den Assistenten. Der ERP läuft als eigenes Programm, und deshalb funktioniert der Browser
weiter.

**Was zu tun ist.** Doppelklicken Sie erneut auf **AI Odoo**. Es startet, was fehlt, und startet keine
zweite Kopie von dem, was schon läuft.

---

## Das ERP antwortet nicht auf seinem Port

**Was Sie sehen.** Nach der Installation kann der Browser die am Ende gedruckte Adresse nicht erreichen (Vorgabe ist `http://localhost:8069`) oder der Launcher öffnet eine leere Seite.

**Was es bedeutet.** Der ERP-Prozess läuft nicht, oder er ist gestartet und dann wegen eines Fehlers im eigenen Log gestoppt.

**Was zu tun.** Öffnen Sie die Datei `odoo.log` im Ordner, den der Installer angelegt hat (Vorgabe unter Ihren lokalen Anwendungsdaten, in `odoo-tool-stack`). Die letzten Zeilen sagen, warum. Die drei häufigsten Ursachen sind: der Datenbankdienst läuft nicht; das Datenbankpasswort in der Konfiguration stimmt nicht mehr mit der Datenbank überein; und der Port wird von einem anderen Programm belegt. Alle drei sind ohne Neuinstallation zu beheben.

---

## Der Assistent antwortet, findet aber das ERP nicht

**Was Sie sehen.** Sie fragen "listet die Kunden auf" und der Assistent antwortet, dass er sich nicht verbinden kann, oder dass die Konfiguration fehlt.

**Was es bedeutet.** Der Connector des Assistenten hat keine Adresse, keinen Schlüssel, oder einen Schlüssel, den das ERP nicht mehr akzeptiert. Der Connector liest seine Einstellungen aus der Umgebung oder aus einer kleinen Datei im Datenordner des Assistenten.

**Was zu tun.** Prüfen Sie zuerst, ob das ERP läuft und in einem Browser erreichbar ist. Dann prüfen Sie den Schlüssel: öffnen Sie im ERP das Benutzer-Menü, gehen Sie zur Kontensicherheitsseite und erstellen Sie einen neuen API-Schlüssel. Fügen Sie ihn in die Konfiguration des Connectors ein. Wenn Sie das Passwort des ERP-Benutzers geändert haben, überleben bestehende Schlüssel üblicherweise; wenn Sie den Benutzer gelöscht und neu erstellt haben, tun sie das nicht.

---

## Der Assistent erstellt einen doppelten Kunden

**Was Sie sehen.** Zwei Kunden, die fast gleich heißen: "Ashfield Academy" und "Ashfield Academy Ltd."

**Was es bedeutet.** Der Assistent wurde gebeten, einen Kunden zu erstellen, und tat, was man ihm sagte. Er entscheidet nicht automatisch, dass ein ähnlicher Name dieselbe Firma ist, und das sollte er nicht: zwei Zweige derselben Organisation dürfen legitim zwei Datensätze sein.

**Was zu tun.** Formulieren Sie die Anweisung so, dass zuerst gesucht wird—"suche den Kunden Ashfield und füge einen Kontakt hinzu"—oder bitten Sie den Assistenten, Ihnen zuerst die Übereinstimmungen zu zeigen, bevor irgendetwas erstellt wird. Wenn ein Doppelte auftaucht, verschmelzen oder archivieren Sie ihn im ERP statt ihn zu löschen, damit die Geschichte der Rechnungen intakt bleibt.

---

## Ein Dokument kann nicht gebucht werden

**Was Sie sehen.** Das ERP weigert sich, eine Rechnung oder eine Lieferung zu buchen, und zeigt eine Meldung über ein fehlendes Konto, eine fehlende Steuer oder eine abgeschlossene Periode.

**Was es bedeutet.** Das Modell ist unvollständig. Ein Produkt hat kein Einnahmenkonto, oder die Firma hat keine Steuer konfiguriert, oder die Buchungsperiode wurde gesperrt.

**Was zu tun.** Lesen Sie die Meldung; sie nennt das Feld. Beheben Sie die Konfiguration in den Einstellungen des ERP, dann buchen Sie erneut. Dies ist das ERP, das seine Arbeit tut: es weigert sich, einen Buchungssatz zu schreiben, den Pacioli nicht erkennen würde.

---

## Alles ist langsam

**Was Sie sehen.** Bildschirme brauchen Sekunden zum Laden; der Assistent braucht lange zum Antworten.

**Was es bedeutet.** Zwei verschiedene Dinge, üblicherweise verwechselt. Wenn die ERP-Bildschirme langsam sind, ist das Problem lokal: die Datenbank, die Festplatte oder der Speicher des Rechners. Wenn nur der Assistent langsam ist, ist das Problem das Sprachmodell—entweder der entfernte Dienst, oder das lokale Modell, wenn Sie eines laufen lassen.

**Was zu tun.** Schauen Sie zuerst auf den Speicher und die Festplatte des Rechners. Dann schauen Sie auf das Log des Assistenten: es verzeichnet, wie lange jeder Request gedauert hat und welche Werkzeuge aufgerufen wurden. Ein einzelner Request, der dreißig Sekunden dauert, weil er zwölf Werkzeugaufrufe gemacht hat, ist kein Fehler; es ist ein Request, der enger formuliert hätte sein sollen.

---

## Sie haben das Administratorpasswort verloren

**Was es bedeutet.** Das am Ende der Installation gedruckte Passwort wurde nicht aufgeschrieben.

**Was zu tun.** Bei einer selbst gehosteten Installation sind Sie der Besitzer des Rechners, so dass Sie es aus der Datenbank zurücksetzen können. Stoppen Sie das ERP, verbinden Sie sich mit der Datenbank mit dem eigenen Administrator-Akount der Datenbank und setzen Sie einen neuen Passwort-Hash für den Administrator-Benutzer. Das Verfahren ist in der eigenen Dokumentation des ERP unter "das Administratorpasswort zurücksetzen" dokumentiert, und es dauert zwei Minuten. Löschen Sie die Datenbank nicht, um ein Passwortproblem zu lösen.

---

## Die eine Regel

Was auch geschieht, bewahren Sie zwei Dinge: die Log-Datei und eine Kopie der Datenbank aus der Zeit vor der Änderung. Mit diesen beiden kann fast jedes Problem diagnostiziert werden und die meisten können rückgängig gemacht werden. Ohne sie wird jedes Problem zu einem Streit darüber, was früher wahr war.
