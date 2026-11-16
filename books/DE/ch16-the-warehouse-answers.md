# 16. Das Lager antwortet

Die Frage, die Tom Becks Job veränderte, wurde an einem Freitag gestellt, und es war keine Frage zu Computern.

> *Wie viele A4-Ringordner haben wir, und wo sind sie?*

Er hatte sie neunzehn Jahre lang tausendmal gefragt, und die Antwort kam immer von einer Person: von ihm selbst, oder von jenem, der auf der Kommissionierlinie stand, oder von einem Notizbuch, das manchmal richtig war. Jetzt gab er sie in ein Fenster ein und erhielt dies:

> *Ringordner A4: 412 insgesamt auf Lager. 350 für Bestellung S00012 (Ashfield-Akademie) reserviert. 62 verfügbar. Orte: Lager/Ablageregal A — 380, Lager/Rückgaben — 24, Lager/Quarantäne — 8.*

Er las sie dreimal. Dann ging er zum Ablageregal A und zählte, was elf Minuten dauerte und das System bei allen drei Zahlen als richtig bestätigte.

„Gut", sagte er, wenn er zurückkam. „Jetzt glaube ich daran."

---

## Was ein Lagerbewegung ist

Die Zahl 412 wird nirgendwo gespeichert. Das ist die erste Sache, die man verstehen muss, und sie ist es, die ein echtes Bestandsystem von einer Tabelle mit einer Mengenspalte unterscheidet.

Gespeichert ist eine Liste von *Bewegungen*: zweihundert vom Lieferanten im März erhalten, dreihundertfünfzig für Ashfield im Juni kommissioniert, zwanzig im Juli zurückgegeben, acht im August in Quarantäne verlegt. Die Bestandsmenge ist die Summe dieser Bewegungen, berechnet, wenn man fragt. Wenn man erneut fragt, und sich nichts bewegt hat, erhält man dieselbe Antwort. Wenn sich etwas bewegt hat, erhält man eine andere, und der Unterschied ist *die Bewegung selbst*—mit einem Datum, einem Benutzer, einem Grund und einem Dokument.

Dies hat drei Konsequenzen, die eine Tabelle nicht reproduzieren kann.

**Man kann immer herausfinden, warum.** Wenn eine Zahl falsch aussieht, erklären die Bewegungen sie. Nicht „jemand hat die Menge geändert", sondern „zwanzig gingen am 3. August in Quarantäne, weil die Palette zerquetscht war".

**Zwei Menschen können stillschweigend nicht uneinig sein.** Wenn Tom 380 zählt und das System 412 sagt, ist der Unterschied ein Dokument: eine Anpassung, mit einem Grund, von jemandem genehmigt. Die Zählung überschreibt nicht das System; sie erzeugt eine Bewegung, die sie ausgleicht.

**Die Geschichte überlebt einen Wechsel der Einheit, des Preises oder des Lieferanten.** Die Bewegungen behalten die Mengen, in denen sie vorgenommen wurden. Die Neustrukturierung des Katalogs schreibt die Vergangenheit nicht um.

## Reserviert, verfügbar und der Unterschied, der zählt

Die zweite Sache, die Tom lernte, ist der Unterschied zwischen *auf Lager* und *verfügbar*, und es ist der Unterschied zwischen einem Lager, das verspricht, und einem Lager, das seine Versprechen hält.

**Auf Lager** ist das, was physisch im Gebäude ist: 412 Ordner.

**Reserviert** ist das, was für eine bestimmte Bestellung versprochen wurde: 350 Ordner, für Ashfield, wartend auf den Transporter.

**Verfügbar** ist auf Lager minus reserviert: 62 Ordner, die jemandem versprochen werden können.

Ein Unternehmen, das nur *auf Lager* verfolgt, wird dieselben 350 Ordner doppelt versprechen—einmal für Ashfield und einmal für Northgate—und das Problem am Morgen der Lieferung entdecken, wenn es nur eine Palette gibt. Ein Unternehmen, das Reservierungen verfolgt, entdeckt sie im Moment des zweiten Versprechens, wenn das System *62 verfügbar* sagt und der Verkäufer eine Entscheidung treffen muss.

Diese Entscheidung—liefern wir Northgate spät, oder kaufen wir mehr, oder teilen wir die Bestellung?—ist eine kaufmännische Entscheidung, und der Sinn des Systems ist nicht, sie zu treffen. Der Sinn ist, sie vor eine Person zu bringen, *bevor* sie sich zu einer Entschuldigung wird.

## Die Lieferung

Die Lieferung selbst ist das einfachste Dokument im ganzen System und jenes mit den meisten Konsequenzen.

> *Liefern die Bestellung S00012 aus und zeig mir die Lagerbewegungen, die sie erzeugt hat.*

> *Lieferung WH/OUT/00004 für Bestellung S00012 validiert. Bewegungen: 350 × Ringordner A4 (blau) von Lager/Ablageregal A zu Kunden; 20 × Whiteboard-Marker (Packung mit 4) von Lager/Ablageregal A zu Kunden. Bestand nach der Bewegung: 62 Ordner auf Lager, 0 reserviert; Marker 44 auf Lager.*

Drei Dinge geschahen gleichzeitig, und es lohnt sich, sie zu trennen.

Der **Bestand** bewegte sich: 350 Ordner verließen Ablageregal A. Die **Reservierung** verschwand, weil sie erfüllt war. Und die **Bestellung** änderte ihren Zustand: sie ist nun *geliefert*, was bedeutet, dass die Rechnung dagegen erstellt werden kann.

Wenn die Lieferung unvollständig gewesen wäre—zweihundert Ordner statt dreihundertfünfzig—hätte Odoo eine *Nachlieferung* erstellt: ein zweites Lieferungsdokument für den Rest, verknüpft mit dem ersten. Dieser einzelne Mechanismus ist der Grund, warum ein Unternehmen versprechen kann *wir senden den Rest am Freitag*, ohne dass sich jemand daran erinnern muss, was der Rest war.

## Die Orte in der Praxis

Ein Ort klingt nach einer Fachfrage, bis zum ersten Mal, dass etwas verschwindet, und dann ist er die einzige Sache, die zählt.

Rivertons vier Orte—zwei Regale, Rückgaben, Quarantäne—wurden in einer Stunde eingerichtet und etwa einen Monat lang richtig benutzt, bevor jemand sie zu schätzen wusste.

Der Rückgabeort war der erste, der seinen Lohn verdiente. Ein Kunde gibt zwanzig Ordner zurück, weil sie die falsche Farbe haben; der Transporter bringt sie zur Verladefläche; Tom muss entscheiden, ob sie zurück auf Ablageregal A gehen (sie sind schließlich verkaufbar) oder in Quarantäne (sie sind es nicht). Auf dem alten System wurde die Entscheidung dort getroffen, wo die Kiste abgestellt wurde, und die Kiste wurde dort abgestellt, wo immer Platz war. Auf dem neuen System ist die Entscheidung eine Lagerbewegung, und die Bewegung hat einen Grund angehängt.

Die Konsequenz erschien im Margenbericht drei Monate später: der Rückgabeort hielt einundvierzig Artikel, die „zurückgegeben" und nie geprüft waren, einige beschädigt, einige tatsächlich ein anderes Produkt. Jeder einzelne wurde als verkaufbarer Bestand gezählt. Das ist einundvierzig Artikel Bestand, die das Unternehmen für hatte und die es nicht verkaufen konnte—eine kleine Zahl, und eine perfekte Illustration des allgemeinen Prinzips: **der Wert eines Ortes ist, dass er eine Entscheidung zur Aufzeichnung zwingt.**

## Der dreiseitige Abgleich von der Seite des Lagers

Kapitel siebzehn beschreibt den dreiseitigen Abgleich vom Standpunkt des Buchhalters. Von Tom's Seite sieht er anders aus und verdient einen Absatz.

Wenn eine Lieferung eintrifft, ist die Aufgabe des Lagers, aufzuzeichnen, was tatsächlich kam: wie viele, welches Produkt, in welchem Zustand, an welchem Datum. Dieses Record ist die *Empfangsbestätigung*, und sie ist das mittlere Bein des Abgleichs. Wenn sie falsch ist—if Tom einundvierzig Paletten statt einundvierzig Ballen aufzeichnet, oder wenn er die Empfangsbestätigung zählt, bevor er zählt—dann wird der Abgleich gegen eine falsche Zahl „gelingen", und der Fehler wird den ganzen Weg in die Bücher überleben.

Dies ist der Grund, warum die Empfangsbestätigung ein Dokument mit einem Benutzer und einem Zeitstempel ist, und warum der Assistent nicht erlaubt ist, eine Empfangsbestätigung aus eigener Initiative zu validieren. Er kann eine aus einer Bestellung erstellen, was ein Vorschlag ist; ihre Validierung bedeutet *ich habe dies gezählt*, und das ist eine Aussage über die physische Welt, die nur jemand machen kann, der vor der Palette steht.

Tom's Regel, geschrieben an die Whiteboard-Wand: *das System kann raten, was sein sollte. Nur ich kann sagen, was ist.*

## Die Kosten einer falschen Zählung

Es lohnt sich, eine Zahl in die vierteljährliche Zählung zu bringen, weil „wir sollten sie häufiger tun" die Art von Rat ist, die in einem geschäftigen Monat stirbt.

Rivertons Bestand war zu Kosten etwa 180.000 Pfund wert. Die erste Zählung fand einen Nettounterschied von 1,8 Prozent—etwa 3.200 Pfund—verteilt auf elf Produkte. Das ist kein Diebstahl; es ist die kumulierte Wirkung von vierzig kleinen Fehlern: eine Palette als vierzig Paletten gebucht, eine Rückgabe ohne Prüfung zurückgelegt, eine Lieferung vor ihrer Zählung validiert.

Eine Zählung kostet zwei Menschen einen Tag, zweimal im Jahr, was etwa 1.200 Pfund Lohn ist. Sie fand 3.200 Pfund Fehler beim ersten Mal und 900 Pfund beim zweiten. Die Rechnung ist nicht subtil: ein Unternehmen, das zweimal im Jahr zählt, kauft eine 1.200-Pfund-Versicherung gegen einen 3.000-Pfund-Fehler, und der Fehler, den es verhindert, ist der, der die Bücher am Jahresende falsch macht.

Was sich mit dem System änderte, war nicht die Rechnung, sondern die *Form* der Zählung. Statt alles zu zählen und eine Liste auszugleichen, schlägt das System vor, was es glaubt, und der Zähler bestätigt oder korrigiert. Die Korrekturen werden dann untersucht, eine nach der anderen, und jede Untersuchung behebt eine Gewohnheit statt einer Zahl. Das ist der Unterschied zwischen dem Zählen von Bestand und seinem Verwalten.

## Der Lieferschein und die drei Unterschriften

Eine Lieferung bei einem Großhändler hat drei Momente, und jedes hat eine Unterschrift einer Art.

**Das Kommissionieren:** jemand nimmt die Waren vom Regal und legt sie auf eine Palette. Die Unterschrift ist die Kommissionierliste, zeilenweise unterzeichnet, und sie ist das Lager, das sagt *das ist es, was ich zusammengelegt habe*.

**Das Beladen:** die Waren gehen auf den Transporter. Die Unterschrift ist die des Fahrers, und sie ist das Unternehmen, das sagt *das hat das Gebäude verlassen*.

**Die Lieferung:** der Betreuer des Kunden unterzeichnet den Schein. Die Unterschrift ist ihre, und sie ist der Kunde, der sagt *das ist angekommen*.

In Odoo fallen die drei Momente in zwei Dokumente zusammen—die Bestellung und ihre Validierung—und das ist eine Vereinfachung, die es zu verstehen lohnt, weil dort die meisten Diskrepanzen geboren werden. Eine Palette, die kommissioniert, belastet und nie geliefert wird, hat das Bestand des Systems verlassen, aber nicht den Hof des Unternehmens; eine Palette, die geliefert, aber nie validiert wurde, hat den Hof verlassen, aber nicht das System.

Tom's Gewohnheit nach dem ersten Jahr war, die Validierung als Moment der Wahrheit zu behandeln: die Lieferung wird validiert, wenn die unterzeichnete Rückkehr des Scheins kommt, nicht wenn der Transporter abfährt. Sie macht den Bestandsbericht einen Tag spät und sie macht ihn richtig, und er hätte lieber eine richtige Zahl am Mittwoch als eine falsche am Freitag.

## Was das Lager weiß, das System aber nicht

Es gibt eine Grenze für all dies, und Tom ist der Erste, der sie beschreibt.

Das System kennt Mengen, Orte und Daten. Es kennt nicht, dass die Ecke von Ablageregal B dort ist, wo die Feuchtigkeit eindringt, dass die Papierpalette der April-Lieferung schwerer ist als die Februar-Palette, weil der Lieferanten das Ballengewicht änderte, oder dass der Fahrer, der am Freitag liefert, nicht warten wird, während man zählt.

Ein Lagermanager trägt dieses Wissen, und der Wert des Systems ist nicht, dass es es ersetzt, sondern dass es es *befreit*: eine Person, die sich nicht merken muss, wo vierhundertzwölf Ordner sind, kann die Aufmerksamkeit darauf verwenden, warum die Palette vom April falsch aussieht.

„Es ist dasselbe wie im Büro", sagt Tom. „Das System zählt. Ich bemere."

## Die Zählung

Vierteljährlich zählt Riverton.

Es ist kein angenehmer Nachmittag. Es beinhaltet ein Schreibbrett, zwei Menschen, eine Taschenlampe und ein Lager, das kälter ist, als es aussieht. Aber es ist jetzt anders, in einer Weise, die Tom eine Weile brauchte, um zu artikulieren.

„Das erste Mal zählte ich alles und gab es ein, und das System sagte mir, wo ich falsch lag", sagte er. „Das zweite Mal zählte ich nur die Dinge, die das System sagte, ich hätte sie, und es sagte mir, wo *es* falsch lag. Das ist ein anderer Job. Das erste ist eine Pflicht. Das zweite ist ein Gespräch."

Was er damit meinte, ist dies: Bei einer Bestandszählung schlägt das System eine Liste von Produkten und die Mengen vor, die es für auf dem Regal haltend glaubt, und der Zähler bestätigt oder korrigiert. Die Korrekturen werden dann überprüft, und jede ist eine kleine Untersuchung: war es eine Kommissionierfehler, eine Lieferung, die unterschrieben, aber nicht aufgezeichnet wurde, eine Rückgabe, die nie zurück aufs Regal kam?

Diese Untersuchung ist dort, wo das Geld ist. Im ersten Jahr Rivertons fand die vierteljährliche Zählung drei wiederkehrende Probleme, und keines von ihnen war Diebstahl:

- Ein Produkt, dessen Mengeneinheit 2022 falsch eingerichtet war, sodass jeder Empfang als eine Palette statt als vierzig Ballen aufgezeichnet wurde. Das System „verlor" drei Jahre lang Papier.
- Ein Lieferschein, der an der Schule unterschrieben, aber nie im System validiert wurde, sodass die Waren auf dem Regal waren und auch im Schrank des Kunden.
- Ein Rückgabeprozess, der zurückgegebene Waren ohne Prüfung wieder in Bestand legte, sodass beschädigte Artikel doppelt verkauft wurden.

Jeder dieser wurde gefunden, indem man verglich, was das System glaubte, mit dem, was wahr war, und jeder wurde behoben, indem man eine Gewohnheit änderte, nicht indem man etwas kaufte.

---

## Eine Anmerkung zum Wort „Lager"

Tom's Lager ist ein Raum mit Regalen, einer Verladefläche und einer Ecke, wo die beschädigten Dinge hingehen. In Odoo ist es ein *Ort*, und Orte können verschachtelt sein: ein Lager enthält einen Bestandsbereich, der enthält Regale, die enthalten Fächer.

Ein Unternehmen mit einem Raum braucht die Verschachtelung nicht, und Riverton benutzte sie nicht zuerst. Aber die Struktur war da, und im zweiten Jahr, wenn das Unternehmen die Einheit nebenan anmietete, war das Hinzufügen eines zweiten Lagers eine Sache des Erstellens eines Ortes und des Verschiebens von Bestand—not des Kaufens eines zweiten Systems oder des Startens eines zweiten Tabellenkalkulation.

Das ist der leise Vorteil der Modellierung der Realität statt ihrer Aufzeichnung. Eine Tabelle, die „412 Ordner" sagt, kann kein zweites Regal wachsen lassen, ohne neu aufgebaut zu werden. Ein System, das „412 Ordner, hier sind die Bewegungen, die sie dahin gebracht haben" sagt, kann einen zweiten Bau am Nachmittag wachsen lassen.

---

Tom's Bericht am Ende jenes ersten Viertels war vier Seiten lang, und er las ihn im Transporter.

„Die Sache, zu der ich immer wieder zurückkomme", sagte er, wenn er sie zurückbrachte, „ist, dass ich Dinge *kannte* und sie nicht *zeigen* konnte. Jetzt kann ich sie zeigen. Es ist das Zeigen, das das Gespräch verändert."

Maggie fragte ihn, was er meinte.

„Früher, wenn ich sagte, wir hätten zu viel Papier, war es Tom's Meinung. Jetzt ist es eine Zahl auf einem Blatt mit einem Datum darauf. Niemand streitet mit einer Zahl auf einem Blatt. Sie streiten mit Tom."

Er grinste. „Es ist sehr beruhigend."
