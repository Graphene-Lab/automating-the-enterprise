# 22. Arbeit, die läuft, während Sie schlafen

Der erste geplante Job, den Riverton einrichtete, war nicht klug. Es war die Montag-Liste.

Jeden Montag um acht produziert der Assistent eine Seite: Rechnungen, die in der
vorherigen Woche überfällig wurden, Produkte, die unter ihren Nachbestellpunkt gefallen sind,
Aufträge, die für die Lieferung in den nächsten sieben Tagen anstehen, und alle
Lageranpassungen ohne dokumentierten Grund. Er sendet sie an Maggie, Priya und Tom als
E-Mail, und der Assistent braucht etwa vierzig Sekunden.

Niemand hat darum gebeten. Es war Sams Idee, und er erklärte sie mit einem Satz, der
Maggie seither begleitet.

"Der Sinn eines Zeitplans ist nicht, dass die Maschine läuft, während Sie schlafen. Er ist,
dass die *Frage* gestellt wird, ob nun jemand daran denkt, sie zu stellen."

---

## Zwei Arten von geplanter Arbeit

Es gibt zwei Mechanismen in diesem Stack, und es lohnt sich, sie zu unterscheiden, weil sie
unterschiedliche Fragen beantworten.

**Die eigenen Scheduler des ERP** laufen innerhalb von Odoo. Es sind die Dinge, die ein
Geschäftssystem seit jeher zeitgesteuert erledigt: Neuberechnung der Nachbestellpunkte,
Versenden der Erinnerungsmails, Lauf der Abschreibung, Aufräumen alter Sitzungen. Sie werden im
ERP konfiguriert, sie laufen, ob nun der Assistent geöffnet ist oder nicht, und sie sind der
richtige Ort für alles, was zum *Modell* gehört—alles, was hätte passieren müssen, selbst wenn
niemand im Unternehmen Interesse hätte.

**Der Task-Scheduler des Assistenten** führt Jobs als Unterhaltungen aus. Eine geplante
Aufgabe ist, wörtlich, ein Prompt mit einem Datum daran: um acht Uhr am Montag wird dem
Assistenten eine Anweisung gegeben, er erledigt die Arbeit, und er berichtet. Das ist der
richtige Ort für alles, was Urteil über *was zu betrachten ist* erfordert—eine Zusammenfassung,
ein Rundgang, ein Vergleich, ein Anstoß.

Riverton nutzt beide, und die Trennung zwischen ihnen ist der nützliche Teil dieses
Kapitels.

## Was in einen Zeitplan gehört

Die Versuchung, wenn man geplante Arbeit entdeckt, ist es, alles zu planen. Widersteht ihr und
nutzt einen Test, der leicht anzuwenden ist: **Ein Job gehört in einen Zeitplan, wenn seine
Abwesenheit nur bemerkt würde, wenn es zu spät ist.**

Die Montag-Liste besteht den Test. Ohne sie wird eine überfällige Rechnung bemerkt, wenn
jemand denkt, nachzusehen—was heißt: wenn sie sechzig Tage alt ist.

Eine nächtliche Sicherung besteht den Test, katastrophal.

Ein tägliches "Verkaufsbericht" schlägt ihn meist fehl. Niemand liest ihn; die Zahl steht im
Dashboard; und ein Bericht, den niemand liest, ist eine kleine tägliche Steuer auf Aufmerksamkeit,
die Menschen schließlich beibringt, Nachrichten des Systems zu ignorieren.

Der Test hat eine Folgerung: **Ein geplanter Job sollte eine Entscheidung erzeugen, kein
Dokument.** Die Montag-Liste erzeugt vier Entscheidungen (verfolge diese, bestelle das nach,
liefere dies, erkläre jenes). Ein Bericht erzeugt ein Dokument, und Dokumente häufen sich.

## Die drei Jobs, die Riverton behielt

Nach einem Monat des Experimentierens einigte sich das Unternehmen auf drei, und es hat sie
seitdem behalten.

**Die Montag-Liste**, um acht. Vier Fragen, eine Seite, drei Empfänger.

**Der Freitag-Lagercheck**, um vier. Der Assistent listet jedes Produkt auf, das während der
Woche unter seinen Nachbestellpunkt gefallen ist, und schläft Aufträge vor—im Entwurf, niemals
bestätigt. Tom liest sie am Freitagnachmittag und entscheidet; die Aufträge werden am Montagmorgen
aufgegeben, wenn die Lieferanten ans Telefon gehen.

**Die Zusammenfassung zum Monatsanfang**, um sieben. Verkäufe nach Kunde, Verkäufe nach
Produkt, die fünf besten und die fünf schlechtesten nach Marge, Geld rein und raus, und die drei
Kunden, deren Zahlungsverhalten sich verändert hat. Sie ist zwei Seiten lang, und sie ist das
Dokument, das Maggie mit ihrem ersten Kaffee des Monats liest.

Alles andere, das in diesem Monat versucht wurde, wurde gelöscht, und die Löschungen sind so
lehrreich wie die Behaltenen: eine tägliche Zusammenfassung (niemand las sie), ein stündlicher
Verbindungscheck (er erzeugte Lärm, keine Information) und ein nächtlicher "Doppelte löschen"-
Job, der eine wirklich schlechte Idee war—eine Maschine, die um drei in der Früh entscheidet,
welche von zwei Kundenregistrierungen real ist, mit niemandem, der zusieht.

## Was passiert, wenn ein Job fehlschlägt

Der interessante Teil der geplanten Arbeit ist nicht der Zeitplan. Es ist der Ausfall.

Ein Job kann aus drei Gründen fehlschlagen, und jeder hat eine andere Signatur.

**Die Maschine war aus.** Das ERP lief nicht um acht Uhr, also lief der Job nicht. Odos
eigene Scheduler erledigen verpasste Jobs, wenn der Server startet; die geplanten Aufgaben des
Assistenten werden als Pläne gespeichert und beim nächsten Start ausgeführt, mit dem Datum, an
dem sie hätten laufen sollen. Wie auch immer, die Arbeit geschieht, verspätet.

**Der Job lief und die Antwort war falsch.** Das ist der gefährliche, weil nichts kaputt
aussieht. Die Montag-Liste kommt, und einer ihrer vier Abschnitte ist leer, weil ein Filter
eingelassen wurde. Die Verteidigung ist dieselbe wie überall sonst in diesem Buch: die Liste sagt,
*was sie betrachtet hat*, nicht nur, was sie gefunden hat. Ein leerer Abschnitt, der sagt
"keine Rechnung wurde in der Woche bis zum 14. November überfällig", ist Information; ein leerer
Abschnitt ohne Erklärung ist eine Frage.

**Der Job lief und niemand las ihn.** Das ist der häufigste Ausfall und der am wenigsten
besprochene. Ein geplanter Job, der in einem Postfach ankommt, das niemand öffnet, ist schlimmer
 als kein Job überhaupt, weil er den *Eindruck* von Kontrolle erzeugt. Sons Antwort war, aus der
Montag-Liste ein Meeting zu machen—fünfzehn Minuten, drei Personen, die Liste auf dem Bildschirm—
was nach Bürokratie klingt und in Wirklichkeit die billigst mögliche Art ist, die Automatisierung
real zu machen.

## Eine kurze Geschichte des Batch-Jobs

Geplante Arbeit ist älter als der Personalcomputer, und ihr Vokabular kommt vom Großrechner.

In den 1960er Jahren war ein Computer zu teuer, um eine Person daran sitzen zu lassen, also
wurde Arbeit auf Karten vorbereitet und nachts in *Batches* ausgeführt: Gehaltsabrechnung am
25., Rechnungen am 1., das Hauptbuch zum Monatsende. Der Batch war eine Warteschlange, und die
Aufgabe des Bedieners war es, die Warteschlange in Bewegung zu halten. Wenn Minicomputer in den
1970er Jahren kamen, überlebte der Batch als `cron`—ein Unix-Programm, 1975 geschrieben von Ken
Thompson, dessen Name von *chronos* kommt, Zeit—und `cron` ist immer noch das, was die Server der
Welt antreibt, indirekt also auch den Scheduler innerhalb Ihres ERP.

Was neu ist, ist nicht der Timer. Es ist *was* darauf läuft. Ein Batch-Job von 1975 war ein
Programm, das ein Programmierer schrieb, um genau eine Sache zu tun. Eine geplante Aufgabe von
2026 ist ein Satz in Englisch, und die Maschine ermittelt die Schritte jedes Mal, wenn sie läuft.
Das ist eine andere Art von Automatisierung, und sie braucht eine andere Art von Aufsicht: Das
Programm tat, wofür es geschrieben wurde, jedes Mal; der Satz kann unterschiedlich interpretiert
werden, wenn sich die Daten ändern.

Deshalb ist die erste Regel der geplanten Arbeit in diesem Buch: **Planen Sie Fragen, nicht
Aktionen.** Die Montag-Liste fragt. Der Freitag-Lagercheck schlägt vor. Die Zusammenfassung zum
Monatsanfang berichtet. Keiner von ihnen bucht eine Rechnung, sendet einen Brief an einen Kunden
oder gibt einen Auftrag auf, denn das sind Entscheidungen mit Konsequenzen, und eine Entscheidung,
die um drei in der Früh von einer Maschine getroffen wird, die niemand sieht, ist keine
Entscheidung—es ist eine Wette.

## Die eine Ausnahme

Es gibt einen geplanten Job bei Riverton, der tatsächlich handelt, und es lohnt sich, ihn zu
beschreiben, weil er zeigt, wo die Linie verläuft.

Jeden Nachts um zwei nimmt das System eine Sicherung: ein Dump der Datenbank, eine Kopie der
Konfiguration und eine Zeile in einem Log. Es handelt. Es verändert die Welt, in dem Sinne, dass
Dateien erscheinen. Und es darf handeln, weil die Aktion *von Design aus reversibel* ist: eine
Sicherung, die falsch ist, kann gelöscht und erneut gemacht werden, und nichts im Geschäft hängt
davon ab, dass sie stattgefunden hat, bis zu dem Tag, an dem es doch tut.

Das ist der Test für jeden geplanten Akt: Kann ich ihn, wenn er um drei in der Früh falsch läuft,
wieder rückgängig machen, bevor jemand es merkt? Wenn ja, kann er geplant werden. Wenn nein, kann
er vorschlagen, und eine Person kann entscheiden.

## Die Kosten eines Zeitplans, den niemand besitzt

Ein geplanter Job ist ein kleines Versprechen, und Versprechen brauchen einen Eigentümer.

Der Ausfall ist leise und er ist häufig: Ein Job wird von jemandem eingerichtet, der dann
geht, oder eine Rolle wechselt, oder einfach vergisst. Er läuft weiter. Sechs Monate später
erzeugt er einen Bericht mit einem Filter, der im März noch richtig war, oder schlägt Aufträge für
eine Produktlinie vor, die das Unternehmen eingestellt hat, und niemand merkt es, weil niemand ihn
liest—bis jemand es tut und ihm vertraut.

Das Mittel ist eine Liste, geführt in derselben Datei wie die Prompts: jeder geplanter Job, was
er tut, wer ihn liest, und wann er zuletzt überprüft wurde. Vier Spalten, eine Seite, zweimal im
Jahr überprüft. Ein Job, für den niemand einen Namen als Eigentümer nennen kann, ist ein Job zum
Löschen.

Rivertons Liste hat drei Einträge und einen vierten, der eine Erinnerung ist, die Liste zu
überprüfen. Sie ist das unbeeindruckendste Dokument im Unternehmen und sie hat zwei schlechte
Entscheidungen verhindert, beide von einer Maschine getroffen, die genau tat, was man ihr
aufgetragen hatte.

## Wo der Zeitplan lebt, und was passiert, wenn die Maschine aus ist

Eine geplante Aufgabe ist eine Datei, und zu wissen, wo sie lebt, ist der Unterschied zwischen
einem Zeitplan, den Sie besitzen, und einem Zeitplan, dem Sie ausgeliefert sind.

Der Assistent speichert seine Pläne als JSON, in seinem eigenen Datenordner, und sie überleben
einen Neustart. Jeder Plan ist ein Satz, eine Zeit, eine Wiederholung und eine Liste von zu
Erledigendem mit dem Ergebnis. Das lohnt sich aus zwei Gründen zu wissen: man kann es mit dem
Rest der Konfiguration sichern, und man kann es einsehen—was heißt, ein Unternehmen kann die Frage
*was tut diese Maschine um acht Uhr am Montag?* beantworten, indem es eine Datei liest, statt zu
merken.

Die eigenen Scheduler des ERP leben in der Datenbank, in einer Tabelle der geplanten Aktionen,
und sie sind in der Oberfläche unter *Einstellungen → Technisch → Geplante Aktionen* sichtbar.
Jeder hat einen Namen, ein Intervall und eine Anzahl, wie oft er已 gelaufen ist. Diese Anzahl ist
ein kleines aber ausgezeichnetes Diagnosemittel: ein Job, der vierhundertmal gelaufen ist, und ein
Job, der nullmal gelaufen ist, sagen Ihnen unterschiedliche Dinge, und beide lohnt es sich einmal
pro Quartal anzusehen.

Wenn die Maschine aus ist, können drei Dinge passieren, und das Verhalten des ERP ist das
Sinnvolle.

**Odos Scheduler** erledigen verpasste Jobs beim nächsten Start, in der Reihenfolge, und sie
verzeichnen die Tatsache. Eine Erinnerung, die um acht fällig war, geht um neun raus, und das Log
wird das so verzeichnen.

**Die Aufgaben des Assistenten** werden beim Start geprüft: wenn der nächste Lauf eines Plans in
der Vergangenheit liegt, läuft er sofort und plant sich selbst neu. Eine Montag-Liste, die
verpasst wurde, weil die Maschine aus war, kommt am Dienstag, mit den Daten, wie sie am Dienstag
sind—was ein subtiler und wichtiger Unterschied ist. Die Liste ist nicht "was am Montag
passierte"; sie ist "was jetzt gilt, gefragt zum Zeitplan, der für Montag gedacht war".

**Eine Sicherung**, die verpasst wurde, ist einfach verpasst, und die nächste deckt die Lücke.
Das ist für eine nächtliche Sicherung akzeptabel; es ist nicht akzeptabel für eine wöchentliche
auf einer Maschine, die oft aus ist, weshalb das Sicherungsskript eine Zeile in einem Log schreibt
und das Log monatlich geprüft wird.

## Wenn ein Job Lärm erzeugt

Der Ausfallmodus, der geplante Arbeit tötet, ist kein Absturz. Es ist Lärm.

Ein Job, der eine Nachricht erzeugt, die niemand liest, trainiert Menschen, Nachrichten des
Systems zu ignorieren, und dann wird auch diejenige ignoriert, die wichtig ist. Riverton versuchte
vier Zeitpläne im ersten Monat und löschte drei, und die Löschungen waren so Lehrreich wie die
Behaltenen.

**Die tägliche Zusammenfassung** wurde gelöscht, weil sie das Dashboard duplizierte und zu einer
Zeit ankam, zu der niemand am Schreibtisch war. Die Information war nicht falsch; die Zustellung.

**Der stündliche Verbindungscheck** wurde gelöscht, weil er jede Stunde Erfolg meldete. Eine
Nachricht, die sagt *alles ist in Ordnung*, ist keine Information; sie ist ein Gewohnheit, und
Gewohnheiten sind es, die Menschen aufhören lassen zu lesen.

**Der nächtliche Doppelten-Check** wurde gelöscht, weil er eine Aktion war, die niemand
autorisiert hatte, zu einer Zeit laufend, die niemand ansah, an Daten, die niemand aufgeräumt
hatte. Er fand drei Wochen lang nichts und schlug dann vor, zwei Kunden zusammenzuführen, die in
Wirklichkeit zwei Zweige derselben Organisation waren.

Die drei, die überlebten, teilen alle eine Eigenschaft: Sie erzeugen eine *Entscheidung*, die ein
benannter Mensch zu einer benannten Zeit trifft. Die Montag-Liste wird am Montag-Meeting gelesen.
Der Freitag-Lagercheck wird von Tom gelesen, bevor er geht. Die monatliche Zusammenfassung wird
mit dem ersten Kaffee des Monats gelesen.

Ein Zeitplan ohne Leser ist ein cron-Job mit einem Hobby.

---

Die Montag-Liste läuft seit acht Monaten, und Maggie hat sie doppelt verpasst—beide Male, weil
sie gereist war, und beide Male hat sie sie am Dienstag gelesen und sich gewünscht, sie hätte sie
am Montag gelesen.

"Es ist nicht die Information," sagt sie. "Die Information könnte ich bekommen. Es ist nur, dass
am Montagmorgen, bevor sonst etwas passiert, jemand vier Fragen vor mich stellt. Und es sind die
richtigen vier Fragen. Ich würde nie darauf kommen, sie um acht Uhr am Montag zu stellen. Ich
würde sie um vier Uhr am Freitag überdenken, wenn es zu spät ist, irgendetwas zu tun."

Das ist der echte Wert der geplanten Arbeit, und es hat nichts mit Maschinen zu tun, die laufen,
während Sie schlafen. Es ist, dass die *Frage* eine Zeit hat, und die Zeit wird von jemandem
gewählt, der einmal darüber nachgedacht hat, sorgfältig, statt von jenem, der zufällig im Moment
besorgt ist.
