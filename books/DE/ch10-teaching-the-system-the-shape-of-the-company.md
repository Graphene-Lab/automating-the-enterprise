# 10. Dem System die Form des Unternehmens vermitteln

Die Diskussion über das Kontenplan dauerte zwei Tage und ging am Ende darum, ob Riverton ein Briefpapiergeschäft oder ein Unternehmen ist.

Ein Kontenplan ist die Liste der Behälter, in denen ein Unternehmen sein Geld sortiert. Jede Pfund, die fließt, wird in einen davon getan: Warenverkauf, Dienstleistungsverkauf, berechneter Frachtpreis, bezahlte Fracht, Gehälter, Miete, Strom, Bankgebühren, Warenbestand, Forderungen, Verbindlichkeiten, Mehrwertsteuer. Ein kleines Unternehmen hat vielleicht vierzig Behälter; ein großes hat vierhundert; der Unterschied ist keine Ausfeilung, sondern die Zahl der Fragen, die der Kontenplan zu beantworten hat.

Doreen wollte vierzig. Maggie wollte zwölf.

"Es ist keine Frage des Wünschens", sagte Doreen am zweiten Morgen, mit der Geduld einer Person, die etwas zum dritten Mal erklärt. "Wenn ich die berechnete Fracht nicht von der bezahlten Fracht trennen kann, kann ich Ihnen nicht sagen, ob die Lieferungen Geld einbringen."

"Können Sie nicht in die Rechnungen sehen?"

"Nicht ohne vierhundert Rechnungen zu lesen."

Das, gab Maggie zu, war ein fairer Punkt, und es ist die Regel, die jede Diskussion über den Kontenplan entscheidet: **Ein Behälter verdient seinen Platz, wenn jemand eine Frage stellt, die nur dieser Behälter beantworten kann.** Berechnete Fracht und bezahlte Fracht verdienen ihren. "Verschiedene Ausgaben" tut es nicht; es ist ein Behälter, der existiert, damit niemand sich entscheiden muss, und er wird zum Ort, an dem das Geld eines Unternehmens vergessen wird.

---

## Was das System mitbringt

Odoo fragt Sie nicht, ob Sie einen Kontenplan erfinden sollen. Es fragt Sie, in welchem Land Sie sich befinden, und installiert dann den Kontenplan, den Buchhalter in diesem Land erwarten— dieselbe Nummerierung, dieselben Namen, dieselben Steuercodes—damit Ihr Prüfer den Ort erkennt und die Steuererklärung einen Ort hat, von dem sie stammen kann.

Für Riverton bedeutete das die Installation der britischen Buchhaltungskorrektur. Es ist eines von hundert solchen Paketen; der Installer hatte den Code bereits heruntergeladen, und das Einschalten dauerte eine Minute auf dem *Apps*-Bildschirm.

![Der Apps-Bildschirm, auf dem eine Korrektur installiert wird](../../assets/screens/odoo-04-apps.png)

Wenn es fertig war, hatte das Buchhaltungsmodul einen Kontenplan, einen Satz von Steuern, vier Kassenbücher und ein Geschäftsjahr. Nichts davon war noch Riverton's, und alles war ein vernünftiger Ausgangspunkt—was genau ein Kontenplan sein sollte.

![Der Kontenplan, wie er durch die Korrektur installiert wurde](../../assets/screens/odoo-05-chart-of-accounts.png)

Die Konten sind nummeriert, und die Nummerierung ist nicht beliebig. Die erste Ziffer ist die Klasse: 1 für Vermögenswerte, 2 für Schulden, 3 für Eigenkapital, 4 für Erträge, 5 für Aufwendungen, 6 für den Warenkosten. Ein Buchhalter, der eine Bilanzprüfung liest, kann auf einen Blick erkennen, welche Art von Zahl er ansieht, in jedem Unternehmen des Landes, ohne das Unternehmen zu kennen.

Doreen ging die Liste mit einem Stift durch und tat drei Dinge.

**Sie löschte nichts.** Ein Konto ohne Tätigkeit kostet nichts, und das Löschen eines, das ein Prüfer zu finden erwartet, ist ein Gespräch, das niemand möchte.

**Sie änderte vier Kontennamen** auf die Worte, die Riverton tatsächlich verwendet. Das System nannte eines "Ware"; Riverton nennt es "Warenbestand — eingekauft". Der Name auf dem Bildschirm sollte der Name im Gespräch sein, oder die Menschen werden ihn nicht verwenden.

**Sie fügte zwei Konten hinzu:** eines für die Fracht, die Kunden berechnet wird, eines für die Fracht, die Beförderern gezahlt wird. Das waren die zwei Fragen, die sie beantworten wollte, und jetzt konnte sie es.

## Die drei Fragen, die den Kontenplan entscheiden

Doreen und Maggie entschieden ihre Diskussion mit drei Fragen, und sie sind es wert, aufgeschrieben zu werden, weil sie für jedes Unternehmen funktionieren.

**Was werden Sie jeden Monat fragen?** Die Antworten wurden Konten: Warenverkauf, Frachtverkauf, Warenkauf, Frachtkauf, Gehälter, Miete. Alles, worüber niemand fragen würde, bekam kein Konto.

**Was muss das Finanzamt getrennt sehen?** Die Antworten waren wenige—normalembewerteter Verkauf, nullbewerteter Verkauf, steuerbefreit—und sie sind nicht optional. Ein Kontenplan, der die Felder der Erklärung nicht erzeugen kann, ist ein Kontenplan, der in Panik neu erstellt wird.

**Was würde ein Prüfer zuerst verlangen?** Die Antworten waren die Bank, die Forderungen, die Verbindlichkeiten und die Warenbestände. Diese vier müssen sauber, abgestimmt und auf einen Blick verständlich sein, weil sie der Ort sind, an dem das Geld ist.

Sechzehn Konten kamen aus diesen drei Fragen zuzüglich der Steuerkonten, die die Korrektur bereits erstellt hatte. Es ist ein kleinerer Kontenplan, als ein Buchhalter zeichnen würde, und ein größerer, als ein Buchhalter mit einem Tabellenkalkulationsprogramm benötigen würde, was etwa richtig ist.

## Die Einstellungen, die leicht übersehen werden und die meisten kosten

Fünf Einstellungen auf der Unternehmensform sind leicht zu überspringen und teuer, später entdeckt zu werden, weil sie auf jedem Dokument erscheinen, das das Gebäude verlässt.

**Das Logo.** Klein, und das Erste, was ein Kunde bemerkt. Ein Unternehmen, das Rechnungen mit dem Standard-Odoo-Logo versendet, hat dem Kunden etwas darüber gesagt, wie viel Aufmerksamkeit es sich gibt.

**Die Bankangaben.** Sie gehen in den Fußzeilen jeder Rechnung. Ein Unternehmen, das sie von Hand zu jedem Dokument hinzufügt, wird irgendwann das falsche Konto zu einem von ihnen hinzufügen, und das ist ein Gespräch mit einem Kunden, der das falsche Unternehmen bezahlt hat.

**Die Standard-Zahlungsbedingungen. Dreißig Tage, oder Monatsende des Folgemonats, oder vierzehn Tage.** Ihre Einstellung auf das Unternehmen bedeutet, dass jedes neue Kunde sie erbt, und die Ausnahmen sind die Ausnahmen statt der Regel.

**Die Standard-Steuern.** Die auf ein neues Produkt angewandte Steuer, wenn niemand eine auswählt. Wenn dies falsch ist, ist jedes neue Produkt falsch, und der Fehler ist unsichtbar bis zur ersten Erklärung.

**Das Geschäftsjahresende.** Die meisten Unternehmen verwenden das Kalenderjahr, und einige nicht. Die Einstellung entscheidet, wann das Jahr endet, und seine spätere Änderung ist eine wirklich schmerzhafte Operation.

Keines davon ist schwierig, und alle sind die Art von Dingen, die auf einem geschäftigen Nachmittag übersprungen und im März entdeckt werden. Die Regel, die den Nachmittag rettet: **Füllen Sie die Unternehmensform aus, als würde ein Kunde sie sehen, weil ein Kunde sie sehen wird.**

## Die Steuern

Eine Steuer in einem ERP ist kein Prozentsatz. Es ist eine kleine Maschine mit einem Eingang und einem Ausgang: sie nimmt eine Zeile einer Rechnung, rechnet die Steuer aus, entscheidet, welches Konto die Steuer bekommt, und merkt sich die Periode, der sie angehört, damit die Erklärung erzeugt werden kann.

Die Korrektur installierte die normalen Preise: zwanzig Prozent für die meisten Waren, fünf Prozent für einige (wie Autositze für Kinder und bestimmte energiesparende Materialien), null für Bücher und für die meisten Lebensmittel. Riverton verkauft Briefpapier, das normalembewertet ist, und Papier, das normalembewertet ist, und gelegentliche Dienstleistungen, die ebenfalls normalembewertet sind. Die fünf-Prozent-Satz ist vorhanden und wird fast nie verwendet, was in Ordnung ist; das Wichtige ist, dass er existiert, damit niemand am Tresen einen vierten Satz erfindet.

Es gibt eine Falle, die es wert ist, genannt zu werden, weil sie jedes Jahr Unternehmen fängt: **die Steuer wird pro Produkt konfiguriert, nicht per Rechnung.** Wenn ein Produkt auf die falsbe Steuer eingestellt ist, wird jede Rechnung, die es enthält, falsch sein, und der Fehler wird vom Finanzamt entdeckt statt vom Kunden. Die Produktform hat ein Feld dafür, und das korrekte Ausfüllen dieses Feldes einmal ist mehr wert als jede Menge an Prüfung später.

## Die Kassenbücher

Geld kommt geht durch eine kleine Zahl von Türen, und Odoo nennt sie Kassenbücher: *Kundenrechnungen*, *Lieferantenrechnungen*, *Bank*, *Kasse*, *Verschiedene Vorgänge*. Jedes Kassenbuch hat einen Code—INV, BILL, BNK, CSH, MISC—und jedes Dokument, das durch es gebucht wird, bekommt eine Zahl in Folge.

Die Folge ist wichtiger, als es aussieht. Eine Rechnungsnummer muss eindeutig sein und muss der vorherigen folgen, weil das ist es, was die Buchführung prüfbarm macht: wenn die Rechnung 2026/0042 fehlt, wird ein Prüfer fragen, wohin sie gegangen ist. Odoo erzwingt dies, indem es verweigert, ein Dokument zu buchen, das die Folge brechen würde, was eine der kleinen Strenken ist, die das System wertvoll machen.

## Was nicht konfiguriert wurde, und warum

Es gibt eine lange Liste von Dingen, die ein Unternehmen *kann* am ersten Tag konfiguriern, und fast alle von ihnen sollten warten.

**Mehrwährungsrechnung.** Riverton kauft bei einem Lieferanten in der Eurozone, also irgendwann ja. Am ersten Tag nein: Wechselkurse, Gewinne und Verluste und die Behandlung von Fremdwährungsrechnungen sind ein Thema ihrer eigenen, und ihre vor dem grundlegenden Rechnungswesen zu tun ist, wie ein Unternehmen damit endet, eine Buchführung zu haben, die niemand versteht.

**Analytische Rechnung.** Die Fähigkeit, jede Zeile mit einem Projekt, einer Abteilung oder einem Kostenstelle zu kennzeichnen. Nützlich für ein Unternehmen mit Projekten; eine Steuer auf ein Unternehmen ohne sie.

**Mehrere Unternehmen.** Odoo kann mehrere Unternehmen in einer Datenbank halten, mit unternehmensübergreifenden Transaktionen. Riverton ist ein Unternehmen. Das Hinzufügen eines zweiten am ersten Tag ist, wie ein Unternehmen im März entdeckt, dass die Hälfte seiner Rechnungen zur falschen juristischen Person gehört.

**Budgets, Vermögenswerte, verschobene Erträge, Landungskosten.** Alle real, alle nützlich, alle später.

Das Prinzip ist das, das Sam auf die Serviette geschrieben und Maggie an das Brett geheftet hatte: installieren Sie, was Sie diesen Monat verwenden. Eine Einstellung, die niemand verwendet, ist keine Fähigkeit; es ist ein Ort, an dem jemand irgendwann einen Fehler macht.

---

## Die Bank und der Eröffnungssaldo

Es gibt ein weiteres Stück Konfiguration, das ein Unternehmen spät entdeckt und wünscht, es hätte früher getan: die Bank.

Odoo installiert ein Bank-Kassenbuch ohne Bank dahinter. Das Verbinden mit dem echten Konto bedeutet, die Angaben des Kontos einzugeben, und dann—das ist der Teil, den niemand erwartet—zu entscheiden, wie das *bestehende* Geld des Unternehmens ins System kommt.

Ein Unternehmen, das seit dreißig Jahren handelt, beginnt nicht mit Null in der Bank. Es beginnt mit dem, was die Abrechnung am Tag des Systemstarts sagt, und mit einer Geschichte, die im alten Buchhaltungsprogramm lebt. Es gibt zwei ehrliche Wege, damit umzugehen, und einen unehrlichen.

Die ehrliche Weise, für ein kleines Unternehmen, ist ein **Eröffnungseintrag**: ein Kassenbuch-Eintrag, auf den Tag vor dem Systemstart datiert, der angibt, was das Unternehmen besitzt und schuldet—Banksaldo, Warenbestandswert, was Kunden schuldig sind, was Lieferanten geschuldet wird—und das zum Eigenkapital-Konto ausgleicht. Es ist ein Schnappschuss, es ist prüfbarm, und es nimmt einen Nachmittag mit der Bilanz des Vorjahres.

Die andere ehrliche Weise ist, **die Geschichte hereinzuholen**: die alten Rechnungen und Rechnungen der Lieferanten zu importieren, so dass die altverschuldeten Forderungen und Verbindlichkeiten echte Dokumente statt einer einzigen Masse sind. Mehr Arbeit, mehr nützlich, und es lohnt sich, wenn Kunden regelmäßig spät zahlen—weil der Moment, da der Assistent überfällige Rechnungen auflisten kann, Rechnungen zum Auflisten braucht.

Die unehrliche Weise ist, das Bankkonto in ein Feld einzutippen, das so aussieht, als würde es es annehmen. Wird es. Und dann wird die Buchführung nicht ausgleichen, und jemand wird ein Wochenende damit verbringen, herauszufinden, warum.

Doreen wählte den Eröffnungseintrag, mit den altverschuldeten Forderungen, die als Dokumente importiert wurden, und der Nachmittag, den sie kostete, war der erste Mal, dass sie das System für etwas verwendete, das ihr tatsächlich am Herzen lag. Sie konfigurierte keine Software mehr. Sie bewegte die Zahlen ihres Unternehmens von einem Buchführungssatz zum anderen, und prüfte, Zeile für Zeile, dass nichts auf dem Weg verloren gegangen war.

---

## Der erste Eintrag

Am dritten Nachmittag buchte Doreen das erste Dokument.

Es war keine Rechnung, und es war kein Verkauf. Es war eine Bankzahlung: zweihundert Pfund vom Konto des Unternehmens zum Konto eines Lieferanten, für Papier, das im Oktober geliefert wurde. Sie erstellte den Lieferanten, erstellte die Rechnung, registrierte die Zahlung, und sah zu, wie die drei Dokumente sich miteinander verbanden—Rechnung zu Lieferanten, Zahlung zu Rechnung, beide zur Bank.

Dann öffnete sie die Buchführung und sah sich an, was das System geschrieben hatte.

Zwei Einträge. Zweihundert Pfund aus der Bank heraus; zweihundert Pfund von dem, was das Unternehmen dem Lieferanten schuldet. Gleich und entgegengesetzt, in zwei verschiedenen Konten, auf den Tag der Zahlung. Pacioli's Regel, durchgeführt von einer Maschine in einem Bruchteil einer Sekunde, in einer Datenbank in einem Ordner in einem Benutzerprofil.

Sie lehnte sich zurück und sagte etwas, das Maggie aufschrieb, weil es der Moment war, da das System aufhörte, Software zu sein, und die Erinnerung des Unternehmens wurde.

"Es ist dasselbe wie mein Buch", sagte sie. "Es ist genau dasselbe wie mein Buch. Nur ich kann es Fragen."

Das ist die ganze erste Woche. Keine Transformation: eine Anerkennung. Die Regeln, denen das System folgt, sind die Regeln, die sie seit dreizehnunddreißig Jahren von Hand verfolgt hat, von jemandem anderem, vor sechs Jahrhunderten, aufgeschrieben, und jetzt erzwungen von einer Maschine, die nie müde wird und nie vergisst, die zweite Zeile zu schreiben.

Der Rest des Buches ist, was passiert, wenn Sie es Fragen können—und wenn etwas anderes sie für Sie fragen kann.
