# 8. Was geschah, während sich die Leiste bewegte

Die Installation dauerte vierzig Minuten, von denen die meiste mit dem Ansehen eines Bildschirms verbracht wurde, der sich nicht veränderte.

Dieses Kapitel beschreibt, was während dieser vierzig Minuten geschah, erklärt für jemanden, der sie nie von Hand ausführen muss, der aber dennoch wissen sollte, was jetzt auf dem Computer läuft—weil ein System, das man nicht versteht, ein System ist, das man nicht vertrauen kann, und ein System, das man nicht vertrauen kann, ist ein System, das man im März aufgeben wird.

Es gibt fünf Dinge zu erklären: die Datenbank, die Python-Umgebung, das ERP, den Connector und den Assistenten. Sie leben in einem Ordner, und wer diesen Ordner kennt, kennt die Installation.

---

## Der Ordner

Alles, was der Installer erstellt, geht an einen Ort:

```
%LOCALAPPDATA%\odoo-tool-stack
```

Auf einem üblichen Windows-Computer ist das `C:\Users\<du>\AppData\Local\odoo-tool-stack`. Darin befinden sich vier Unterordner, je einer pro Komponente, plus die Protokolldateien. Nichts ist über die Fest zerstreut, keine Dateien werden in `Windows` abgelegt, und außer dem Datenbankdienst und zwei Verknüpfungen wird nichts registriert.

Das ist eine bewusste Designentscheidung, und sie hat eine enorme praktische Konsequenz: **Das Deinstallieren ist das Löschen eines Ordners.** Ein Unternehmen, das das System im Januar ausprobiert und im Februar aufgibt, hinterläßt keinen Fossil im Computer für die nächsten fünf Jahre. Es löscht ein Verzeichnis und deinstalliert die Datenbank.

Die eigenen Daten des Benutzers—die Einstellungen des Assistenten, dessen Unterhaltungen, die Konfiguration des Connectors—leben getrennt, in `%LOCALAPPDATA%\agent`, so daß das Aktualisieren oder Neuinstallieren des Stacks sie nicht zerstört.

## Die Datenbank

PostgreSQL wird so installiert, wie PostgreSQL auf Windows installiert werden soll: als Dienst, mit einem eigenen Datenverzeichnis, das auf einem Port lauscht. Der Dienst bedeutet, daß er mit dem Computer startet und ohne jegliches Anmelden läuft; das Datenverzeichnis bedeutet, daß das Gedächtnis des Unternehmens eine Dateiensammlung an einem bekannten Ort ist, was ein Backup überhaupt erst möglich macht.

Der Installer wählte den Port. Er wollte 5432, fand ihn vom Inneren des Windows-Subsystems für Linux belegt und nahm 5433. Dann tat er drei Dinge, die eine Person sonst von Hand tun mußte:

1. Er erstellte einen Datenbankbenutzer namens `odoo`, mit einem Passwort, so daß das ERP nie als Superuser verbindet. Das ist der Unterschied zwischen der Übergabe eines Schlüssels zum Büro an die Buchhalterin und der Übergabe ihres Masterschlüssels zum Gebäude.
2. Er erstellte eine Datenbank namens `odoo`, die Eigentum dieses Benutzers ist.
3. Er schrieb den Port und die Zugangsdaten in die Konfigurationsdatei des ERP.

Das Superuser-Passwort ist `odoo`, es sei denn, die installierende Person wählte etwas anderes, und der Installer gibt es in der Zusammenfassung aus. Es ist ein lokales Konto. Es hat mit keinem Konto im Internet zu tun, und es ist das Passwort, das man benötigen wird, falls man jemals ein Backup von Hand wiederherstellen muß.

## Die Python-Umgebung

Odoo ist in Python geschrieben, und Python-Programme benötigen Bibliotheken. Der Installer erstellt eine isolierte Umgebung—eine *virtuelle Umgebung*—innerhalb des Stack-Ordners und installiert darin genau die Bibliotheken, die Odoo benötigt, auf den Versionen, die Odoo erwartet.

Das Wort „isoliert" leistet hier echte Arbeit. Ohne würde das Installieren von Odoo die Python-Version verändern, die andere Programme auf dem Computer verwenden, und eines Tages würde etwas Unzusammenhängendes aufhören zu funktionieren. Mit ihr trägt der Stack seine eigene Python und kann außerhalb seines Ordners nichts kaputtgehen lassen.

Falls der Computer überhaupt keine nutzbare Python hatte, installierte der Installer zuerst eine—und sie wurde geprüft, indem man sie ausführte, nicht indem man nach ihr suchte, weil auf einem modernen Windows-Computer der Befehl `python` oft eine Werbung für den Microsoft-Store ist statt eines Programms.

## Das ERP

Odoo selbst ist ein Ordner aus Python-Quellcode und eine große Menge an Modulen. Der Installer lud die zu installierende Version herunter, erstellte das Datenbank-Schema und lud die Basismodule—diejenigen, die das Modell eines Unternehmens bereitstellen: Partner, Produkte, Dokumente, das Hauptbuch, die Weboberfläche.

Dies ist der Schritt, der am längsten dauert und am meisten wie ein Nichts-Geschehen aussieht. Es wird eine Datenbank aufgebaut: Hunderte von Tabellen, Tausende von Regeln, das Kontenplan eines allgemeinen Unternehmens, die Steuern eines allgemeinen Landes, die Menüs eines allgemeinen Benutzers. Wenn es fertig ist, ist das ERP ein funktionierendes Programm, das weiß, wie man ein Unternehmen ist, aber noch nicht weiß, welches Unternehmen es ist. Dafür ist die Seite der ersten Schritte da.

## Der Connector

Der Connector ist das kleine Programm, das zwischen dem Assistenten und dem ERP übersetzt. Es wird als Plugin installiert—ein Ordner aus Dateien, die der Assistent beim Start lädt—und es wird mit zwei Fakten konfiguriert: der Adresse des ERP (`http://localhost:8069`) und einem Schlüssel.

Der Schlüssel wird während der Installation erzeugt und in die Konfigurationsdatei des Connectors geschrieben. Es ist ein Odoo-API-Schlüssel: ein Zugangsdatum, das zu einem Benutzer gehört, ohne Änderung des Passworts dieses Benutzers widerrufen werden kann und die Berechtigungen dieses Benutzers mit sich trägt. Wenn der Assistent Odoo auffordert, eine Rechnung zu erstellen, reist именно dieser Schlüssel mit der Anfrage, und Odoo prüft ihn genau so, wie es das Login einer Person prüfen würde.

Dies ist der Teil der Architektur, nach dem der Prüfer eines Unternehmens fragen wird, und die Antwort ist beruhigend: der Assistent ist ein *Benutzer*. Er erscheint in der Benutzerliste des ERP. Er hat eine Rolle. Jedes Record, das er erstellt, wird mit seinem Namen gestempelt. Er kann mit einem einzigen Klick deaktiviert werden, und die Prüfspur wird weiterhin zeigen, was er tat.

## Der Assistent

Der Assistent kommt als öffentliche Veröffentlichung: ein ausführbare Datei, ein Ordner aus Werkzeugen und der Desktop-Chat-Client. Der Installer entpackt ihn, installiert den Connector darin und erstellt die Verknüpfung **AI Odoo**.

Die Verknüpfung ist das Stück, das das System wie ein Produkt wirken lässt statt wie ein
wissenschaftliches Projekt. Ein Doppelklick darauf startet den ERP, wenn er nicht läuft, öffnet die
Startseite im Browser und öffnet den Assistenten in einem Terminalfenster. Ein Symbol, und dann zwei
Fenster: die Seite, die sagt, wo alles liegt, und das schwarze Fenster, in das man tippt. Die Arbeit
kann beginnen.

Die eigene Konfiguration des Assistenten—welcher AI-Anbieter, welches Modell, welcher Schlüssel—wird beim ersten Start abgefragt, vom Assistenten selbst, im selben Terminalfenster, in dem man seine Anweisungen tippen wird. Das ist ein guter Ort, um zu fragen, weil es der einzige Ort ist, an dem der Schlüssel tatsächlich getestet werden kann: der Assistent ruft die Modellliste des Anbieters mit dem Schlüssel ab, den man eingefügt hat, und wenn die Liste zurückkommt, funktioniert der Schlüssel.

---

## Was schiefgehen konnte

Alles Obige funktionierte beim zweiten Versuch. Es lohnt sich aufzulisten, was beim ersten schiefging, weil jeder Punkt ein Ort ist, an dem ein Unternehmen, das dies real installiert, einen Nachmittag verliert, und jeder wurde behoben statt als bekanntes Problem dokumentiert.

**Der Download, der von vorne begann.** Im vorherigen Kapitel beschrieben: der Installer löschte seinen teilweisen Download vor jedem Wiederholungsversuch, so daß eine langsame Leitung drei Fehler statt eines langsamen Erfolgs bedeutete. Behoben durch das Beibalten des teilweisen Datei, das Nachbenennen nach seiner Version und das Fortsetzen.

**Eine Versionsliste, die veraltet.** Der Installer kannte die Dateinamen von drei aktuellen PostgreSQL-Builds. Der Hersteller hatte einen vierten veröffentlicht, der nicht auf der Liste stand. Ein Leser, der in sechs Monaten installiert, hätte auf eine Liste von Dateien gestoßen, die nicht mehr existieren. Behoben durch das Hinzufügen des aktuellen Builds und durch einen Fehlermeldung, die exakt sagt, welche Datei von Hand abgerufen werden soll.

**Die Meldung des Paketmanagers in der Sprache des Computers.** Wenn `winget` fehlschlägt, erklärt es warum in der Sprache von Windows. Der Installer wiederholte die letzten zweihundert Zeichen dieser Erklärung, und auf einer Konsole, deren Code-Seite nicht UTF-8 ist, kamen die akzentierten Buchstaben als Müll an—so zeigte der Bildschirm ein Fragment Italienisch, verstümmelt, in der Mitte einer englischen Installation. Zweimal behoben: die Konsole ist jetzt auf UTF-8 eingestellt, und der Installer wiederholt den Text des Paketmanagers nicht mehr. Der Exit-Code ist die Tatsache; die nächste Zeile sagt, was stattdessen geschieht.

**Stille während der Datenbankinstallation.** Die eigene Installation der Datenbank läuft ohne Ausgabe, so daß der Bildschirm mehrere Minuten still steht. Dieser ist nicht behoben, weil die Behebung darin bestehen würde, eine Fortschrittsleiste zu erfinden, die lügt. Stattdessen ist sie dokumentiert, hier und im Anhang: Wenn der Bildschirm seit fünf Minuten nicht mehr gewechselt hat, sieht man im Ordner `C:\Program Files\PostgreSQL` nach—wenn er wächst, läuft die Installation.

Keines dieser Probleme ist dramatisch. Zusammen sind sie der Unterschied zwischen einem Verfahren, das eine nicht-technische Person bei einer schlechten Verbindung abschließen kann, und einem, das mit einem Support-Ticket endet.

---

## Die zwei Dateien, die es wert sind, verstanden zu werden

Innerhalb des Connector-Ordners gibt es zwei kleine Dateien, und sie sind die einzige Konfiguration, die ein Unternehmen wahrscheinlich berühren wird.

**`odoo.json`** hält die Adresse des ERP, den Datenbanknamen und den Schlüssel. Es sind vier Zeilen Text. Verschiebt sich das ERP auf einen anderen Port, ist dies die Datei, die verändert wird; wird der Schlüssel widerrufen, ist dies die Datei, die den neuen erhält.

**`toolset.json`** hält die Liste der Werkzeuge, deren sich der Assistent bedienen darf. Dies ist die Datei, die entscheidet, ob der Assistent eine Datei berühren, das Web durchsuchen oder nur mit dem ERP sprechen darf. Es ist die einzelne wichtigste Sicherheitseinstellung der ganzen Installation, und es ist eine Zeile Text.

Rivertons erste Woche ergab eine Lektion über diese zweite Datei, die es wert ist, erzählt zu werden, weil sie die Art von Dingen ist, die kein Handbuch vorhersagt.

Der Installer hatte vier Werkzeuge aktiviert: den ERP-Connector, ein Datei-Werkzeug, ein Web-Werkzeug und ein Versionswerkzeug. Das ist ein vernünftiger Standard für einen allgegenwärtigen Assistenten. Aber die erste Anweisung, die das Unternehmen gab—*erstelle einen Kunden namens Ashfield Academy, Mill Lane, Ashfield*—wurde vom Assistenten beantwortet, indem er ging, die Adresse im Internet nachzuschlagen, weil ein Web-Werkzeug verfügbar war und eine Adresse eine Sache ist, die man nachschlägt.

Es war nicht falsch, genau genommen. Es war unaufschlüssam, es war langsam, und es benutzte ein Werkzeug, über das das Unternehmen nicht nachgedacht hatte. Die Behebung nahm eine Zeile in Anspruch: die Werkzeugliste wurde auf den Connector und das Datei-Werkzeug beschnitten, und der Assistent hörte mit dem Durchsuchen auf und begann, das ERP zu befragen.

Das ist eine Designentscheidung, die jedes Unternehmen treffen muß, und der Standard sollte der enge sein. Ein Assistent mit einem Werkzeug, das er nicht benötigt, ist ein Assistent, der es irgendwann benutzen wird, zum schlechtestmöglichen Zeitpunkt, aus einem Grund, der einem Sprachmodell vernünftig erschien.

Es gibt jedoch eine bessere Antwort als das Beschränken der Liste, und sie ist die, welche dieses Buch empfiehlt.

Ein Sprachmodell wählt ein Werkzeug, indem es liest, wofür das Werkzeug laut eigener Aussage dient. Wenn sich der ERP-Connector als *Abfragen und Verwalten von Odoo-ERP-Daten* beschreibt und nichts weiter, dann ist eine Anweisung, die die Wörter „Kunde" und „Adresse" enthält, ein fairer Treffer für eine Websuche—eine Adresse ist schließlich eine Sache, die man nachschlägt. Das Modell ist nicht dumm; es ist wörtlich bezüglich zweier gleichermaßen plausibler Beschreibungen.

Die Behebung ist ein Satz in der eigenen Beschreibung des Werkzeugs, an der Stelle, die das Modell tatsächlich liest: *dieses Werkzeug ist das System of Record des Unternehmens: für jede Frage oder jede Handlung über Kunden, Lieferanten, Produkte, Preise, Verkäufe, Käufe, Rechnungen, Zahlungen oder Lagerbestand benutze diese Methoden statt einer Websuche, einer Datei oder allgemeinem Wissen; schlage ein benanntes Record hier zuerst nach, und sage es, wenn es hier nicht ist.*

Dieser Satz wurde hinzugefügt, die vier Werkzeuge wurden wieder eingesetzt, und das Verhalten änderte sich: dieselbe Installation, mit dem Datei-Werkzeug, dem Web-Werkzeug und dem Versionswerkzeug allesamt aktiviert, beantwortet nun „wie viele Kunden haben wir" aus dem ERP, in einer Sekunde, mit dem Kriterium, das es verwendete, und den Records hinter der Zahl.

Zwei Lehren, und sie zeigen in entgegengesetzte Richtungen.

**Für das Unternehmen:** Löse kein Routing-Problem, indem man Werkzeuge wegnimmt. Ein reales Büro benötigt das Web, die Dateien und das ERP gleichzeitig; ein Assistent, der zur korrekten Handlung gekröpft wurde, ist ein Assistent, der am Tag versagen wird, an dem die Arbeit das von dir weggommene Werkzeug benötigt.

**Für jenen, der das Werkzeug schreibt:** Die Beschreibung ist die Schnittstelle. Sie wird vom Modell bei jeder Wendung gelesen, sie kostet nichts, und ein einzelner Satz über *wann man dies benutzt und wann nicht* ist mehr wert als jegliche Prompt-Engineering in der Anweisung. Die Regeln, die zählen, gehören in die Zusammenfassung des Werkzeuges, in kurzen imperativen Zeilen—nicht in ein Handbuch, und nicht in eine Anmerkung, die das Modell nie sieht.

## Die Gestalt der Sache

Wenn der Installer fertig war, hatte Riverton fünf Programme dort, wo einst ein Aktenschrank stand.

Eine Datenbank, die sich erinnert. Ein ERP, das weiß, was die Fakten bedeuten. Eine Python-Umgebung, die das ERP ausführt. Ein Connector, der übersetzt. Ein Assistent, der handelt. Und ein Ordner, der alles hält und gelöscht werden kann.

Maggie schrieb den Pfad des Ordners auf das Blatt Papier, unter dem Passwort, und sah einen Moment lang darauf. Es war ein seltsames Gefühl, einunddreißig Jahre Papier durch ein Verzeichnis in ihrem Benutzerprofil ersetzt zu haben—als wäre das Gedächtnis des Unternehmens eine Sache geworden, die in vier Minuten auf einen USB-Stick kopiert werden konnte.

Es konnte tatsächlich in vier Minuten auf einen USB-Stick kopiert werden. Das ist es, was ein Backup ist, und es ist der Gegenstand eines Gesprächs, das sie drei Wochen später mit Sam führen würde, nach der ersten Beängstigung.

Aber vor den Backups, vor den Rechnungen, vor irgendeiner der Arbeiten gab es eine Seite im Browser, die fragte, welche Währung das Unternehmen verwendet.

---

## Die erste Beängstigung, und was ein Backup tatsächlich ist

Die Beängstigung kam an einem Donnerstag, drei Wochen später, und sie war kein Absturz.

Maggie hatte den Assistenten eine Frage gestellt—wie viel haben letzten Monat in Rechnung gestellt?—und die Antwort war kleiner als erwartet. Nicht falsch, genau genommen: kleiner. Sie prüfte die Rechnungsliste, und es waren weniger Rechnungen vorhanden als sie sich zu genehmigen erinnerte.

Die Ursache, als Sam sie fand, war unschuldig: Doreen hatte mit einem Filter in der Rechnungsliste experimentiert, und der Filter war angeschaltet geblieben. Der Assistent hatte die Frage beantwortet, die ihm gestellt wurde, gegen die Liste, die ihm gegeben wurde, und die Liste war gefiltert. Nichts wurde gelöscht. Nichts wurde verloren.

Aber zwanzig Minuten lang glaubte Maggie, drei Wochen von Rechnungsstellung seien verschwunden, und das Gefühl dieser zwanzig Minuten ist es, worum es in diesem Abschnitt geht. Weil die zweite Frage, die sie stellte, bevor sie Sam irgendetwas fragte, lautete: *haben wir ein Backup?*

Die Antwort, an diesem Tag, war: nicht wirklich. Es gab eine Kopie des Ordners vom Tag der Installation, gemacht vom Installer selbst, und nichts seitdem.

Was ein Backup in einem System wie diesem ist, sind drei Dinge und nicht eines.

**Die Datenbank.** Ein Dump von allem, was das ERP weiß, gemacht mit dem eigenen Werkzeug der Datenbank, auf einem Zeitplan. Es ist eine einzelne Datei, sie kann in eine leere Installation wiederhergestellt werden, und sie ist die einzige Kopie, die für das Hauptbuch zählt.

**Der Ordner.** Das ERP-Quellcode, die Konfiguration, die Einstellungen des Assistenten, der Schlüssel des Connectors. Klein, und mühsam, von Hand neu zu erstellen, was genau der Grund ist, warum es sich lohnt, es zu kopieren.

**Die Prüfung.** Einmal im Monat die Wiederherstellung des Backups in einer Versuchs-Installation und ein Hinsehen darauf. Ein Backup, das nie wiederhergestellt wurde, ist eine Datei mit einem hoffnungsvollen Namen. Martins Regel—*ein unverifiziertes Backup ist ein Wunsch*—stammte davon, ein Unternehmen beim schleiestmöglichen Moment dabei beobachtet zu haben, wie sein nächtlicher Auftrag auf eine volle Festplatte schrieb.

Die Werkzeuge für alle drei befinden sich im Stack-Ordner: ein Skript, das die Datenbank dumpft, ein Ordner zum Kopieren, und ein Dokument mit den vier Befehlen zur Wiederherstellung. Rivertons Version läuft um zwei Uhr nachts, bewahrt dreißig Tage, und schreibt in einen Ordner, den OneDrive synchronisiert. Es kostete Sam eine Stunde, es einzurichten, und es ist mit weitem Abstand die billigste Versicherung, die das Unternehmen je gekauft hat.
