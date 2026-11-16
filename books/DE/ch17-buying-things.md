# 17. Das Einkaufen

Einkaufen ist die Hälfte eines Geschäfts, über die niemand Bücher schreibt.

Der Verkauf hat etwas Romantisches: Kunden, Angebote, der Nervenkitzel der Bestellung. Das Einkaufen hat eine Bestellung, einen Lieferschein, eine Rechnung eines Lieferanten und eine Zahlungsläufe. Und doch kommt jedes Pfund, das ein Großhändler ausgibt, durch diese Tür, und der Unterschied zwischen einem Unternehmen, das gut einkauft, und einem, das schlecht einkauft, ist der Unterschied zwischen einer Marge und einer Gewohnheit.

Das EKAUFEN von Riverton wurde elf Jahre lang von Maggie am Telefon und aus dem Gedächtnis erledigt. Sie kannte den Papierlieferanten, den Stiftlieferanten und den Binderlieferanten, und sie wusste, was sie beim letzten Mal bezahlt hatte, weil sie einen Ordner hatte. Was ihr fehlte, war jede Möglichkeit zu wissen, ob der Preis gestiegen war, ob die letzte Lieferung tatsächlich eingetroffen war, oder ob die Rechnung, die sie bald bezahlen würde, mit der Bestellung übereinstimmte, die sie aufgegeben hatte.

Die erste Einkaufsaufgabe des Assistenten war eine Nachbestellsregel, die einen Mittwoch auslöste.

---

## Die Nachbestellsregel und was sie vorschlägt

Kapitel elf hat auf jedes Produkt zwei Zahlen gesetzt: ein Minimum und ein Maximum. Odoo beobachtet den Bestand, und wenn ein Produkt unter sein Minimum fällt, schlägt es eine Bestellung vor.

Sie schlug eine für Ringbinder vor, am Mittwoch, in einer Liste, die Tom bei seinem Kaffee betrachtete.

> *Drei Produkte befinden sich unter ihrem Nachbestellpunkt: Ringbinder A4 (blau) 62 verfügbar, Minimum 100; Whiteboard-Stifte (sortiert) 44 verfügbar, Minimum 60; A4-Papier 9 Ballen verfügbar, Minimum 40.*

Tom betrachtete die Liste, entschied, dass das Papier bis zur Bestätigung des Palettenpreises warten konnte, und forderte die anderen zwei.

> *Erstelle eine Bestellung über 500 Ringbinder A4, blau, und 200 Packungen Whiteboard-Stifte, sortiert, von unseren üblichen Lieferanten, zum letzten Preis, den wir bezahlt haben. Noch nicht bestätigen.*

> *Bestellung P00008 erstellt, im Entwurf. Zwei Lieferanten, weil die Produkte aus verschiedenen Lieferanten kommen: 500 × Ringbinder A4 (blau) von Pennine Paper bei £2,10; 200 × Whiteboard-Stifte (Packung mit 4, sortiert) von Kestrel Supplies bei £6,80. Gesamt netto £2.410,00, MwSt. £482,00, gesamt £2.892,00. Es wurde nichts versandt; sage "confirm", um die Aufträge aufzugeben.*

Zwei Dinge in dieser Antwort sind beachenswert, und beide davon sind Dinge, die das System tut, die eine Person von Hand hätte tun müssen.

Das erste sind *zwei Lieferanten*. Tom hatte zwei Produkte bestellt; das System wusste, dass sie aus verschiedenen Lieferanten kommen, und produzierte zwei Bestellungen. Eine Person hätte dasselbe getan, nach dem Ansehen der Produktakten. Der Unterschied ist, dass die Person es vergessen hätte und die Binder beim Stiftlieferanten bestellt hätte.

Das zweite ist *der letzte Preis, den wir bezahlt haben*. Das ist keine Preisliste; es ist ein Fakt aus der Historie. Das System sah sich den jüngsten Einkauf dieses Produkts an und verwendete den Preis. Wenn der Lieferant seine Preise erhöht hat, wird die Bestellung falsch sein—aber sie wird auf eine Weise falsch sein, die man sehen kann, weil der frühere Preis auf der Akte neben dem neuen steht.

## Was die Bestätigung tut

Die Bestätigung einer Bestellung tut drei Dinge, und das dritte ist dasjenige, das zählt.

Sie **verpflichtet** das Unternehmen zu kaufen, zu einem Preis, bis zu einem Datum—was ein Versprechen ist und daher ein Dokument, das man sich vor der Erstellung ansehen sollte.

Sie **erzeugt eine erwartete Lieferung**: das Lager weiß nun, dass fünf hundred Binder kommen, und wann. Das ist es, was es möglich macht, die Frage *kö wir das einem Kunden nächste Woche versprechen?* mit etwas Besserem als einer Vermutung zu beantworten.

Und sie **öffnet eine Tür für die Rechnung**: wenn die Rechnung des Lieferanten eintrifft, kann sie gegen die Bestellung abgeglichen werden. Nicht, weil das System misstrauisch ist, sondern weil der *Drei-Wege-Abgleich* die älteste Kontrolle im Handel und zugleich die beste ist.

## Der Drei-Wege-Abgleich

Die Idee ist einfach genug, um auf eine Serviette zu passen, und sie hat Unternehmen mehr Geld gespart als jede Softwarefunktion, die je erfunden wurde.

Man hat five hundred Binder bei £2,10 pro Stück bestellt. Das Lager hat five hundred Binder erhalten. Die Rechnung des Lieferanten sagt five hundred Binder bei £2,10 pro Stück. Drei Dokumente, drei Zahlen, und sie müssen übereinstimmen, bevor die Rechnung bezahlt wird.

Wenn die Rechnung £2,30 sagt, fragt jemand, warum. Wenn das Lager vier hundred und achtzig erhalten hat, fragt jemand, wo die zwanzig hingegangen sind. Wenn die Bestellung über five hundred ging und die Rechnung über six hundred, fragt jemand, wer die zusätzlichen hundred autorisiert hat—und die Antwort ist oft *niemand*, was genau der Punkt ist.

Die Kontrolle ist alt. Lehrbücher der Kostenrechnung beschrieben sie in den 1920er Jahren, und sie wurde in den Einkaufshandbüchern der 1950er Jahre formalisiert, als große Hersteller entdeckten, dass der Unterschied zwischen dem, was sie bestellten, und dem, was sie bezahlt hatten, ein signifikanter Bruchteil ihres Gewinns war. Sie überlebt, weil sie billig ist: drei Dokumente, die bereits existieren, verglichen von einer Maschine, die sich nicht langweilt.

Was neu ist, ist, dass der Abgleich eine Sekunde dauert und *erklärt* werden kann.

> *Erstelle die Lieferantenrechnung für Bestellung P00008 und prüfe sie gegen die Bestellung und die Lieferung.*

> *Lieferantenrechnung BILL/2026/0031 aus P00008 für Pennine Paper erstellt: 500 × Ringbinder A4 (blau) bei £2,10, netto £1.050,00, MwSt. £210,00, gesamt £1.260,00. Abgeglichen: bestellt 500, erhalten 500, in Rechnung gestellt 500. Kein Unterschied. Die Rechnung ist im Entwurf.*

Kein Unterschied. An einem guten Tag ist das die ganze Arbeit: drei Zahlen, die übereinstimmen, in einem Satz, in einer Sekunde.

An einem schlechten Tag sagt es etwas wie: *bestellt 500, erhalten 480, in Rechnung gestellt 500 — ein Unterschied von 20 Stück bei £2,10.* Und dann muss eine Person entscheiden: hat der Lieferant unter geliefert, hat das Lager falsch gezählt, oder hat jemand eine Teillieferung angenommen und vergessen, sie zu protokollieren? Das System kann das nicht beantworten. Es kann nur die Frage unvermeidbar machen.

---

## Das Zahlen

Das Zahlen eines Lieferanten ist das Spiegelbild des bezahlt Werdens, und es hat dieselbe Form: ein Dokument (die Rechnung), eine Zahlung und ein Abgleich zwischen beiden.

> *Register eine Zahlung des vollen Betrags von BILL/2026/0031, heute datiert, per Banküberweisung.*

> *Zahlung für BILL/2026/0031 registriert: £1.260,00 an Pennine Paper, aus dem Bankbuch, datiert 14. November 2026. Die Rechnung ist nun vollständig bezahlt; das Guthaben des Lieferanten ist null.*

Das Bankbuch ist nicht die Bank. Es ist der *Stand* des Unternehmens über das, was die Bank getan hat, und beide müssen abgeglichen werden—was das monatliche Ritual ist, das im Kapitel nach dem nächsten beschrieben wird. Der Unterschied zählt, weil es dort ist, wo ein Unternehmen entdeckt, dass eine von ihm registrierte Zahlung nie erfolgte, oder eine von der Bank getane Zahlung nie registriert wurde.

## Eine kurze Geschichte der Bestellung

Die Bestellung als Dokument ist ein Kind des Eisenbahnzeitalters. Vor den Eisenbahnen kaufte ein Händler von Menschen, die er sehen konnte, und ein Handschlag plus ein BuchungsEintrag reichten aus. Die Eisenbahnen schufen Entfernung: ein Käufer in Manchester, der bei einer Mühle in Leeds bestellte, brauchte ein Dokument, das sagte, was bestellt wurde, zu welchem Preis und wann, weil die Waren Tage später eintrifften und der Mann, der sie bestellt hatte, vielleicht nicht mehr da war.

Die Form der modernen Bestellung—Nummer, Datum, Lieferant, Positionen, Mengen, Preise, Konditionen—wurde im frühen zwanzigsten Jahrhundert fixiert und hat sich seitdem nicht verändert, weil sie die minimale Information kodiert, die nötig ist, um einen Streitfall zu klären. Die Software hat das Dokument nicht verändert. Sie hat die Kosten seiner Erstellung, seines Versands, seines Abgleichs und seines Auffindens verändert.

Was, in einem Satz, das Argument dieser ganzen ist.

## Das Lieferantenakten und wofür sie da ist

Ein Lieferant in einem ERP ist kein Adressbuch-Eintrag. Es ist eine Reihe von Konditionen, und die Konditionen sind es, die die Papierarbeit funktionsfähig machen.

Die Lieferantenakten von Riverton wurden an einem Nachmittag aufgebaut, und jede von ihnen hält fünf Dinge, die zählen: die **Zahlungskonditionen** (dreißige Tage ab Rechnungsdatum, oder Monatsende des folgenden Monats, was sehr verschiedene Dinge sind), die **Währung**, die **Steuerbehandlung** (ob der Lieferant MwSt. berechnet und nach welchem Regime), die **Lieferzeit**, die der Käufer erwartet, und den **Kontakt**, der antwortet, wenn etwas falsch ist.

Keines davon ist Dekoration. Die Zahlungskonditionen entscheiden über den Fälligkeitstag auf jeder Rechnung, und ein Lieferant, dessen Konditionen als "30 Tage" registriert sind, wenn sie tatsächlich "60 Tage netto" sind, wird jeden Monat ein Jahr lang frühzeitig bezahlt—was harmlos klingt und in Wirklichkeit ein kleines, dauerhaftes Darlehen an einen Lieferanten ist, der nicht danach gefragt hat. Die Währung entscheidet, ob eine Rechnung in Euro zum Kurs des Rechnungsdatums oder des Zahlungsdatums umgerechnet wird, was sich als Gewinn oder Verlust zeigt. Die Lieferzeit entscheidet, wann das System die Waren erwartet, was dem Bericht "späte Bestellungen" überhaupt eine Bedeutung verleiht.

Das alte System hatte nichts davon. Es hatte einen Ordner von Rechnungen und eine Telefonnummer, die auf die Innenseite des Ornders geschrieben war.

## Was eine Bestellung nicht tut

Es lohnt sich, über die Grenzen Klarheit zu gewinnen, weil ein Unternehmen, das zu viel von einem Dokument erwartet, von der Software, die es erzeugt, enttäuscht wird.

Eine Bestellung **verhandelt nicht**. Sie protokolliert den Preis, der vereinbart wurde, und der Assistent kann dir zeigen, was du beim letzten Mal bezahlt hast, und was du beim Mal davor bezahlt hast—was die Munition für eine Verhandlung ist, nicht die Verhandlung selbst.

Sie **garantiert nicht** die Lieferung. Sie erzeugt eine Erwartung, und die Erwartung ist es, was der Bericht über späte Bestellungen misst.

Sie **prüft nicht** die Waren. Das ist die Lieferung, und die Lieferung ist eine Person mit einem Schreibbrett.

Und sie **zahlt nicht**. Die Zahlung ist eine separate Entscheidung, später getroffen, normalerweise von jemandem, der zuerst auf das Bankguthaben sieht.

Was sie tut, ist, alle vier dieser Dinge *sichtbar* zu machen, und Sichtbarkeit ist es, was eine am Telefon geführte Beziehung in eine Beziehung verwandelt, die geprüft werden kann.

## Der Preis, der gestiegen ist

Die Palettengebühr, die Doreen im Kapitel neunzehn fand, hatte ein Gegenstück auf der Einkaufsseite, und sie wurde durch dieselbe Art von Frage gefunden.

> *Wel Lieferanten haben ihre Preise in den letzten sechs Monaten erhöht, und um wie viel?*

Die Antwort listete vier Lieferanten und elf Produkte auf, und eines davon war das Papier: der Einkaufspreis war von £2,05 auf £2,18 pro Ballen im Juli gestiegen, was sechs Prozent ist, bei einem Produkt, das Riverton per Palette kauft.

Sechs Prozent auf Papier waren, bei Rivertons Mengen, etwa £1.900 pro Jahr. Niemand hatte es bemerkt, weil niemand eine Liste von dem hatte, was sie vorher bezahlt hatten. Der Käufer—Maggie in diesem Fall—hatte bemerkt, dass die Rechnung "etwas höher aussah" und hatte angenommen, es war ihre Einbildung.

Das ist das Muster, zu dem diese ganze Buch immer wieder zurückkehrt: das Geld wird nicht in großen, dramatischen Fehlern verloren. Es wird in Änderungen verloren, die zu klein sind, um sie einzeln zu bemerken, und zu groß, um sie aufsummiert zu ignorieren. Ein System, das sich den früheren Preis merkt, macht sie bemerkbar, und das Bemerken ist der größte Teil der Arbeit.

## Die eine Sache, die man am ersten Tag richtig machen muss

Wenn ein Unternehmen eine Sache aus diesem Kapitel mitnimmt, dann diese: **registriere die Zahlungskonditionen auf dem Lieferanten, nicht auf der Rechnung.**

Eine Rechnung, auf die Konditionen eingetragen wurden, ist ein Dokument, das einmal nach diesen Konditionen bezahlt wird. Ein Lieferant mit Konditionen auf der Akte ist ein Lieferant, dessen jede Rechnung zum richtigen Tag fällig ist, für immer, ohne dass sich jemand darüber Gedanken macht. Der Unterschied ist eine Konfiguration von dreißig Sekunden und ein Jahr lang, in dem man dieses Gespräch nicht zu führen hat:

"Warum zahlen wir Pennine früh?"
"Ich weiß nicht, das System sagt, die Rechnung ist fällig."
"Die Rechnung ist in sechzig Tagen fällig, nicht in dreißigen."
"Dann ist die Lieferantenakte falsch."
"Seit wann?"

Seit dem ersten Tag, normalerweise, und niemand hat es bemerkt, weil frühzeitiges Zahlen kein Fehler ist, über den sich jemand beschwert—außer der Person, die im Februar auf den Cashflow sieht.

---

Toms Urteil am Ende des ersten Monats des Einkaufs durch das System war charakteristisch praktisch.

"Ich hielt eine Bestellung früher für Papierkram", sagte er. "Das ist sie nicht. Es ist das einzige Ding, das mich davon abhält, für etwas zu zahlen, das ich nicht bekommen habe."

Maggie fragte ihn, ob das System etwas eingefangen habe.

"Zweimal. Einmal war die Rechnung über zwanzig mehr als wir erhalten hatten, und einmal war der Preis gestiegen, ohne dass uns jemand es gesagt hatte. Beide Male hätte ich sie bezahlt, weil ich auf die Rechnung gesehen und gedacht hätte: ja, das ist etwa richtig."

*"Etwa richtig"* ist die Phrase, die man sich merken sollte. Das meiste Geld, das in einem kleinen Unternehmen verloren geht, geht im Zwischenraum zwischen *etwa richtig* und *richtig* verloren, und der Zwischenraum wird nicht durch vorsichtigeres Tun geschlossen. Er wird geschlossen durch das Haben von drei Zahlen zum Vergleichen und einer Maschine, die sie jedes Mal vergleicht.
