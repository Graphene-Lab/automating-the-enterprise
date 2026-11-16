# 18. Wenn das System Nein sagt

Die erste Ablehnung kam an einem Donnerstag Nachmittag, und es war der Moment, in dem Doreen dem System gegenüber misstrauisch wurde und begann, ihm zu vertrauen.

Sie hatte den Assistenten gebeten, einen Fehler zu korrigieren: Eine Rechnung war mit der falschen Menge gebucht worden, und sie wollte, dass dies behoben wird.

> *Ändere die Menge auf der Rechnung INV/2026/0007 von 350 auf 300.*

> *Ich kann sie nicht ändern. INV/2026/0007 ist gebucht, und gebuchte Rechnungen sind schreibgeschützt: die Buchungsansätze und der Buchungszeitpunkt sind bereits erfasst. Zur Korrektur stornieren Sie die Rechnung und stellen eine Gutschrift aus, oder Sie stellen eine Gutschrift für die Differenz aus. Welche möchten Sie?*

Doreen las es zweimal und rief dann Maggie herbei.

"Es will es nicht tun", sagte sie.

"Nicht oder kann nicht?"

"Kann nicht. Es sagt, die Hauptbuchführung ist bereits gebucht."

Diese Unterscheidung—*will nicht* gegenüber *kann nicht*—ist das Thema dieses Kapitels, und sie ist der Grund, warum ein Unternehmenssystem sich von einem hilfsbereiten Kollegen unterscheidet.

---

## Die drei Arten von Nein

Ein ERP lehnt für drei verschiedene Gründe ab, und es lohnt sich, zu lernen, sie zu unterscheiden, weil jede einzelne eine andere Reaktion erfordert.

**Das System kann es nicht tun, weil das Modell es verbietet.** Man kann keine Rechnung ohne Positionen buchen, Waren liefern, die man nicht hat, oder ein Dokument ändern, das bereits Buchungsansätze erzeugt hat. Diese Ablehnungen sind strukturell: sie schützen die Integrität des Modells, und es gibt keinen Überstieg, weil ein Überstieg die Garantie brechen würde, die das Modell überhaupt wertvoll macht.

**Das System kann es nicht tun, weil der *Benutzer* nicht berechtigt ist.** Der Assistent ist ein Benutzer mit einer Rolle, und wenn die Rolle das Löschen von Datensätzen nicht einschließt, wird die Anfrage vom Berechtigungssystem abgelehnt, bevor sie das Modell erreicht. Diese Ablehnungen betreffen die Befugnis, und sie können geändert werden—durch jemanden mit dem Recht, sie zu ändern, bewusst und mit einem Protokoll über das geschehene.

**Das System kann es nicht tun, weil die *Daten* nicht da sind.** Der Kunde existiert nicht, das Produkt hat keinen Preis, der Lagerbestand befindet sich in einem Ort, den der Benutzer nicht sehen kann. Diese Ablehnungen betreffen den Zustand der Welt, und sie sind meist die nützlichsten, weil sie auf etwas hinweisen, das behoben werden muss, statt auf etwas, das überstimmt werden muss.

Ein guter Assistent sagt Ihnen, welche Art von Nein es ist. Genau das ist oben geschehen: die Ablehnung nannte das Dokument, den Grund und zwei legale Alternativen.

## Die Ablehnungen, die Riverton etwas lehrten

Über die ersten Monate sagte das System Nein in einer Handvoll von Arten, die jeweils eine kleine Lehre waren.

**"Nicht genug Lagerbestand."** Tom bat um die Lieferung von sechshundert Ordnern, obwohl nur vierhundertzwölf vorhanden waren. Das System lehnte ab und bot an, die verfügbare Menge zu liefern und eine Nachbestellung für den Rest zu erstellen. Tom entschied sich für die Nachbestellung, und der Kunde wurde angerufen, bevor der Transporter losfuhr—was den ganzen Punkt der Ablehnung ausmacht: sie versetzte das Gespräch von der Ladebucht ans Telefon, wo es noch nützlich sein konnte.

**"Der Buchungszeitraum ist abgeschlossen."** Doreen versuchte, eine Rechnung mit Datum im Vormonat zu buchen, nachdem der Monat gesperrt war. Das System lehnte ab und erklärte, der Zeitraum sei abgeschlossen. Sie verschob die Rechnung in den aktuellen Monat und bat dann den Assistenten um eine Liste aller nach dem Abschluss gebuchten Posten—die leer zurückkam, was genau der Zweck eines abgeschlossenen Zeitraums ist.

**"Dieser Benutzer kann keine Datensätze löschen."** Der Assistent sagte, als er gebeten wurde, einen doppelten Kunden zu entfernen, dass er es nicht könne, und bot an, ihn stattdessen zu archivieren. Das Archivieren bewahrt den Datensatz und blendet ihn aus den Listen aus, was die richtige Antwort auf einen Doppelgänger mit angehängten Dokumenten ist. Die Ablehnung wurde absichtlich konfiguriert, in Kapitel zwölf, von jemandem, der sich im Voraus darüber Gedanken gemacht hatte.

**"Dieses Produkt hat keine Steuer."** Ein neues Produkt war ohne Steuersatz erstellt worden, und die Angebotskalkulation lehnte die Berechnung eines Gesamtbetrags ab. Die Ablehnung wies auf das Produktformular hin, und die Behebung dauerte dreißig Sekunden. Ohne die Ablehnung hätte das Angebot ohne Mehrwertsteuer versandt und das Unternehmen hätte es am Ende des Quartals entdeckt, in einer Erklärung, die nicht aufging.

## Das Protokoll lesen

Jede Ablehnung hinterlässt eine Spur, und zu lernen, die Spur zu lesen, ist die Fähigkeit, die einen Assistenten von einer schwarzen Kiste zu einem Kollegen macht.

Der Assistent schreibt ein Protokoll: was ihm gefragt wurde, welche Werkzeuge er wählte, mit welchen Argumenten, was zurückkam, und wie lange es dauerte. Es ist kein schönes Dokument—es ist eine Datei, in einem Ordner, mit Zeitstempeln—und es ist der erste Ort, an den man blickt, wenn etwas schiefgegangen ist.

Drei Muster sind erkennenswert.

**Eine Schleife.** Das gleiche Werkzeug mit den gleichen Argumenten aufgerufen, drei- oder viermal. Das ist der Assistent, der versucht, etwas zum Laufen zu bringen, und jedes Mal auf die gleiche Weise scheitert—meil weil ein Dokument sich in einem Zustand befindet, den er nicht erwartete. Die Ablehnung steht dreimal im Protokoll, und sie einmal zu lesen, reicht.

**Ein falsches Werkzeug.** Der Assistent wählte *erstellen*, wo er *aktualisieren* hätte wählen sollen, und das ERP lehnte ab, weil der Datensatz bereits existierte. Das Protokoll zeigt die Wahl; die Behebung liegt in der Anweisung, die *aktualisieren* nicht sagte.

**Ein stiller Erfolg, der nicht das Gewünschte war.** Kein Fehler, keine Ablehnung, ein Ergebnis, das technisch korrekt und praktisch nutzlos ist. Das ist das schwerste Muster, weil im Protokoll nichts falsch aussieht. Die Verteidigung ist die Prüfung: frage den Assistenten, was er getan hat, und vergleiche das mit dem, was du meintest.

Doreen liest das Protokoll jeden Freitag, aus dem gleichen Grund, aus dem sie früher den Kontoauszug las: nicht, weil sie ein Problem erwartet, sondern weil das Lesen die Art ist, wie man lernt, wie Normal auszusehen hat—und daher, wie man bemerkt, wenn es nicht so ist.

## Die Ablehnung, die einen Kunden rettete

Eine Ablehnung im ersten Jahr von Riverton war mehr als jeder der Erfolge wert, und sie geschah in der Mitte eines Streits.

Ein Kunde—ein großer und ein schwieriger—war mit einer Rechnung für eine Lieferung belegt worden, die dieser behauptete, nie erhalten zu haben. Der Lieferschein war unterzeichnet, aber die Unterschrift war unleserlich, und der Einkaufsleiter des Kunden bestand darauf, dass die Waren am Tor abgelehnt worden seien.

Priya bat den Assistenten um eine Gutschrift, weil der Kunde drohte, sein Geschäft woandershin zu verbringen, und die Rechnung 640 Pfund betrug.

Der Assistent lehnte ab, und der Grund, den er nannte, ist der Grund, warum diese Geschichte in diesem Buch steht.

> *Ich kann eine Gutschrift erstellen, aber Sie sollten wissen, wie sie in den Buchungen aussehen wird: eine Gutschrift ohne Rückgabe dahinter verzeichnet, dass die Waren nie geliefert wurden. Die Lieferung wurde am 3. September von Tom Beck validiert, und die Lagerbewegung zeigt 40 Artikel, die Regal A verlassen. Wenn der Kunde die Lieferung abgelehnt hat, müsste die Ware zurückgekommen sein, und es ist keine Rückgabe erfasst. Wenn sie sie nicht abgelehnt haben, würde die Gutschrift eine Ware bezahlen, die geliefert wurde. Welche ist es?*

Priya rief den Kunde an, stellte die Frage, die der Assistent gestellt hatte, und stellte fest, dass die Lieferung von einem vorübergehenden Wachmann angenommen worden war, der die Palette in einen Lagerraum stellte und niemandem davon erzählte. Die Rechnung wurde vollständig bezahlt, und der Kunde entschuldigte sich.

Die Ablehnung rettete keine 640 Pfund. Sie rettete eine Beziehung, und sie tat dies, indem sie verhinderte, dass eine Person eine Frage übersprang—was immer die Aufgabe einer guten Buchhalterin war, und was dieses System deshalb tut, weil jemand es dazu konfiguriert hat.

## Die Ablehnungen, die ein Unternehmen absichtlich entwerfen sollte

Most refusals come with the software. A few should be added, deliberately, and they are the ones that turn an ERP from a system of record into a system of control.

Four are worth considering in any company that lets an assistant write.

**A credit limit on customers.** When an order would take a customer above their limit, the system can refuse to confirm it, or require approval. The assistant will then report the refusal and the number, which is exactly the conversation a salesperson should have with the owner—before the goods leave, not after.

**A maximum discount.** Odoo can be configured so that a discount above a threshold needs a second person. The assistant cannot grant it, because the assistant is one user with one role; it can only say who could.

**A closed period.** Once a month is locked, nothing posts into it, by anybody, including the assistant. That is the single most effective control in the whole system, and it costs one setting.

**A four-eyes rule on payments.** In Odoo this is a configuration of the payment process, not a feature of the assistant, but the effect is the same: the assistant prepares the payment run, a person releases it.

None of these is a technicality. Each one encodes a decision the company has already made about how it wants to be run, and each one turns that decision into something that cannot be forgotten on a busy Friday.

## What a refusal costs

There is a cost to strictness, and it is worth naming because companies that ignore it end up turning the rules off.

A refusal stops work. Somebody has to stop what they are doing, find out why, and either fix the data or ask for an exception. In a small company, that somebody is often the owner, and the owner is often the busiest person in the building.

The cost is real, and the way to keep it small is not to weaken the rule but to make the refusal *informative*. A message that says *credit limit exceeded: £2,310 of £2,000, customer Calder and Sons, last reviewed in March* tells the person what to do. A message that says *access denied* does not.

That is the argument for an assistant in front of an ERP in one sentence: the rules are the ERP's, and the *explanation* is the assistant's.

## Why strictness is the feature

There is a temptation, when a system refuses something, to look for the setting that turns the refusal off. Most ERPs have such settings, and most of them are a mistake.

Consider what the refusals are protecting.

The refusal to edit a posted invoice protects the **audit trail**: the record of what was sent to the customer, and when. A company that can edit its own history cannot prove anything about it.

The refusal to deliver stock that is not there protects the **promise**: the customer was told a date, and the date depends on goods that exist.

The refusal to post into a closed period protects the **accounts**: a period is closed because somebody has reported on it—to the bank, to the tax office, to the owners—and reopening it silently would make the report a lie.

The refusal to let a user delete protects **accountability**: if a document can vanish, then the absence of a document means nothing.

None of these is about tidiness. Each is about the one property that makes an ERP worth its cost: that what it says is true, and can be shown to be true.

## The assistant's part in this

An assistant makes refusals *better*, in a way that is easy to miss.

A person meeting a refusal in a screen sees a red box with a code and a sentence. An assistant meeting the same refusal can explain it in the language of the business, offer the alternatives, and do the legal one if you agree. That is the difference between *Error: cannot modify a posted move* and *the invoice is posted, so it can't be edited; I can issue a credit note for the difference, or cancel and re-issue—which do you want?*

There is a risk in that fluency, and it is worth naming: an assistant that explains refusals helpfully can make them feel negotiable. They are not. The explanation is a courtesy; the rule is the rule. The assistant cannot override the ERP, because the assistant is not the authority—and any assistant that claims otherwise has been given too much power, which is a fault in the installation, not a feature of the model.

## The one refusal that is not a refusal

There is a fourth kind of no, and it is the most dangerous because it looks like a yes.

The assistant, asked a question whose answer is not in the system, may answer *plausibly*. Not because it is lying, but because that is what a language model does when it has no facts: it produces the most likely sentence. This is the hallucination problem, and the defence is architectural, not moral: the assistant must be made to get its facts from the ERP, through tools, and to say so when the tool returns nothing.

Riverton's rule, on the wall next to the napkin, is a single sentence: *if it can't show you where the number came from, don't use the number.*

That rule is why every answer in this book includes the documents behind it—the invoice number, the order, the list of moves. It is not decoration. It is the difference between a system you can audit and a system you have to believe.

---

Doreen issued the credit note, and the invoice stood.

That evening she said something to Maggie that neither of them expected.

"I like that it argues with me."

"Why?"

"Because my old system did whatever I typed. If I typed the wrong number, it took the wrong number, and it never told me. This one makes me say what I mean."

She thought for a moment.

"It's like having a bookkeeper who's been doing it for six hundred years and has no manners."

Which is, more or less, exactly what Pacioli's rules are: no manners, no memory of your excuses, and no interest in whether you are in a hurry. Just the two sides of the page, and the refusal to let them disagree.
