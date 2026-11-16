# 24. Das Papier, das das Gebäude verläuft

Es gibt ein Regal im Büro von Riverton, das vier Ordner hält, und dies sind die letzten Papiere, die das Unternehmen aufbewahrt.

Es sind keine Rechnungen. Die Rechnungen sind im System und in den Postfächern der Kunden. Die Ordner enthalten die Dinge, die unterschrieben werden müssen: die Lieferscheine, die mit den Initialen eines Hausmeisters zurückkamen, die Gutschriften, die ein Kunde beanstandete, und die zwei Verträge, die wirklich zählen. Alles andere ist ein PDF.

Dieses Kapitel behandelt den Moment, in dem ein Dokument das Gebäude verläuft, also den Moment, in dem Software auf die physische Welt trifft—und in dem eine überraschende Anzahl sonst guter Systeme versagt.

---

## Was ein Dokument druckbar macht

Ein druckbares Dokument ist kein Bildschirm, der verkleinert wurde. Es ist ein anderes Objekt mit anderen Regeln, und der Report-Engine von Odoo lohnt sich zu verstehen, weil sie diese durchsetzt.

**Es hat ein fixes Layout.** Ein Bildschirm fließt um; eine Seite nicht. Die Rechnungs-Vorlage entscheidet, wo das Logo hingehört, wie breit die Beschreibungsspalte ist und was geschieht, wenn ein Produktname länger ist als die Spalte. (Die Antwort ist, dass es in einer guten Vorlage umbricht—und die Zeile wächst. In einer schlechten überlappt es den Preis, und der Kunde sieht eine Zahl, die zu einer anderen Zeile gehört.)

**Es hat eine Kopf- und Fußzeile, die sich wiederholen.** Seite eins einer fünfseitigen Rechnung muss sagen, wessen Rechnung sie ist, und Seite fünf muss sagen, dass sie Seite fünf von fünf ist. Dies ist keine Eitelkeit: eine Seite, die allein ankommt, ohne Kopfzeile, ist eine Seite, die beanstet werden kann.

**Es trägt die Identität des Unternehmens.** Name, Adresse, Steuernummer, Registrierung, Bankverbindung. Diese sind keine Dekoration; sie sind die Felder, die das Dokument zu einem rechtlichen Anspruch machen, und sie stammen aus dem Unternehmensdatensatz, der in Kapitel neun konfiguriert wurde.

**Es ist reproduzierbar.** Dieselbe Rechnung, ein Jahr später gedruckt, muss gleich aussehen. Deshalb ist die Vorlage eine Vorlage und kein Dokument, das jemand bearbeitet hat: eine Rechnung, die nachträglich bearbeitet werden kann, ist eine Rechnung, die nichts beweist.

## Die drei Dokumente, die ein Großhändler tatsächlich druckt

Riverton druckt drei Dinge, und jedes hat eine andere Aufgabe.

**Die Rechnung** als PDF, das einer E-Mail angehängt ist. Sie ist die Zahlungskündigung und das Steuerdokument, und sie ist diejenige, die die Buchhaltung des Kunden abheften wird.

**Der Lieferschein**, gedruckt auf dem Drucker des Transporters und an der Tür unterschrieben. Er ist kein Finanzdokument; er ist der Beweis, dass die Waren angekommen sind, und er ist diejenige Sache, die den Streit drei Wochen später darüber auflöst, ob das Palettenstück unterschrieben wurde.

**Die Kontoumsatzliste**, monatlich an Kunden mit mehreren offenen Rechnungen gesendet. Sie ist eine Liste, keine Forderung, und sie ist das einzelne wirksamste Inkassowerkzeug, das existiert—weil sie jeden offenen Posten vor die Person stellt, die zahlt, auf einer Seite, ohne eine Anklage.

Es gibt ein viertes, weniger offensichtliches: den **Bestandsbericht**. Er wird an niemanden gesendet. Er wird gedruckt, weil Tom ihn im Transporter liest, und das Lesen einer Sache auf Papier ist anders als das Lesen auf einem Bildschirm—langsamer und daher wahrscheinlicher durchdacht.

## Der Arbeitsablauf, der den Umschlag ersetzte

Doreens alter Arbeitsablauf war: drucken, falten, adressieren, stempeln, per Post senden, die Kopie abheften. Fünf Schritte, und der letzte war derjenige, der versagte, weil das Abheften der Schritt ist, der keine Frist hat.

Der neue Arbeitsablauf ist: erzeugen, prüfen, senden, und das System es abheßen lassen. Drei Schritte, und das Abheften ist automatisch—was bedeutet, dass es geschieht, was bedeutet, dass die Antwort eine Suche ist, wenn ein Kunde im November wegen einer Rechnung aus Juni anruft, statt einer Expedition ins Rechnungszimmer.

Die Prüfung ist der Schritt, der zählt, und er ist derjenige, den Unternehmen überspringen. Ein von einer Maschine erzeugtes Dokument ist nicht automatisch korrekt: es ist korrekt, wenn die dahinterliegenden Daten korrekt sind, und die dahinterliegenden Daten wurden von jemandem eingegeben. Doreens Gewohnheit, die sie aus der Papierära beibehielt, ist es, die erste Rechnung jeder Serie zu lesen—nicht alle, die erste—and auf den Namen des Kunden, die Adresse, die Gesamtsumme und die Steuer zu sehen. Wenn diese vier richtig sind, sind die anderen fast sicher richtig.

## Was der Assistent tut, und was er nicht tut

Der Assistent kann das PDF erzeugen und es einer E-Mail anhängen. Bei Riverton tut er das nicht, und die Entscheidung ist es wert, festgehalten zu werden, weil sie eine Wahl ist, keine Einschränkung.

Die Rolle des Assistenten ist es, *vorzubereiten*: die Rechnung erstellen, verbuchen, das Dokument erzeugen und Doreen sagen, dass sie bereit ist. Das Senden geschieht von einer Person, im Mail-Client, weil das Senden der Schritt ist, in dem ein Fehler einen Kunde erreicht—und ein Fehler, der einen Kunde erreicht, mehr kostet als die Minute, die es dauert, ihn zu verhindern.

Das ist eine konservative Wahl, und ein Unternehmen mit hundert Rechnungen pro Tag kann sie nicht treffen. Riverton hat fünfzehn, und fünfzehn Minuten menschlicher Aufmerksamkeit sind bezahlbar. Das Prinzip aber, das skaliert, ist bei jedem Volumen dasselbe: **der Schritt, der das Gebäude verläuft, ist der Schritt, in dem ein Mensch sein sollte, bis man die Maschine hundertmal korrekt hat arbeiten sehen.**

## Eine kurze Geschichte der Rechnungsform

Die gedruckte Rechnung ist ein Kind des neunzehnten Jahrhunderts, und ihre Form wurde von den Eisenbahnen und dem Telegraphen festgelegt.

Bevor das Drucken billig war, war eine Rechnung eine handschriftliche Notiz. Wenn Unternehmen wuchsten und derselbe Kunde bei mehreren Abteilungen desselben Lieferanten kaufte, wurde die Notiz zu einer Form: gedruckt mit dem Namen des Unternehmens, mit durchnummerierten Zeilen, mit Spalten für Menge, Beschreibung, Preis und Betrag. Die Spalten sind nicht beliebig—sie spiegeln die Sequenz wider, in der ein Buchhalter das Dokument prüft, von links nach rechts, endend mit der Gesamtsumme.

Die Form hat jede Technologie seitdem überlebt, einschließlich dieser, weil sie die minimale Information kodiert, die nötig ist, um einen Streit beizulegen: wer, was, wie viele, zu welchem Preis, wie viel Steuer, insgesamt, bis wann. Die Software hat die Form nicht verändert. Sie hat die Kosten ihrer Erstellung verändert, und—wichtiger—die Kosten ihres *Wiederauffindens* danach.

Diese letzte Veränderung ist diejenige, die niemand bemerkt. Im Jahr 1975 lebte eine Kopie einer Rechnung in einem Aktenschrank, in einem Ordner, unter dem Namen eines Kunden, und ihr Auffinden erforderte eine Person, die das System kannte. Im Jahr 2026 lebt sie in einer Datenbank und kann von jedem aufgefunden werden, der den Namen eines Kunden tippen kann—was bedeutet, dass sie von der Person aufgefunden werden kann, die tatsächlich am Telefon ist, statt von der Person, die zufällig weiß, wo der Ordner ist.

## Das Archiv

Jedes Dokument, das das Gebäude verläuft, sollte nachträglich auffindbar sein, und hier weichen die Gewohnheit einer kleinen Firma und die Fähigkeit eines Systems üblicherweise voneinander ab.

Odoo bewahrt jedes verbuchtes Dokument auf und kann sein PDF jederzeit neu erzeugen, was bedeutet, dass die *Datei* nicht separat archiviert werden muss: das Dokument ist die Daten, und das PDF ist eine Ansicht davon. Das ist elegant, und es ist zugleich leicht beunruhigend beim ersten Mal, wenn man es hört—was, wenn sich die Vorlage ändert und die Rechnung ein Jahr später anders gedruckt wird?

Die Antwort ist, dass sie es wird, und dass dies akzeptabel ist, weil der *Inhalt* zählt, und der Inhalt ist gespeichert. Wenn Ihre Rechtsordnung das exakte PDF wie ausgegestellt verlangt, kann Odoo das erzeugte PDF beim Verbuchen an den Datensatz anhängen, und die Datei ist dann fixiert. Riverton tut das für Rechnungen, die ins Ausland gesendet werden, wo die Steuerbehörde pingeliger ist, und nicht für die inländischen.

## Der Drucker, und alles, was mit ihm schiefgeht

Ein Kapitel über das Drucken, das den Drucker nicht erwähnte, wäre ein Kapitel, geschrieben von jemandem, der noch nie in einem Büro gearbeitet hat.

Der Drucker ist die unzuverlässigste Komponente des ganzen Stapels, und er ist derjenige, der im Moment der höchsten Dringlichkeit versagt—das ist die Natur von Druckern. Drei Dinge sind es wert, bekannt zu sein.

**Das Drucken auf PDF ist nicht das Drucken.** Jedes in diesem Kapitel beschriebene Dokument kann als PDF erzeugt werden, ohne dass ein Drucker beteiligt ist, und für Rechnungen und Kontoumsatzlisten ist das, was ein Unternehmen tun sollte: das PDF erzeugen, es einer E-Mail anhängen und das Papier für die Dinge aufbewahren, die eine Unterschrift benötigen. Der Drucker von Riverton wird für Lieferscheine und den wöchentlichen Bestandsbericht verwendet, und für nichts anderes.

**Ein Dokument, das gedruckt wurde, ist kein Dokument, das gesendet wurde.** Das klingt selbstverständlich und es ist die Quelle der Ashfield-Rechnung zu Beginn dieses Buches. Das System weiß, dass das PDF erzeugt wurde; es weiß nicht, ob die E-Mail gesendet wurde. Wenn das Senden zählt, muss das Senden festgehalten werden—was einer der Gründe ist, warum Unternehmen schließlich den ganzen Schritt automatisieren, so dass der Datensatz existiert.

**Der Papierstau ist ein Unternehmensrisiko.** Ein Lieferschein, der nicht gedruckt werden kann, ist eine Lieferung, die nicht abfahren kann, weil der Fahrer nicht ohne das Papier geht, das der Kunde unterschreibt. Jedes Unternehmen, das sich an der Verladetür auf einen Drucker verläuft, sollte einen zweiten haben oder einen Weg, die Notiz an der Adresse des Kunden zu drucken. Riverton lernte dies an einem Samstag, und nun hält es ein Ersatzgerät in einem Schrank.

## Die drei Dinge, die beim Druckvorgang schiefgehen

Jedes Unternehmen, das Dokumente druckt, hat diese drei getroffen, und jedes hat eine billige Lösung.

**Die Vorlage ändert sich, und niemand bemerkt es.** Ein Logo aktualisiert, eine Adresse geändert, eine Bankverbindung korrigiert—und die Vorlage zeigt immer noch die alte, weil die Änderung am Unternehmensdatensatz vorgenommen wurde und die Vorlage eine Kopie einliest. Odoo's Vorlagen lesen den Unternehmensdatensatz direkt, also ist dies seltener als in Systemen, die kopieren; aber eine benutzerdefinierte Vorlage kann einen Wert immer noch hart codieren, und der Weg, es herauszufinden, ist, ein Dokument nach jeder Änderung zu drucken und es zu lesen.

**Das Papier hat die falsche Größe.** Ein für A4 konfigrierter Lieferschein, auf dem Drucker des Transporters im A5-Format gedruckt, verliert seine rechtssseitige Spalte—wo die Mengen stehen. Die Lösung ist eine zweite Vor für das kleine Format oder ein Drucker, der A4 nimmt, und es lohnt sich, dies vor der ersten Lieferung zu entscheiden, nicht danach.

**Die Kopie des Kunden und die Archivkopie weichen voneinander ab.** Jemand schreibt auf die gedruckte Kopie—eine Notiz, eine Korrektur, eine Unterschrift—und das Archiv bewahrt die makellose Version auf. Das ist für die Rechnung korrekt und für den Lieferschein falsch: die unterschriebene Notiz *ist* der Datensatz, und sie sollte gescannt oder abgeheftet werden, nicht weggeworfen, weil „sie ist im System".

## Was eine Unterschrift bedeutet

Der Lieferschein kommt mit einer Kratzerei zurück, und die Kratzerei ist die rechtlich interessanteste Sache im ganzen Stapel.

Eine Unterschrift auf einem Lieferschein ist ein Empfangsbestätigung: *Ich habe diese Waren in dieser Menge empfangen*. Sie ist kein Vertrag—der Vertrag war die Bestellung—und sie ist kein Quittung über eine Zahlung. Sie ist ein Beweis, und ihr Wert ist, dass sie im Moment der Lieferung von jemandem gemacht wurde, der dort war.

Deshalb wird der Lieferschein noch gedruckt, und warum dem Assistenten nicht gestattet ist, eine Lieferung als unterschrieben zu markieren. Die Unterschrift ist ein physischer Akt einer dritten Partei, und keine Menge Software kann sie vollziehen. Was Software tun kann, ist sicherzustellen, dass die Notiz, die unterschrieben wird, die richtige ist: der richtige Kunde, die richtige Bestellung, die richtigen Mengen, und eine Seite, die der Fahrer tatsächlich im Transporter lesen kann.

Der Tag, an dem die Notiz unterschrieben wird und zurückkommt, validiert jemand die Lieferung im System—und das Papier kommt in einen Ordner für sechs Jahre, weil das lange ist, wie lange ein Unternehmen beweisen may, dass die Waren angekommen sind.

## Das Archiv gesendeter Dokumente

Es gibt eine Frage, die ein Unternehmen sich zum ersten Mal stellt, wenn ein Kunde eine Rechnung aus zwei Jahren beanstet: *können wir beweisen, was wir gesendet haben?*

Die Antwort hängt von einer Entscheidung ab, die lange vorab getroffen wurde, und es lohnt sich, sie bewusst zu treffen: bewahrt das System das *Dokument* oder die *Daten*?

Das Bewahren der Daten—der Rechnungsdatensatz und seine Zeilen—bedeutet, dass das PDF jederzeit neu erzeugt werden kann, und es wird wie die heutige Vorlage aussehen statt wie diejenige, die zum Zeitpunkt der Erstellung verwendet wurde. Für die meisten Zwecke ist das in Ordnung, und das ist es, was Odoo standardmäßig tut.

Das Bewahren des Dokuments bedeutet, das erzeugte PDF beim Verbuchen an den Datensatz anzhängen, so dass die Datei fixiert ist. Das kostet ein paar Hundert Kilobytes pro Rechnung und erledigt jeden Streit über das, was gesendet wurde, in der Form, in der es gesendet wurde.

Riverton hängt das PDF für Rechnungen an Kunden im Ausland an, wo die Steuerbehörde pingeliger ist, und für die zwei Verträge, die wirklich zählen. Für inländische Rechnungen verläuft sie sich auf die Daten, was eine Entscheidung ist, die Doreen nach Rücksprache mit ihrem Buchhalter getroffen hat, und die sie jedes Jahr wieder aufnimmt.

---

Die Ordner auf dem Regal sind die Ausnahme, die die Regel bestätigt: die Dinge, die unterschrieben werden müssen, sind noch Papier, weil eine Unterschrift in den meisten Teilen der Welt noch ein physischer Akt ist. Alles andere ist eine Datei geworden, und das Regal ist im Jahr nicht gewachsen.

Doreen bemerkte das, bevor jemand anderes es tat.

„Das Regal füllte sich bis Juni," sagte sie. „Ich musste ein neues beginnen. Dieses Jahr habe ich etwa vier Zoll verwendet."

Sie sah es einen Moment lang an.

„Es ist seltsam. Ich habe dreißig Jahre damit verbracht, Papier herzustellen, und ich vermisse es nicht. Was ich vermisse, ist zu wissen, wo die Dinge sind—und das habe ich zurückbekommen, in einer anderen Weise."

Das ist der Handel, den das ganze Buch beschrieben hat, gesagt von der Person, die ihn vollzogen hat: nicht das Verschwinden des Papiers, sondern die Rückkehr des Wissens, wo die Dinge sind, ohne der sein zu müssen, der sie abgeheftet hat.
