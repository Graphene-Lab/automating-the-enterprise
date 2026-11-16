# 14. Ein Angebot für einen Kunden

Die erste richtige Arbeit, die der Assistent in Riverton erledigte, war ein Angebot, und es ging um den Kunden, dessen Rechnung die ganze Geschichte begonnen hatte.

Die Ashfield Academy bestellte vierhundert Ringordner und zwanzig Packungen weiße Whiteboard-Stifte für den Beginn des Sommersemesters. Priya hatte die Anfrage in einer E-Mail, die sie zweimal gelesen hatte, weil die Mengen ungewöhnlich waren: vierhundert Ordner entsprachen einem Semester, und zwanzig Packungen Stifte waren mehr, als die Schule je auf einmal bestellt hatte.

Auf dem alten System hätte sie das zwölf Minuten gedauert: Buchhaltungsprogramm öffnen, Kunden finden, Angebot erstellen, zwei Zeilen hinzufügen, Preise in der Tabelle nachschlagen, die die Vertragspreise enthält, Rabatt anwenden, ausdrucken, per E-Mail senden, ablegen. Auf dem neuen System dauerte es vierzig Sekunden, und die zwölf Minuten gingen wohin, wo sie nützlicher waren—in einen Telefonanruf an Carol in Ashfield, um zu fragen, ob die Stifte für die ganze Schule oder für das Kunstabstitut waren, eine Frage eben, die eine Rückkehr verhindert.

Hier ist es, was Priya eingab.

> *Erstellen Sie ein Angebot für die Ashfield Academy über 400 A4-Ringordner, blau, und 20 Packungen Whiteboard-Stifte, bunte Farben, zu den Vertragspreisen. Lieferung an die Schule, Ende der nächsten Woche.*

Und hier ist es, was zurückkam.

> *Angebot S00012 für die Ashfield Academy erstellt: 400 × Ringordner A4 (blau) bei £3,40, 20 × Whiteboard-Stifte (Packung mit 4, bunt) bei £11,40. Netto £1.588,00, MwSt. £317,60, gesamt £1.905,60. Lieferdatum auf Freitag, 27. Juni gesetzt. Das Angebot ist im Entwurf—sagen Sie "bestätigen", wenn es eine Bestellung werden soll.*

Vierzig Sekunden, und jede Zahl darin war überprüfbar.

---

## Die Preisliste und warum der Vertragspreis kein Rabatt ist

Der Preis, den der Assistent für Ashfield verwendete—£3,40 für einen Ordner, der mit £3,95 ausgewiesen ist—stammte weder aus dem Produktrecord noch aus einem Rabatt. Er stammte aus einer *Preisliste*, und der Unterschied ist einer, den Unternehmen seit Jahren falsch verstehen.

Eine Preisliste in Odoo ist eine Reihe von Regeln, die an einen Kunden (oder an eine Kundengruppe, oder an eine Währung) angehängt sind: für dieses Produkt, oder diese Kategorie, oder alles, wenden Sie diesen Preis an, oder diesen Prozentsatz ab, oder diese Formel. Ashfield hat eine Vertragspreisliste von Januar, in einem Meeting vereinbart, auf einem einzigen Blatt unterzeichnet, und sie sagt, was die Schule für die zwölf Produkte zahlt, die sie regelmäßig kauft.

Der Unterschied zwischen einer Preisliste und einem Rabatt ist kein kosmetischer.

Ein **Rabatt** ist eine Anpassung eines Preises, angewandt auf ein Dokument, von einer Person, im Moment desverkaufs. Er ist auf dem Angebot sichtbar, er ist prüfbar, und er ist eine Entscheidung, die jemand getroffen hat.

Eine **Preisliste** ist der Preis. Sie ist keine Anpassung; sie ist es, was der Kunde zahlt, und der Listenpreis ist eine andere Zahl, die dieser Kunde nie sieht. Ein Angebot für Ashfield, das £3,95 mit einem fünfzehnprozentigen Rabatt zeigte, wäre *richtig* gewesen und zugleich eine kleine Beleidigung: es würde dem Kunden sagen, dass der echte Preis des Unternehmens höher ist und dass man ihm eine Gunst erweist.

Es gibt eine dritte Möglichkeit, die die meisten kleinen Unternehmen tatsächlich tun: eine Tabelle mit den Vertragspreisen, von einer Person konsultiert, und von Hand auf das Angebot eingetragen. Das funktioniert, bis die Person im Urlaub ist, die Tabelle veraltet ist, oder der Vertrag neu ausgehandelt wird und die Tabelle nicht.

## Was passiert, wenn der Preis falsch ist

Jedes Unternehmen hat eine Geschichte über einen Preis, der auf einem Angebot falsch war, und alle Geschichten haben dieselbe Form: Der Fehler wurde nach der Bestellbestätigung gefunden, der Kunde wurde angerufen, und jemand musste entscheiden, ob man den Preis einhält oder den Fehler erklärt.

Die Entscheidung ist normalerweise, ihn zu halten—der Unterschied ist klein und die Beziehung nicht, und die Kosten werden als Lehre abgeschrieben. Was das Unternehmen aus der Lehre lernt, ist normalerweise das falsche: *seien Sie vorsichtiger*, statt *machen Sie den Preis zu einer Tatsache statt zu einer Erinnerung*.

Eine Preisliste macht den Preis zu einer Tatsache. Sie lebt am selben Ort, sie ist datiert, sie gilt für jedes Dokument für diesen Kunden, und wenn der Vertrag neu ausgehandelt wird, ändert jemand sie einmal. Der Assistent liest sie auf dieselbe Weise wie eine Person, nur dass sie nicht vergessen kann, welche Tabelle aktuell ist.

Die eine Sache, die eine Preisliste nicht tun kann, ist *entscheiden*. Ob Ashfield fünfzehn Prozent vom Listenpreis abbekommt, oder einen Festpreis, oder einen Preis, der mit dem Papierindex steigt, ist eine geschäftliche Entscheidung, die von Menschen getroffen wird. Die Aufgabe des Systems ist es, sie exakt anzuwenden, jedes Mal, und sie sichtbar zu machen, wenn sie sich ändert—das ist das Thema des nächsten Abschnitts.

## Das Angebot, das einen Preis änderte

Drei Monate später stellte Priya eine Frage, die vorher nicht möglich gewesen war.

*Welche Kunden zahlen einen Preis, der sich seit Januar nicht geändert hat, und was würde es uns kosten, ihn um drei Prozent zu erhöhen?*

Die Antwort war eine Liste von neun Kunden und eine Zahl: etwa £4.100 zusätzliches Jahreseinkommen, mit der Rechnung pro Kunde. Die Preise hatten sich nicht geändert, weil niemand hingesehen hatte, und niemand hatte hingesehen, weil das Hinsehen das Öffnen von neun Preislisten erforderte und deren Abgleich mit den Einkaufspreisen, was einen Nachmittag gedauert hätte.

Ob die Preise erhöht werden, ist eine geschäftliche Entscheidung, und Riverton erhöhte sie für vier der neun und ließ die anderen aus Gründen in Ruhe, die mit der Rechnung nichts zu tun hatten. Aber die Entscheidung wurde mit einer Zahl davor getroffen, in zehn Sekunden, statt für ein weiteres Jahr verschoben zu werden.

Das ist wieder das Muster: Die Maschine entscheidet nicht. Sie macht die Entscheidung billig genug, um sie zu treffen.

---

## Was tatsächlich geschah

Es lohnt sich, das zu verlangsamen, weil die Geschwindigkeit nicht der interessante Teil ist.

Der Assistent wusste nicht, was ein Ringordner ist. Er hatte Ashfield Acadys Vertrag nie gesehen, und er hatte keine Ahnung, was ein Semester ist. Was er hatte, war eine Reihe von Werkzeugen und eine Beschreibung, was jedes davon tut, und ein Modell des Unternehmens, das jemand anderes gebaut hatte.

Also tat der Assistent, wenn Priyas Anweisung eintraf, was ein neuer Mitarbeiter auf seinem ersten Tag tut: Er schlug Dinge nach.

Er durchsuchte die Kunden nach einem Namen, der mit *Ashfield Academy* übereinstimmt, und fand einen—und weil er von Natur aus vorsichtig ist, hätte er gefragt, wenn er zwei gefunden hätte. Er durchsuchte die Produkte nach *Ringordner* und fand ein Produkt mit Varianten, und er wählte das blaue, weil Priya blau gesagt hatte. Er durchsuchte nach den Stiften und fand die Packung mit vier, bunt. Er fragte das ERP nach dem Preis von jedem, für diesen Kunden, an diesem Datum, was eine andere Frage ist als "was ist der Preis dieses Produkts", und der Unterschied ist das ganze zehnte Kapitel.

Dann erstellte er das Angebot: ein Dokument mit einem Kunden, einem Datum, zwei Zeilen, einer Steuerberechnung und einem Status. Und dann hörte er auf, weil ein Angebot im Entwurf keine Verpflichtung ist, und er sagte das so.

Dieser letzte Satz ist die wichtigste Sache, die der Assistent tat. Er bestätigte die Bestellung nicht. Er reservierte den Lagerbestand nicht. Er sendete niemandem etwas. Er produzierte einen *Vorschlag*, und er sagte Priya, dass der Vorschlag auf sie wartete.

---

## Die Zustandsmaschine und warum sie wichtig ist

Ein Angebot, eine Bestellung und eine Rechnung sind nicht drei Dokumente. Sie sind drei Zustände derselben Absicht, und die Übergänge zwischen ihnen sind die Momente, in denen ein Unternehmen sich verpflichtet.

**Entwurf.** Ein Vorschlag. Nichts wurde versprochen, kein Lagerbestand reserviert, der Preis kann sich ändern. In Odoo heißt das ein Angebot, und es hat ein Gültigkeitsdatum, weil ein Preis, der im Juni genannt wird, nicht notwendigerweise ein Preis im September ist.

**Bestätigt.** Eine Bestellung. Das Unternehmen hat versprochen, zu einem Preis, bis zu einem Datum, zu liefern. Lagerbestand wird reserviert (oder, in einem Unternehmen, das nicht reserviert, zumindest die Absicht verzeichnet), und das Dokument erhält eine Nummer, die auf dem Lieferschein und der Rechnung erscheinen wird.

**Geliefert.** Die Waren sind weg. Jetzt gibt es einen Lagerverzug, und ein Stück Papier, das der Kunde unterzeichnet hat.

**Rechnung.** Das Geld wurde gefordert. Jetzt gibt es einen Buchungsansatz, und einen Steuerzeitpunkt.

**Bezahlt.** Das Geld ist eingetroffen. Jetzt gibt es eine Banktransaktion, die mit der Rechnung abgeglichen werden muss, und das ist der Schritt, in dem die meisten kleinen Unternehmen den Überblick über ihre Liquidität verlieren.

Jeder Übergang ist eine Entscheidung, und die Aufgabe des ERP ist es, sicherzustellen, dass die Entscheidung bewusst getroffen wird. Ein Angebot, das sich in eine Bestellung verwandelt, ohne dass jemand entscheidet, ist eine Verpflichtung, die das Unternehmen nicht wusste, dass es eingegangen war. Eine Bestellung, die sich in eine Rechnung verwandelt, bevor die Waren weg sind, ist ein Steuerzeitpunkt, der sich ohne Erlaubnis verschoben hat.

Priya las das Angebot, änderte eine Sache—sie reduzierte die Ordner auf dreihundertfünfzig, weil das Kunstabstitut einen Schrank voller gefunden hatte—und bestätigte es.

> *Ändern Sie die Ordnermenge auf 350 und bestätigen Sie die Bestellung.*

> *Bestellungsbeleg S00012 bestätigt: 350 × Ringordner A4 (blau), 20 × Whiteboard-Stifte. Gesamt £1.712,40. Lieferdatum Freitag, 27. Juni. Lagerbestand reserviert: 350 Ordner verfügbar, Stifte verfügbar.*

Beachten Sie, was der Assistent am Ende hinzufügte: *Lagerbestand reserviert, verfügbar*. Er war nicht danach gefragt worden. Er hatte nachgesehen, weil das Nächste, was passieren würde, eine Lieferung wäre, und eine Lieferung, die nicht gemacht werden kann, ist schlimmer als ein Angebot, das nicht bestätigt werden kann.

![Die gleiche Operation auf der Demonstrationsinstallation: Bestellbeleg S00002 bestätigt, mit den Summen, dem Zustand und zwei Dingen, die der Assistent Sie wissen lassen wollte](../../assets/screens/assistant-06-order.png)

Die obige Abbildung lohnt sich, sorgfältig zu lesen, weil sie das Verhalten ist, für das dieses Kapitel argumentiert hat, eingefangen statt beschrieben. Der Assistent berichtet über die Bestellnummer, den Zustand (*entwurf → verkauf*), den steuerbefreiten Betrag, die Steuer und die Gesamtsumme; dann bietet er zwei Dinge an, die nicht gefragt wurden—dass die Steuer automatisch bei fünfzehn Prozent angewandt wurde, und dass das Bestätigen einer Bestellung weder eine Lieferung noch eine Rechnung erzeugt. Und es endet mit der Aussage, wie es nachgesehen hat: *Ich habe den Record überprüft, indem ich ihn nach der Bestätigung erneut las.*

Dieser letzte Satz ist der Unterschied zwischen einem Assistenten und einem Formular. Ein Formular sagt Ihnen, was es gespeichert hat. Ein Kollege sagt Ihnen, was er getan hat und wie er weiß, dass es funktioniert hat.

---

## Eine kurze Geschichte des Angebots

Das Wort *Angebot* stammt vom Lateinischen *quotare*, numerieren— dieselbe Wurzel wie *quote* im Sinne des Zitierens eines Abschnitts. Im Handel hat es seit mindestens vierhundert Jahren eine Preisangabe bedeutet, die einem Käufer angeboten wird, und sein rechtlicher Status wird seitdem in Gerichtssälen diskutiert.

Die Argumentation ist immer dieselbe: Ist ein Angebot ein Angebot, das sich bei Annahme zu einem Vertrag wird, oder eine Einladung zur Behandlung, die bloß eine Eröffnungshaltung ist? Die Antwort hängt von der Formulierung, dem Kontext und der Zuständigkeit ab, und das ist der Grund, warum ein Angebotsformular normalerweise eine Zeile wie *dieses Angebot gilt dreißig Tage* und *je nach Verfügbarkeit* trägt.

Ein ERP erledigt die rechtliche Frage nicht, aber es tut etwas Verwandtes und Nützliches: es verzeichnet, *welches* Angebot gesendet wurde, *wann*, *an wen*, und *was es sagte*. Wenn ein Kunde im September anruft und sagt "Sie haben mir vierhundert Pfund genannt", kann das Unternehmen das Dokument finden und sehen, ob es vierhundert oder vierhundertfünfzig sagte, und an welchem Datum, und für wie viele.

Das ist keine kleine Sache. Im alten System lebte die Antwort in einer E-Mail-Spur, in einer ausgedruckten Kopie in einem Fach, und in Priyas Erinnerung—in dieser Reihenfolge der Zuverlässigkeit.

---

## Was der Ass nicht tat

Drei Dinge lohnen sich in dem zu bemerken, was *nicht* geschah.

Er wandte keinen Rabatt an. Ashfield hat einen Vertragspreis, der ein anderer Mechanismus ist als ein Rabatt, und der Assistent verwendete den Vertragspreis, weil das die Aufzeichnung des Kunden sagt. Wenn Priya einen Rabatt gewünscht hätte, hätte sie danach fragen müssen, und der Rabatt wäre verzeichnet worden—das ist der Unterschied zwischen einem Preis und einer Gunst.

Er wählte das Lieferdatum nicht eigenständig. Er nahm *Ende der nächsten Woche* und verwandelte es in ein Datum, was eine kleine Auslegungsakt ist, und er sagte, welches Datum er gewählt hatte, damit Priya es korrigieren konnte.

Und er sendete das Angebot nicht. Senden ist eine Handlung mit einem Kunden am anderen Ende, und der Assistent hat kein Werkzeug für E-Mail in Ryertons Konfiguration—bewusst. Das Angebot wurde zu einem PDF vom ERP ausgedrückt und von einer Person an eine E-Mail angehängt, was Priya thirty Sekunden dauerte und den letzten Schritt, den, in dem ein Gebäude das Gebäude verlässt, in menschlichen Händen hielt.

Einige Unternehmen werden diesen Schritt automatisieren wollen, und das System kann es. Riverton entschied im ersten Monat, dass nichts an einen Kunden gesendet wird, ohne dass jemand darauf sieht. Es ist eine Entscheidung, die ein Unternehmen überdenken kann; es ist keine Entscheidung, die ein Unternehmen durch Zufall treffen sollte.

---

Die Bestellung lag zwei Tage im System und wartete auf das Lieferdatum.

Am Donnerstag stellte Tom dem Assistenten eine Frage, die Priya nicht zu fragen gedacht hatte.

> *Welche Orders sind in den nächsten drei Tagen zur Lieferung fällig, und ist der Lagerbestand für alle davon vorhanden?*

Die Antwort war eine Liste von vier Orders und ein Satz, der die Woche veränderte: die Ordner für Ashfield waren da, die Stifte waren da, aber die Order für Northgate Library Service benötigte zwölf Packungen A4-Papier und es waren neun.

Neun Packungen, und ein Versprechen, am Montag zu liefern. Das ist die Art von Tatsache, die früher von einem Fahrer an der Verladetür entdeckt wurde, und sie wurde stattdessen am Donnerstagmittag von jemandem entdeckt, der zu fragen dachte.
