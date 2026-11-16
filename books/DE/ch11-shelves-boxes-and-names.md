# 11. Regale, Kisten und Namen

Tom Beck hatte im Lager von Riverton neunzehn Jahre gearbeitet, und er hatte eine Regel bzgl.
Computer, die er am Morgen des vierten Tages bekannt gab, in der Türe des
kleinen Raumes stehend mit verschränkten Armen.

„Ich werde elf tausend Produkte nicht eingeben."

„Niemand bittet dich darum," sagte Maggie. „Wir werden vierzig eingeben."

Tom entflechtete seine Arme, was seiner Begeisterung vor dem Mittagessen am nächsten kam.

---

## Warum vierzig und nicht elf tausend

Der Katalog eines Großhändlers ist nicht dasselbe wie sein *Sortiment*. Riverton führte elf tausend
Referenzen, weil es über dreißig Jahre hinweg alles gekauft hatte, was die Kunden
anforderten, und die Liste war gewachsen wie eine Hecke. Von diesen elf tausend hatten vierhundert mehr als zehn Einheiten im
letzten Jahr verkauft. Vierhundert sind immer noch zu viele, um sie in einer Woche einzugeben, und die meisten teilen sich eine Form:
eine Marke, eine Größe, eine Farbe, eine Packungsmenge.

Der Plan war also nicht, den Katalog zu kopieren. Der Plan war, die *Familien* richtig zu modellieren und den
Varianten die Arbeit zu überlassen.

Das Whiteboard im Lagerbüro endete mit vier Zeilen darauf:

| Familie | Varianten | Verkaufsseinheit | Einkaufseinheit |
|---|---|---|---|
| Ringordner | 2 Größen × 3 Farben | Stück | Kiste mit 20 |
| Whiteboard-Marker | 4 Farben | Packung mit 4 | Kiste mit 12 Packungen |
| A4-Papier | 1 | Rolle | Palette mit 40 Rollen |
| Kugelschreiber | 2 Farben | Kiste mit 50 | Kiste mit 50 |

Vier Familien, und zwischen ihnen ein paar dutzend Varianten. Das ist es, was ein modernes ERP eine
Produktliste nennt: keine Liste von allem, was man je gekauft hat, sondern ein Modell der Dinge, die man verkauft, mit den
Unterschieden, die als Varianten statt als separate Einträge ausgedrückt werden.

Der Unterschied ist nicht kosmetisch. Wenn „Ringordner A4 blau" und „Ringordner A4 rot" zwei
Produkte sind, dann kann das System die Frage „wie viele A4-Ordner haben wir verkauft?" nicht beantworten, ohne dass jemand
weiß, dass die zwei miteinander verwandt sind. Wenn sie ein Produkt mit einer Farbvariante sind, ist die Frage
trivial—und die Frage ist der ganze Punkt.

## Kategorien, und warum ein Bericht sie braucht

Eine Produktkategorie ist ein Ordner, und Ordner sind langweilig, bis jemand eine Frage stellt.

In Odoo tut eine Kategorie drei Dinge: sie gruppiert Produkte für die Berichterstellung, sie kann Standard-
Konten tragen (so dass jedes Produkt der Kategorie seinen Verkauf auf dasselbe Einnahmenkonto bucht), und sie
kann eine Standard-Messseinheit und Kostenmethode tragen.

Rivertons Kategorien endeten bei sechs: *Papier*, *Ordner und Ablage*, *Schreibgeräte*,
*Tinte und Toner*, *Möbel* und *Dienstleistungen*. Sechs reicht aus, um die Frage *welcher Teil des
Unternehmens diesen Monat Geld verdient hat* zu beantworten, und wenig genug, dass niemand über den Platz eines
Produkts streitet.

Die Alternative—eine Kategorie namens *Alle Produkte*—ist das, was ein Unternehmen bekommt, wenn es
keine Entscheidung trifft, und es bedeutet, dass jeder Margenbericht ein Bericht über das
Unternehmen als Ganzes ist. Das ist ein guter Bericht, und es ist nicht der, den ein Großhändler braucht, weil der Gewinn eines Großhändlers in der Mischung
zwischen den Kategorien gemacht und verloren wird, nicht in der Gesamtsumme.

Es gibt einen zweiten Grund, sich darum zu kümmern, und er ist die Buchführung. Wenn die Kategorie das Einnahmenkonto trägt,
dann wird ein neues Produkt standardmäßig korrekt gebucht, und die Person, die es anlegt, muss nichts über
das Kontenplan wissen. Wenn nicht, ist jedes neue Produkt eine kleine Buchführungsentscheidung, die von jemandem getroffen wird, der an
Schreibmaterial denkt.

## Messseinheiten, und die Arithmetik des Lagers

Die zweite Sache, die richtig sein muss, ist die Einheit.

Riverton kauft Ringordner in Kisten zu zwanzig und verkauft sie einzeln. Wenn das System nicht weiß,
dass eine Kiste zwanzig enthält, dann ist jede Annahme, jede Zählung und jede Lieferung ein Streitpunkt, und
jemand wird irgendwann im Kopf falsch umrechnen.

Odoo behandelt dies mit zwei Einheiten pro Produkt: der Messseinheit zum Einkauf und zur Lagerung (die Kiste),
und der Verkaufseinheit (das Stück), mit einem Umrechnungsfaktor. Das Lager zählt Kisten; der Kunde
ordnet Stücke an; die Rechnung ist in Stück; der Lagerbestand ist in Kisten. Eine Zahl, drei Ansichten.

Es gibt hier eine Falle, die Unternehmen mehr Geld gekostet hat als jede andere einzelne Einstellung: **die Messseinheit
bei einem bestehenden Produkt kann nicht verändert werden, nachdem es sich bewegt hat.** Sobald hundert Annahmen
in „Stück" gebucht wurden, wandelt die Angabe an das System, dass das Produkt tatsächlich in „Kisten zu zwanzig" gekauft wird,
nicht die Vergangenheit; sie verderbt sie. Die Zeit, dies richtig zu machen, ist vor der
ersten Annahme, was erklärt, warum Tom eine Stunde damit verbrachte und warum die Stunde mehr wert war als die zwei
Tage, die er später mit dem Abstimmen einer Lagerzählung verbracht hätte.

## Das Lager selbst

Ein ERP hat nicht „das Lager". Es hat *Lagerorte*, und ein Lagerort ist jeder Ort, an dem
Lagerbestand sein kann.

Odoo installiert zwei standardmäßig: einen virtuellen Ort namens *Partner* (woher Waren kommen und wohin sie
gehen, weil ein Lieferant keine Regale ist) und *Lager*, das physische Lager. Von dort fügt ein Unternehmen
hinzu, was es tatsächlich hat: *Lager/Regale A*, *Lager/Regale B*, *Lager/Rückgaben*, *Lager/Beschädigt*.

![Die Lagerorte: ein Ort für alles, einschließlich der Orte, an denen die Waren nicht sind](../../assets/screens/odoo-06-locations.png)

Riverton fügte vier hinzu: zwei Regale, ein Rückgabengebiet und ein Quarantäneybiet für beschädigte Waren. Das letzte
ist wichtiger, als es sich anhört. Ohne es sitzt beschädigter Lagerbestand im Hauptort und wird als
verkäuflich gezählt, und das Unternehmen entdeckt das Problem, wenn ein Kunde eine Kiste zerdrückter Ordner öffnet.
Mit ihm ist der Schaden eine *Bewegung*—ein Dokument, mit einem Datum und einem Grund—und die Lagerbestandsberichterstellung sagt die
Wahrheit.

## Die ersten Produkte

Die Produkte wurden an einem Nachmittag eingetragen, von Priya und Tom zusammen, was die einzige Art ist, wie es
funktioniert: der Verkäufer weiß, wie es der Kunde nennt, das Lager weiß, wie es der Lieferant nennt, und die
Produktzeichnung braucht beide.

Sechs Felder auf diesem Formular entscheiden fast alles, was später geschieht.

**Produkttyp.** *Waren* für Dinge, die man auf eine Regale legen kann; *Dienstleistung* für Dinge, die man nicht kann. Eine
Dienstleistung hat kein Lager und keine Lieferung; eine Ware hat beide. Dies falsch zu machen macht ein Produkt
dauerhaft nicht lieferbar oder dauerhaft nicht zählbar.

**Verkaufspreis und Einkaufspreis.** Die Standardwerte. Der echte Preis für einen bestimmten Kunden kann
anders sein—dafür sind Preislisten da—aber der Standardwert ist es, den der Verkäufer sieht, wenn er
es eilig hat.

**Steuer.** Der Satz, der auf dieses Produkt gilt. Wie im zehnten Kapitel gesagt: hier konfiguriert, einmal, und
von jedem Dokument geerbt.

**Messseinheit.** Wie oben.

**Interner Verweis.** Der Code, den das Lager verwendet. Es ist das Feld, das den Unterschied macht
zwischen einem System, das Menschen verwenden können, und einem, das sie nicht können, weil es das ist, was Menschen laut aussprechen,
wenn sie vor einer Regale stehen.

**Barcode.** Optional, und transformativ, wenn man einen Scanner hat: eine Lieferung kann durch
Anpipen jeder Kiste statt durch Lesen einer Liste geprüft werden.

## Die erste Lagerbestände

Ein System, das glaubt, das Lager sei leer, wird verweigern, irgendetwas zu liefern, was korrekt und
unpraktisch ist. Also muss das erste Lagerbestände eingetragen werden, und es gibt zwei ehrliche Arten, es zu tun.

Die erste ist ein *Anfangsinventar*: man teilt dem System mit, wie viele von jedem Produkt man hat, an einem
bestimmten Datum, und es erstellt das entsprechende Lagerbestände. Das ist es, was Riverton tat, über zwei Abende hinweg,
mit einem Schreibbrett und einer Taschenlampe.

Die zweite ist eine *Lagerzählung*: das System bittet dich zu zählen, und du gibst ein, was du findest, und es
buchtet die Differenz zwischen dem, was es glaubte, und dem, was wahr ist. Das ist es, was Riverton jetzt jeden
Vierteljahr tut, und es ist eine andere Operation mit einem anderen Zweck.

Beide sind Dokumente. Keine ist eine Zahl, die in ein Feld getippt wird. Das ist die Disziplin, die das
ganze Ding funktionieren lässt: **Lagerbestände sind niemals eine Zahl, die man setzt; sie ist die Summe der Bewegungen, die man gebucht hat.**
Wenn das pedantisch klingt, bedenke, was geschieht, wenn eine Zahl gesetzt werden kann: jemand setzt sie, jemand
anderes setzt sie zurück, und das Lager und die Konten streiten sich ewig.

## Die Dinge, die keine Dinge sind

Es gibt eine Kategorie von Produkten, die mehr Verwirrung verursacht als jede andere, und sie verdient eine Seite
ihrer eigenen: die Produkte, die nicht physisch sind.

Riverton hat drei davon, und jedes Unternehmen hat dieselben drei.

**Fracht.** Die Gebühr, die der Kunde für die Lieferung zahlt. Sie hat kein Lager, sie wird nie empfangen, und
sie muss berechnet werden. In Odoo ist sie ein Produkt des Typs *Dienstleistung*, mit einem Steuersatz und einem Preis, und das
einzige, was sie von einer Kiste mit Stiften unterscheidet, ist, dass sie nie in einer Lieferung erscheint.

**Der Rabatt.** Überhaupt kein Produkt, in den meisten Systemen: eine negative Zeile auf der Bestellung, oder eine
Preislistenregel. Aber ein Unternehmen, das Gutschriften für Mengenrabatte ausstellt, braucht ein Produkt, das es auf die
Gutschrift zu setzen hat, und es wird gewöhnlich etwas wie *Mengenrabatt* genannt und als Dienstleistung getippt.

**Die Muster.** Ein Produkt, das verschenkt wird. Es hat Lager, es verlässt das Lager, und es muss nicht
berechnet werden. Wenn es als normales Produkt mit einem Nullpreis modelliert wird, zeigen die Margenberichte einen
hundertprozentigen Verlust bei hundert Einheiten; wenn es als Dienstleistung modelliert wird, wird das Lager nie
verlassen. Die saubere Art ist eine *Lieferung* des Produkts ohne Bestellung dahinter, mit einem Grund, was auch
der einzige Weg ist, wie die Kosten am richtigen Ende landen.

Keines davon ist schwierig. Alle sind unsichtbar am ersten Tag und produzieren seltsame Zahlen
am dreißigsten, was erklärt, warum die Person, die das System konfiguriert, mit der Person sitzen sollte, die
berechnet, und eine einfache Frage stellen: *was setzen wir auf eine Rechnung, die nicht auf einer Regale ist?*

## Die vierhundert Produkte, die niemand kauft

Jeder Großhändler hat sie: den Katalog von Dingen, die einmal für einen Kunden gekauft wurden, der anforderte,
und dann nie wieder. Rivertons elf tausend Referenzen enthielten, nach Tom's Schätzung, etwa
vierhundert davon.

Die Versuchung ist, sie in der ersten Woche aufzuräumen, und es ist der falsche erste Schritt aus zwei
Gründen. Das Aufräumen dauert Wochen, und es bringt dem Büro bei, dass das neue System eine Last ist, bevor
es ihnen beigebracht hat, dass das neue System nützlich ist.

Der richtige Schritt ist, die vierhundert Zeilen hereinzubringen, die wichtig sind—die mit Aktivität im letzten
Jahr—und den Rest im alten System zu lassen, archiviert, solange das Gesetz es verlangt. Ein Produkt,
das seit 2019 nicht bewegt hat, braucht keinen Eintrag im neuen System am ersten Tag; es braucht eine
Entscheidung, und die Entscheidung kann warten, bis jemand Zeit hat.

Es gibt einen zweiten Nutzen des Wartens. Nach drei Monaten des neuen Systems ist der Bericht *Produkte
mit keiner Bewegung im letzten Jahr* eine Liste genau der Kandidaten für die Versetzung in den Ruhestand, produziert in
einer Sekunde, mit der Lagerbestandswert angehängt. Das Aufräumen wird zu einer Entscheidung mit Zahlen, statt einer
Woche des Tippens.

## Die Nachbestellsregel

Die letzte Sache, die Tom einrichtete, war die Nachbestellsregel, und es ist der erste Ort, an dem das System beginnt,
nützlich statt bloß genau zu sein.

Für jedes Produkt setzte er zwei Zahlen: ein *Minimum* (unterhalb dieses, sind wir im Risiko) und ein
*Maximum* (bis zu diesem bestellen). Odoo beobachtet das Lager, und wenn ein Produkt unter das Minimum fällt, schlägt es eine
Bestellmenge für die Differenz vor. Es sendet sie nicht. Es schlägt sie vor, in einer Liste, und eine Person
entscheidet.

Dieser Unterschied—vorschlagen, nicht handeln—ist derselbe Unterschied, der enorm zählen wird, wenn der
Assistent in Teil III ankommt. Eine Maschine, die vorschlägt, ist ein Kollege. Eine Maschine, die ohne
Frage handelt, ist ein Risiko mit einem Stecker.

---

Am Freitag dieser Woche tat Tom etwas, das er in neunzehn Jahren nicht getan hatte: er druckte einen Lagerbestände
bericht aus und las ihn im Transporter, auf dem Weg zu einer Lieferung.

„Vierhundertzwölf Zeilen," sagte er, wenn er zurückkam. „Ich kenne alle von ihnen. Aber ich habe sie nie
auf einer Seite vor mir gesehen. Ich habe sie in meinem Kopf gesehen, eine nach der anderen, wenn jemand fragte."

Er legte den Bericht auf Maggie's Schreibtisch.

„Sieh dir das Papier an," sagte er. „Wir haben elfhundert Rollen, und wir verkaufen etwa neunzig eine Woche. Das ist
drei Monate Papier. Es ist nicht genau falsch, aber es ist eine Menge Geld, das auf einer Regale sitzt."

Es war so, und es war der erste Mal, dass jemand bei Riverton es sagen konnte mit einer Zahl
angehängt. Das Lagerbestände war immer da gewesen; die *Tatsache* über das Lagerbestände war in Tom's Kopf gewesen, und
Tom's Kopf war in einem Transporter gewesen.

Das ist es, was ein Lager wird, wenn es richtig modelliert wird: nicht ein Ort, an dem Dinge sind, sondern ein
Ort, an dem Dinge *bekannt* sind. Und das Wissen, sobald es existiert, beginnt sofort, Fragen zu stellen,
die niemand zu fragen gedacht hatte—über Papier, über Geld, über die elfhundert Rollen,
die vierhundert hätten sein können.

Maggie schrieb die Zahl auf die Rückseite des Lagerbeständeberichts und legte sie in die Schublade mit dem Serviette
und der Karte von Gerald. Die Schublade wurde voll. Das, entschied sie, war ein gutes Zeichen.
