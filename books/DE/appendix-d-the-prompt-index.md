# Anhang D — Der Prompt-Index

Jede Anweisung, die in diesem Buch vorkommt, an einem Ort, mit dem Kapitel, in dem sie verwendet wird, und mit dem, was sie erzeugt. Sie ist dazu da, um überflogen zu werden, statt gelesen zu werden: Finde die Frage, die du hast, und sieh dir die Anweisung an, die sie beantwortet.

Die Anweisungen sind so geschrieben, wie sie getippt wurden, in der Sprache eines Büros. Namen von Kunden und Produkten sind von Riverton; ersetze sie durch deine eigenen.

## Fragen zu Kunden

| Anweisung | Erzeugt | Kapitel |
|---|---|---|
| Wie viele Kunden haben wir, und wie viele haben in den letzten neunzig Tagen eine Bestellung aufgegeben? | zwei Zahlen, wobei die zweite die nützlichere ist | 13 |
| Finde den Kunden namens Ashfield Academy und zeig mir ihre Adresse, Telefonnummer und Zahlungsbedingungen. | der Datensatz, in der Form eines Telefonats | 13 |
| Lege einen Kunden namens Ashfield Academy an, in der Mill Lane, Ashfield, mit 30-Tage-Zahlungsbedingungen. | ein neuer Datensatz, plus ein Duplikatscheck | 13 |
| Füge einem zweiten Kontakt zu Ashfield Academy hinzu: Carol Whitfield, Finanzbüro, Rechnungsanschrift. | ein am Kunden gekoppelter Kontakt | 26 |
| Welche Kunden haben in den letzten sechs Monaten nichts bestellt, und was war ihre letzte Bestellung? | die Liste der ruhigen Kunden | 20, 26 |
| Zeig mir die zehn Kunden mit dem höchsten insgesamt in Rechnung gestellten Betrag in diesem Jahr. | eine Rangliste mit Summen | 26 |
| Welche Kunden haben uns Geld schuldig und haben zugleich mit der Bestellung aufgehört? | die Risikoliste, annotiert | 20, 26 |

## Angebote und Bestellungen

| Anweisung | Erzeugt | Kapitel |
|---|---|---|
| Lege ein Angebot für Ashfield Academy über 400 Ringbuchmappen und 20 Packungen Stifte an, zu den Vertragspreisen, Lieferung Ende nächster Woche. | ein Entwurfangebot mit Positionen, Steuer und einem Datum | 14 |
| Zeig mir das Angebot, das ich heute für Ashfield Academy angelegt habe, mit seinen Positionen und seiner Summe. | die Prüfung | 14 |
| Ändere die Mappenmenge auf 350 und bestätige die Bestellung. | eine bestätigte Bestellung mit reserviertem Bestand | 14 |
| Welche Bestellungen sind in den nächsten drei Tagen zur Lieferung fällig, und reicht der Bestand für alle? | ein Lieferplan mit Bestandswarnungen | 14 |
| Wie groß ist der Gesamtwert aller Angebote, die noch offen sind, und für wen sind sie? | die Pipeline | 26 |
| Welche Produkte haben wir letzten Monat nach Menge am meisten verkauft? | eine Rangliste | 26 |
| Stelle das Angebot für Northgate Library Service aus und sage mir, in welchem Zustand es jetzt ist. | ein gestelltes Dokument, mit bestätetem Zustand | 26 |

## Rechnungsstellung und Eingänge

| Anweisung | Erzeugt | Kapitel |
|---|---|---|
| Welche gelieferten Bestellungen dieser Woche sind noch nicht in Rechnung gestellt? | die Kandidatenliste der Rechnungsaufläufe | 15 |
| Lege Rechnungen aus jeder noch nicht in Rechnung gestellten Lieferung an, lasse sie im Entwurf, und gib mir die Liste mit Summen. | der wöchentliche Lauf | 15 |
| Buche die Ashfield-Academy-Rechnung und sag mir ihre Nummer und ihre Summe. | eine gebuchte Rechnung mit einer fortlaufenden Nummer | 15 |
| Welche Rechnungen sind unbezahlt und mehr als dreißig Tage alt? | das Alterungsreport | 20 |
| Erfasse eine Zahlung des vollen Betrags auf die Rechnung INV/2026/0007, von heute, per Banküberweisung. | eine Zahlung, abgeglichen | 17, 26 |
| Lege einen Gutschriftzettel über 20 zurückgegebene, beschädigte Ringbuchmappen an und buche ihn. | eine Gutschrift, mit erhaltener Originalrechnung | 15 |
| Wie viel Geld ist uns insgesamt schuldig, und wie viel davon ist überfällig? | zwei Zahlen | 26 |
| Sende eine höfliche Zahlungserinnerung an jeden Kunden mit einer mehr als fünfzehn Tage überfälligen Rechnung. | Entwurfe, oder gesendete Briefe, je nach Konfiguration | 20 |
| Welche Kunden zahlen einen Preis, der seit Januar unverändert ist, und was würde es uns kosten, ihn um drei Prozent zu erhöhen? | eine Preisprüfung | 14 |

## Bestand

| Anweisung | Erzeugt | Kapitel |
|---|---|---|
| Wie viele Ringbuchmappen haben wir gerade auf Lager, und wo sind sie? | da, reserviert, verfügbar, nach Lagerort | 16 |
| Welche Produkte liegen unter ihrem Nachschuppunkt? | die Nachschupliste | 17, 22 |
| Bestätige die Lieferung der Ashfield-Academy-Bestellung und sag mir, welche Bestandsveränderungen sie erzeugt hat. | eine validierte Lieferung und ihre Veränderungen | 16 |
| Erfasse eine Bestandskorrektur um minus 5 Packungen Whiteboard-Stifte, Grund: im Regen beschädigt. | eine Korrektur mit einem Grund | 26 |
| Wie groß ist der Gesamtwert des Bestands im Lager zu Einkaufspreisen? | die Bestandsbewertung | 26 |
| Zeig mir jede Bestandsveränderung der Ringbuchmappen in den letzten dreißigen Tagen. | die Prüfung eines Produkts | 16 |
| Welche Produkte haben in dem letzten Jahr gar keine Bewegung gehabt? | toter Bestand | 26 |

## Einkauf

| Anweisung | Erzeugt | Kapitel |
|---|---|---|
| Lege eine Bestellung über 500 Ringbuchmappen und 200 Packungen Stifte bei unseren üblichen Lieferanten an, zum letzten Preis, den wir gezahlt haben, bestätige sie nicht. | Entwurfsbestellungen, nach Anbieter geteilt | 17 |
| Bestätige die Bestellung und sag mir, wann mit der Ware zu rechnen ist. | eine bestätigte Bestellung und ein zu erwartender Eingang | 17 |
| Nimm die Ware für die Bestellung an und zeig mir den Bestand, den sie hinzugefügt hat. | ein Eingang und seine Bestandsveränderungen | 17 |
| Lege die Lieferantenrechnung für diese Bestellung an und vergleiche sie mit der Bestellung und dem Eingang. | eine Rechnung, dreifach abgeglichen | 17 |
| Welche Lieferanten haben in den letzten sechs Monaten ihre Preise erhöht, und um wie viel? | die schleichende-Preise-Liste | 17 |
| Wie viel schulden wir jedem Anbieter gerade? | die Gläubigerliste | 26 |
| Welche Bestellungen sind spät, und um wie viele Tage? | die Liste der späten Lieferung | 26 |

## Buchhaltung

| Anweisung | Erzeugt | Kapitel |
|---|---|---|
| Zeig mir die Bilanzprüfung für diesen Monat. | der älteste Report der Buchhaltung | 19 |
| Wie hoch ist das Guthaben des Bankkontos heute, laut den Büchern? | das Buchguthaben | 26 |
| Die Kontenabstimmung hat sechs nicht abgeglichene Zeilen. Was sind sie? | sechs Geschichten, eine pro Zeile | 21 |
| Zeig mir jede am Tag gebuchte Buchungsschrift der letzten sieben Tage, mit dem Dokument, aus dem sie kam. | eine Spur von der Nummer zum Dokument | 26 |
| Wie hoch ist unser Umsatz für diesen Monat bis jetzt, und wie vergleicht er sich mit dem letzten Monat? | zwei Zahlen und ein Vergleich | 26 |
| Liste die für diese Firma konfigurierten Steuern und den Satz jeder auf. | die Steuerliste | 26 |

## Berichterstattung und Analyse

| Anweisung | Erzeugt | Kapitel |
|---|---|---|
| Gib mir eine einseitige Zusammenfassung des Betriebs dieser Woche: Verkäufe, Rechnungen, überfälliges Geld, Bestandswarnungen. | die Montageliste | 22 |
| Welche fünf Produkte haben die beste Marge, und welche fünf die schlechteste? | die Margen-Rangliste | 26 |
| Zeig mir die Verkäufe nach Monat für dieses Jahr, als Tabelle. | eine monatliche Reihe | 26 |
| Welcher Prozentteil unserer Rechnungen wird spät bezahlt, und wie groß ist die durchschnittliche Verspätung? | zwei Messungen | 26 |
| Vergleiche die Anzahl der Bestellungen in diesem Monat mit dem gleichen Monat letzten Jahres. | ein Vergleich | 26 |
| Was war unser Nettogewin letzten Monat, und wovon besteht er? | Gewin mit seinen Bestandteilen | 26 |

## Hauswirtschaft

| Anweisung | Erzeugt | Kapitel |
|---|---|---|
| Prüfe die Verbindung zu Odoo und sag mir, welche Version läuft. | die erste Anweisung zum Tippen | 12 |
| Finde alle Duplikatkunden mit dem gleichen Namen und zeig sie mir. | eine Liste, keine Zusammenführung | 26 |
| Welche Produkte haben keinen festgelegten Preis? | die Fehler, die ein Angebot blockieren | 26 |
| Liste die Produkte, deren Name nicht zu ihrer interner Referenz passt. | angesammelte Nachlässigkeit, gefunden | 26 |
| Gibt es Angebote, die älter als neunzig Tage sind und noch offen sind? Archiviere sie. | eine ordentlichere Pipeline | 26 |

## Stehende Arbeit

| Anweisung | Zeitplan | Kapitel |
|---|---|---|
| Send mir eine Liste von Rechnungen, die in der vorherigen Woche überfällig wurden. | Montag, 08:00 | 22 |
| Sag mir, welche Produkte unter ihren Nachschuppunkt gefallen sind, und schlage die Bestellungen im Entwurf vor. | Freitag, 16:00 | 22 |
| Erzeuge die Zusammenfassung der Verkäufe des vorherigen Monats nach Kunde. | erster Arbeitstag des Monats, 07:00 | 22 |
| Liste die späten Bestellungen und die Anbieter, die dafür verantwortlich sind. | Donnerstag | 22 |
| Prüfe die Verbindung zu Odoo und sag mir, ob etwas nicht stimmt. | täglich (nur wenn es schweigt, wenn alles in Ordnung ist) | 22 |

## Die vier, für die ein zweiter Versuch nötig war

| Erster Versuch | Warum es scheiterte | Funktionierende Version |
|---|---|---|
| Zeig mir die Produkte, die wir nie verkauft haben. | mehrdeutig: keine Bestellposition, oder gar keine Bewegung? | Produkte ohne Bestellpositionszeile und ohne direkte Lieferung in dem letzten Jahr |
| Sende die Rechnung an den Kunden. | der Assistent hat kein E-Mail-Werkzeug, von daher | erzeuge das Rechnungspdf und sag mir, dass sie bereit ist |
| Lösche den Duplikatkunden. | der Agent-Benutzer kann nicht löschen | archiviere das Duplikat |
| Wie viel haben wir letzten Monat verdient? | mehrdeutig zwischen Umsatz, Marge und Gewin | was war unser Nettogewin letzten Monat, und wovon besteht er? |

---

Jede obige Anweisung wurde auf der in diesem Buch beschriebenen Installation getippt, gegenüber einer Firma mit Kunden, Produkten, Bestand und Dokumenten. Diejenigen in der letzten Tabelle sind hier, weil sie nicht funktionierten, und eine Bibliothek, die ihre Misserfolge versteckt, ist keine Bibliothek; sie ist ein Prospekt.
