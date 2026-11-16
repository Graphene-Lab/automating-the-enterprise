# Anhang B — Ein Glossar für Menschen, die nicht programmieren

Jedes unten stehende Wort wurde in diesem Buch verwendet oder wird Ihnen beim Installieren des Systems begegnen. Die Definitionen sind bewusst einfach und gelegentlich ungenau gehalten; wo eine präzise Definition einem Programmierenden helfen und einen Büroleiter verwirren würde, hat die einfache Version gewonnen.

**Agent.** Ein Programm, das eine Anweisung in gewöhnlicher Sprache empfangen und sie ausführen kann—etwas nachschlagen, Datensätze erstellen, einen Prozess ablaufen—statt nur mit Text zu antworten. In diesem Buch ist der Agent AgentBridge, das Programm, mit dem Sie in einem Terminalfenster sprechen.

**API.** Application Programming Interface. Ein dokumentierter Weg, wie ein Programm ein anderes um etwas bittet. Stellen Sie es sich als die Ausgabefenster eines Restaurants vor: die Küche möchte Sie nicht in der Küche haben, aber es gibt einen ordentlichen Weg, eine Bestellung abzugeben und einen Teller zu erhalten.

**API-Schlüssel.** Das Passwort, das ein Programm statt eines Menschen verwendet. Es ist eine lange Zeichenkette, wird einmal angezeigt und sollte wie ein Schlüssel zum Safe behandelt werden: im Passwortmanager aufbewahrt, niemals in einer E-Mail, niemals in einem Dokument, das weitergeleitet wird.

**Backup.** Eine Kopie der Daten, die zu einem bestimmten Zeitpunkt erstellt und an einem anderen Ort als der Maschine aufbewahrt wird, die das Original enthält. Ein nicht verifiziertes Backup ist ein Wunsch; ein Backup, das Sie geöffnet und gelesen haben, ist ein Backup.

**Datenbank.** Ein Programm, dessen Aufgabe es ist, Fakten zu speichern und sie genau zurückzugeben, selbst wenn während einer Änderung die Stromausfällt. In diesem Buch: PostgreSQL.

**Dokument (im ERP).** Kein Stück Papier: ein Datensatz über etwas, das geschehen ist oder geschehen wird—eine Bestellung, eine Lieferung, eine Rechnung, eine Zahlung—mit einem Datum, einer Partei, einer Zeilenliste und einem Status. Dokumente bewahren ihre eigene Kopie der Fakten auf, mit denen sie erstellt wurden, sodass die Rechnung vom letzten Monat noch den Preis vom letzten Monat anzeigt.

**ERP.** Enterprise Resource Planning. Software, die den Kunden, das Produkt, die Bestellung, den Lagerbestand, die Rechnung und das Hauptbuch in einem zusammenhängenden Modell hält, sodass ein einmal eingeiteter Fakt überall sichtbar ist. Der Name wurde 1990 vom Analystenunternehmen Gartner geprägt.

**Feld.** Ein einzelnes Informationsstück auf einem Datensatz: die Telefonnummer des Kunden, der Preis eines Produkts, das Datum einer Rechnung.

**Buchungssatz.** Der doppische Buchführungssatz, den jeder finanzielle Vorgang erzeugt: ein Betrag in einem Konto und derselbe Betrag, entgegengesetzt, in einem anderen. Vor langer Zeit softwareentwickelt; 1494 von Luca Pacioli kodifiziert; immer noch der Grund, warum die Bücher geprüft werden können.

**JSON.** Ein Weg, Daten als Text zu schreiben, damit ein Programm sie an ein anderes senden kann. Sie werden sie nur in einer Protokolldatei sehen, wo sie wie ein Absatz aus Satzzeichen aussieht.

**Sprachmodell (LLM).** Ein Programm, das auf einer enormen Menge an Text geschult wurde und in der Lage ist, glaubhaften Text als Antwort auf eine Anweisung zu erzeugen. Es ist gut in Sprache und unzuverlässig in Fakten, es sei denn, es ist *geerdet*—das heißt, es wird gezwungen, die Fakten nachzuschlagen statt sie sich zu merken.

**MCP.** Model Context Protocol. Ein offener Standard, veröffentlicht von Anthropic im November 2024, der einem Programm ermöglicht, die Tools, die es einem Assistenten anbietet, in einheitlicher Weise zu beschreiben. Es ist der Grund, warum ein für einen Assistenten geschriebenes Tool von einem anderen verwendet werden kann.

**Modell (in diesem Buch, zwei Bedeutungen).** 1. Die Repräsentation eines Unternehmens innerhalb eines ERP: Parteien, Produkte, Dokumente, Geld. 2. Das geschulte Artefakt hinter einem Assistenten: das „Sprachmodell." Der Kontext macht deutlich, welche gemeint ist; wenn nicht, ist meist die erste Bedeutung diejenige, die zählt.

**Modul.** Ein Paket, das einem ERP eine Fähigkeit hinzufügt—Buchhaltung, Lagerverwaltung, Fertigung, Einkauf. Das Installieren eines Moduls fügt Bildschirme, Datensätze und Regeln hinzu; es ändert nicht die zugrunde liegenden Daten.

**Odoo.** Ein Open-Source-ERP, gestartet 2005 unter dem Namen TinyERP, 2008 in OpenERP umbenannt und 2014 in Odoo. Die Community-Edition ist frei; die Enterprise-Edition ist lizenziert. Version 20, in diesem Buch verwendet, wurde im September 2026 veröffentlicht.

**PostgreSQL.** Die Open-Source-Datenbank, die von Odoo verwendet wird. Sie begann als Forschungsprojekt an der University of California in Berkeley in den 1980er Jahren und ist heute eine der am weitesten verbreiteten Datenbanken der Welt.

**Prompt.** Die Anweisung, die Sie dem Assistenten in gewöhnlicher Sprache eingeben. Ein guter Prompt sagt, was Sie wollen, für wen und bis wann; ein schlechter Prompt sagt „mach die Rechnungen" und hofft.

**Datensatz.** Eine einzelne Zeile in einer Tabelle: ein Kunde, ein Produkt, eine Rechnung.

**Schema.** Die Liste der Tabellen und Felder, die eine Datenbank enthält, sowie die Regeln über das, was darin stehen darf. Wenn jemand sagt „das Schema sagt, dass ein Kunde einen Namen haben muss," meint er, dass die Datenbank verweigern wird, einen Kunden ohne einen zu speichern.

**Lagerbewegung.** Der Datensatz über Waren, die sich von einem Ort zu einem anderen bewegen: von einem Lieferanten in ein Lager, von einem Regal in einen Transporter, von einem Transporter zurück zu einem Regal, weil die Schultür verschlossen war. Die Lagermenge eines Produkts ist die Summe seiner Bewegungen; sie wird nie direkt eingegeben.

**Token.** Die Einheit, in der die Arbeit eines Sprachmodells gemessen wird. Grob ist ein Token drei Viertel eines Wortes. Anbieter berechnen pro Token, weshalb ein sehr langes Dokument mehr kostet zu verarbeiten als eine kurze Frage.

**Tool (im Kontext eines Assistenten).** Eine einzelne Aktion, die der Assistent ausführen darf, mit einem Namen und einer Beschreibung: *Kunden suchen*, *eine Rechnung erstellen*, *eine Zahlung verbuchen*. Ein Assistent ohne Tools kann nur sprechen. Ein Assistent mit Tools kann arbeiten.

**Transaktion.** Eine Änderung, die entweder vollständig geschieht oder gar nicht. Sie ist das Versprechen, das eine Datenbank vertrauenswürdig macht: es gibt keinen Zustand, in dem eine halbe Rechnung existiert.

**Variante.** Eine Version eines Produkts, das sich in einem—at—unterscheidet—Größe, Farbe, Spannung. Ein Produkt mit zwölf Varianten ist nicht zwölf Produkte, und seine korrekte Modellierung ist der Unterschied zwischen einem nützlichen Bericht und einem nutzlosen.

**Web-Oberfläche (oder Web-UI).** Die Bildschirme, die Sie in einem Browser sehen. Odos Web-Oberfläche ist der Ort, an dem Sie das Unternehmen konfigurieren, Datensätze ansehen und Dokumente drucken; der Assistent ist ein zweiter Weg, dieselben Datensätze zu erreichen.

**Prozessablauf.** Die Abfolge von Zuständen, die ein Dokument durchläuft—Entwurf, bestätigt, geliefert, gerechnet, bezahlt—sowie die Regeln über wer es von einem zum nächsten bewegen darf. In einem guten ERP ist der Prozessablauf die Unternehmenspolitik, niedergeschrieben und durchgesetzt.
