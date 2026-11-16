# 23. Das Büro im Flur

Der Assistent hat zwei Eingänge, und die meisten Unternehmen nutzen einen davon einen Monat lang, bevor sie den anderen entdecken.

Der erste ist das Terminalfenster: schwarzer Hintergrund, eine Aufforderung und die Antwort darunter. Es ist der Eingang, den dieses Buch bereits benutzt hat, weil er die Arbeit zeigt—die Werkzeugaufrufe, die Zwischenschritte, das Protokoll. Es ist eine Werkstatt.

Der zweite ist eine Webseite unter `http://localhost:5290/OfficeManager`, und sie ist keine Werkstatt. Sie ist ein Büro.

---

## Was die Seite zeigt

Die Seite zeichnet ein kleines Zimmer. Es gibt Schreibtische, eine Tür, eine Pflanze und mehrere kleine Figuren, die herumlaufen, sich hinsetzen, wieder aufstehen und sich gelegentlich am Wasserspender treffen. Eine von ihnen ist dein Assistent. Unter dem Zimmer befindet sich eine Chatbox.

![Das Büro: ein Zimmer, ein Arbeiter und eine Chatbox am unteren Rand](../../assets/screens/assistant-01-office.png)

Wenn eine Anweisung eintrifft, erscheint eine Figur an der Tür und nimmt einen Schreibtis, und das Panel rechts zeigt, was sie tut—*Kontext holen*, *suchen*, *erstellen*—und das Chat-Protokoll verzeichnet den Austausch.

![Die Anweisung beim Eintreffen: der Assistent hat einen Schreibtis genommen und arbeitet](../../assets/screens/assistant-02-prompt.png)

Wenn sich das skurril anhört, ist es das auch—und doch ist es zugleich die wirksamste Schnittstelle für diese Art von Arbeit, die Riverton ausprobierte. Der Grund lohnt es zu verstehen, denn es geht nicht um Niedlichkeit.

Ein Terminalfenster zeigt *eine Unterhaltung zur Zeit*, und es zeigt alles: jedes Werkzeugaufruf, jedes Zwischenergebnis, jede Schlussfolgerungslinie. Das ist genau das, was man möchte, wenn man einen Job erstellt oder debuggt. Das ist genau das, was man nicht möchte, wenn man ein Bürovorsteher mit einem Kunden am Telefon ist.

Die Büroseite zeigt *eine Sache*: den Assistenten und ob er beschäftigt ist. Die Figuren laufen, wenn der Assistent denkt, und sitzen, wenn er untätig ist. Man kann von der anderen Seite des Zimmers aus sehen, ob der Assistent arbeitet—was trivial klingt und in der Tat das einzig nützlichste Stück Information im ganzen System ist.

"Man kann sehen, ob er beschäftigt ist, ohne irgendetwas zu lesen," sagte Priya. "Im Terminal muss ich auf die letzte Zeile schauen. Hier scha ich nur hin."

## Wann man welches nutzt

Nach einem Monat hatten Rivertons Gewohnheiten eine einfache Aufteilung.

**Das Terminal für alles, was Geld berührt oder ein Dokument verändert.** Erstellen einer Rechnung, Buchen einer Rechnung, Bestätigen einer Bestellung. Der Grund ist nicht, dass die Webseite das nicht kann—sie kann es—sondern dass das Terminal die *Schritte* zeigt, und wer die Schritte sehen kann, kann sie stoppen. Am Terminal beobachtet man den Assistenten dabei, wie er nach dem Kunden sucht, das Produkt liest, das Dokument erstellt, und man kann den Moment sehen, in dem es schiefgeht. Auf der Webseite sieht man eine Sprechblase mit „fertig", und man muss sich darauf verlassen.

**Die Webseite für Fragen und Durchforstungen.** *Wie viele überfällige Rechnungen haben wir? Welche Produkte sind niedrig? Was haben wir letzte Woche verkauft?* Nichts wird verändert, die Antwort ist kurz, und die Bürometapher lässt die ganze Sache wie das Fragen eines Kollegen wirken statt wie das Bedienen einer Maschine.

**Die Webseite für alle, die nicht Maggie sind.** Tom nutzt sie, Priya nutzt sie, und Doreen—nach einigem Widerstand—nutzt sie. Das Terminal ist auf eine Weise einschüchternd, die mit der Arbeit nichts zu tun hat: sie sieht aus wie das Innere einer Maschine, und die meisten Büroangestellten sind über dreißig Jahre lang darin unterrichtet worden, dass das Innere einer Maschine nichts für sie ist. Die Büroseite sieht aus wie ein Ort, an dem jemand arbeitet.

Dieser letzte Punkt ist keine Dekoration. Er ist der Unterschied zwischen einem Werkzeug, das vier Menschen nutzen, und einem Werkzeug, das eine Person namens vier nutzt.

## Die kleinen Leute

Die Figuren im Büro sind keine Avatare der Belegschaft. Sie sind *Assistenten*: Die Installation kann mehrere laufen lassen, jeder mit seiner eigenen Aufgabe, und die Seite zeigt sie alle. Riverton läuft mit einem, weil die Maschine ein Modell und eine Grafikkarte hat, und parallele Assistenten auf einer Maschine fügen keine Geschwindigkeit hinzu—sie wechseln sich ab, und sie können den Speicher erschöpfen.

Die Seite ist ehrlich dazu, wenn man hinsieht: Die Figuren teilen sich das Zimmer, und das Zimmer hat ein Telefon. Zwei Assistenten, die versuchen, es gleichzeitig zu beantworten, ist keine Funktion.

Es gibt eine Versuchung, wenn man das Büro sieht, es zu bevölkern—jeder Abteilung ihre eigene kleine Figur mit eigenen Anweisungen zu geben. Das ist eine schlechte Idee für ein kleines Unternehmen, und der Grund ist derselbe, der sich durch dieses ganze Buch zieht: ein Assistent ist nur so gut wie das Modell hinter ihm, und ein Modell, das vier Unterhaltungen beantwortet, ist vier langsame Unterhaltungen. Das Büro ist ein Fenster zu einem Arbeiter, nicht eine Belegschaft.

## Die dritte Tür, die gar keine Tür ist

Es gibt einen dritten Zugang, und er ist kein Bildschirm: der Assistent beantwortet HTTP-Anfragen.

Auf derselben Maschine, unter `http://localhost:5290/v1/chat/completions`, spricht es dasselbe Protokoll wie die großen Cloud-Dienste. Alles, was mit einem OpenAI-kompatiblen Endpunkt sprechen kann, kann mit ihm sprechen—a ein Skript, ein Tabellenkalkulations-Makro, ein anderes Programm, ein Telefonsystem, ein Kontaktformular einer Webseite.

Riverton hat dies nicht benutzt, und es lohnt sich zu erklären, warum, denn die Versuchung ist stark und das Risiko subtil.

Die Versuchung ist offensichtlich: ein Kunde sendet eine Anfrage per E-Mail, die Webseite leitet sie an den Assistenten weiter, der Assistent erstellt einen Kundenstammdatensatz und einen Entwurf eines Angebots, und Priya findet die Arbeit erledigt, wenn sie ihren Bildschirm öffnet. Das ist ein echter Arbeitsablauf, und es ist genau die Art von Sache, bei der diese Technologie gut ist.

Das Risiko ist, dass jede Tür ins System eine Tür ist, und die Tür bei `localhost:5290` steht für alles offen, was auf der Maschine läuft—einschließlich eines Browser-Tabs, der dazu verleitet wurde, eine Anfrage zu stellen. Die API hat standardmäßig keine Authentifizierung, weil sie dafür entwickelt wurde, von derselben Maschine aus durch Programme erreicht zu werden, die der Besitzer kontrolliert. Das ist ein vernünftiges Design für eine Werkstatt. Es ist kein vernünftiges Design für ein Unternehmen, das es eines Tages mit dem Internet verbinden wird.

Die Regel, die Riverton annahm, und die dieses Buch empfiehlt: **Die API bleibt auf der Maschine, bis jemand ein bestimmtes Bedürfnis und ein bestimmter Plan hat.** Wenn dieser Tag kommt, ist der Plan drei Zeilen lang—stelle sie hinter einen Proxy, der ein Token erfordert, beschränke sie auf einen Endpunkt, und protokolliere jede Anfrage. Bis dahin reichen zwei Eingänge, und beide haben eine Person dabei.

## Tom's Nachmittag

Der Tag, an dem die Büroseite sich ihren Platz im Unternehmen erwarb, war ein Donnerstag im Februar, und die Geschichte ist klein.

Tom war im Lager mit einem Klemmbrett und führte die vierteljährliche Abzählung durch, und er musste wissen, ob ein Palettenvorrat an Papier gegen eine Bestellung eingetroffen war oder im System noch „in Bearbeitung" war. Am Terminal bedeutet diese Frage, ins Büro zu gehen, sich an die Maschine zu setzen, die den Assistenten laufen lässt, und zu tippen. Auf der Büroseite bedeutet es, einen Browser-Tab auf dem Lager-Laptop zu öffnen—which ist eine billige Maschine, die existiert, um Produktcodes nachzuschlagen—und die Frage dort zu tippen.

*Ist die Palettenvorrat an A4-Papier von Pennine auf Bestellung P00008 bereits eingetroffen?*

*Eingetroffen: 40 Packungen am 12. November, validiert von Tom Beck, Lagerbewegung WH/IN/00031. Die Bestellung ist vollständig eingetroffen; die Rechnung ist noch nicht erstellt.*

Er hatte seine Antwort in neun Sekunden, neben der Palettenvorrat stehend. Die alte Version dieser Antwort war ein Gang ins Büro, eine Unterhaltung und eine Notiz auf einem Klemmbrett.

Dies ist der unaufgeregteste Nutzen im ganzen Buch und vielleicht der wichtigste: die zwischen einer Frage und ihrer Antwort, in Schritten gemessen. Ein Lager, das das System etwas fragen kann, ohne das Lager zu verlassen, ist ein Lager, das Dinge überprüft.

## Was das Büro nicht kann

Drei Grenzen lohnen es zu kennen, bevor ein Unternehmen eine Gewohnheit um die Seite herum aufbaut.

**Es kann zwei Unterhaltungen nicht gleichzeitig sinnvoll laufen lassen.** Das Büro zeichnet mehrere Figuren, und die Versuchung ist, je eine je Abteilung einzustellen. Auf einer Maschine mit einem Modell sind das vier Unterhaltungen, die sich abwechseln, und die Figuren sitzen an ihren Schreibtischen und sehen beschäftigt aus, während nichts fertig wird. Die Seite ist ehrlich dazu, wenn man hinsieht: das Panel rechts listet die Sitzungen auf, und nur eine von ihnen ist zu einem beliebigen Moment *arbeitend*.

**Es kann dir die Schlussfolgerung nicht zeigen.** Das Terminal zeigt die Werkzeugaufrufe, wie sie geschehen; das Büro zeigt ein Label (*suchen*, *erstellen*, *Kontext holen*) und dann eine Antwort. Das ist das richtige Detailgrad für einen Bürovorsteher und das falsche Detailgrad für jemanden, der einen Job debuggt. Die zwei Eingänge sind nicht austauschbar, und ein Unternehmen, das nur die Webseite nutzt, wird schließlich das Terminal brauchen—normalerweise am Tag, an dem etwas schiefgeht.

**Es kann nicht auf einem Bildschirm in einem öffentlichen Raum offen gelassen werden.** Der Chat zeigt die Daten des Unternehmens: Namen, Beträge, Rechnungen. Ein Laptop auf einem Schreibtis in einem Laden ist ein Fenster in das Hauptbuch. Die Seite hat keine eigene Anmeldung, weil sie vom Assistenten auf `localhost` bereitgestellt wird und annimmt, dass die Maschine dir gehört. Diese Annahme ist am Schreibtis korrekt und in einer Empfangshalle falsch.

## Der Klang, und der Schalter, der ihn ausschaltet

Die Seite spielt kleine Geräusche: eine Tastatur, wenn der Assistent tippt, eine Glocke, wenn ein Job erledigt ist. Sie ist eine Woche lang bezaubernd und ein Monat lang wahnsinnig machend, und der Schalter befindet sich in der unteren rechten Ecke der Seite, beschriftet mit *SOUND: ON*.

Die Tatsache, dass dies einen Absatz wert ist, ist selbst eine Lektion über Bürosoftware. Die Funktionen, die entscheiden, ob ein Werkzeug überlebt, sind selten die im Prospekt. Es sind die, die die Nerven des Büros berühren: ob es Geräusche macht, ob es offen gelassen werden kann, ob die Sache, die es zeigt, wahr ist.

## Eine kurze Geschichte der Bürometapher

Menschen in ein Bild zu setzen, um Arbeit darzustellen, ist eine alte Idee im Computing, und es hat eine gute Bilanz.

1984 führte Apples Macintosh die Desktop-Metapher ein—Dateien, Ordner, ein Papierkorb—und sie funktionierte, weil sie es Menschen erlaubte, Wissen zu nutzen, das sie bereits hatten. 1987 ging das Projekt Information Visualizer am Xerox PARC weiter und zeichnete Büros, mit Zimmern und Dokumenten, als Weg, große Informationsräume zu navigieren. 1993 lehrte das Spiel *Doom* eine Generation, dass eine First-Person-Ansicht eines Raums lesbarer ist als ein Diagramm davon.

Was alle drei entdeckten, ist dasselbe: **eine räumliche Metapher trägt Zustand.** Man muss keine Statuszeile lesen, um zu wissen, dass ein Zimmer beschäftigt ist; man kann es sehen. Die Büroseite bei Riverton ist ein direfter Nachfolger dieser Idee, und sie existiert zum selben Grund—nicht, um bezaubernd zu sein, sondern um die Frage *was geschieht?* zu beantworten, ohne den Nutzer lesen zu müssen.

## Der Chat, und dieselbe Disziplin

Die Chatbox am unteren Rand der Seite nimmt dieselben Anweisungen an und produziert dieselbe Arbeit. Alles in Kapitel fünfundzwanzig über Prompts gilt unverändert.

Zwei Dinge sind anders, und beide sind Folgen der Schnittstelle.

**Antworten sind kürzer.** Die Webseite zeigt eine Unterhaltung, kein Protokoll, also fasst der Assistent zusammen. Das ist gut fürs Lesen und schlecht fürs Prüfen: die Rechnungsnummer mag in der Zusammenfassung sein, aber die Liste der Schritte, die sie erzeugt haben, ist es nicht. Wenn ein Ergebnis zählt, frage eine Folgefrage—*zeige mir die Dokumente hinter dieser Nummer*—und die Antwort wird eine Liste sein.

**Die Versuchung zum Multitasking ist stärker.** Ein Chatfenster lädt zu einer zweiten Frage ein, während die erste noch läuft, und eine zweite Frage, während die erste läuft, ist die Sache, die eine Einzelmodell-Installation kaputt wirken lässt. Die Seite verhindert das nicht. Die Gewohnheit tut es.

---

Maggie's eigene Nutzung formte sich zu etwas, das sie nicht erwartet hatte: sie nutzt die Webseite im Morgen und das Terminal im Nachmittag.

„Im Morgen will ich Dinge wissen," sagt sie. „Ich will die Liste von dem, was spät ist, was niedrig ist, was über Nacht eingetroffen ist. Das ist eine Unterhaltung, und das Büro ist, wo ich sie habe. Im Nachmittag will ich *Dinge tun*—die Rechnungen buchen, den drei Konten hinterherjagen, die Sache reparieren, die Tom gefunden hat—und dafür will ich die Räder wenden sehen."

Sie dachte einen Moment darüber nach.

„Es ist wie der Unterschied zwischen dem Fragen einer Sache an jemandem im Flur und dem Hinsetzen mit ihnen an einem Schreibtis. Dieselbe Person. Ein anderer Raum."

Das ist eine ebenso gute Beschreibung der zwei Schnittstellen, wie dieses Buch bieten kann, und es schlägt das Prinzip hinter ihnen vor: die Schnittstelle sollte die *Art der Aufmerksamkeit* anpassen, die die Arbeit erfordert, nicht die Art der Technologie hinter ihr. Eine Frage braucht eine Unterhaltung. Ein Buchen braucht einen Zeugen.
