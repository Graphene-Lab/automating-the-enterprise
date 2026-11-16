# 26. La biblioteca, dipartimento per dipartimento

Questo capitolo è un elenco, ed è pensato per essere usato piuttosto che letto.

Ogni istruzione qui sotto è stata eseguita sull'installazione descritta in questo libro, contro una
compagnia con clienti, prodotti, magazzino, ordini e fatture. Il risultato è indicato dove non è
evidente, e quelli che non sono riusciti al primo tentativo sono marcati, con ciò che ha dovuto
cambiare—perché una biblioteca di istruzioni che contiene solo quelle riuscite è una biblioteca di
menzogne.

Adatta i nomi. I prodotti di Riverton sono raccoglioni con anelli e carta; i tuoi non lo sono. La
*forma* di ogni istruzione è ciò che vale la pena copiare: un verbo, un oggetto, un ambito e un
vincolo.

---

## Clienti

**1.** *Quanti clienti abbiamo, e quanti di loro hanno effettuato un ordine negli ultimi novanta
giorni?* — Due numeri, e il secondo è quello che conta. Un elenco di clienti che cresce solo è un
elenco di persone che hanno smesso di comprare.

**2.** *Trova il cliente chiamato Ashfield Academy e mostrami il suo indirizzo, il numero di
telefono e le condizioni di pagamento.* — La prima cosa che chiunque fa al telefono. Ha sostituito
tre schermate e una ricerca.

**3.** *Crea un nuovo cliente chiamato Northgate Library Service, a Mill Lane 14, Northgate, con le
stesse condizioni di pagamento di Ashfield Academy.* — *Stesse di* è la parte utile: copia una
configurazione reale piuttosto che una indovinata.

**4.** *Quali clienti non hanno ordinato nulla negli ultimi sei mesi, e qual è stato il loro ultimo
ordine?* — L'elenco che ha salvato il garden centre nel capitolo venti.

**5.** *Aggiungi un secondo contatto a Ashfield Academy: Carol Whitfield, ufficio finanziario, e
rendila il contatto per le fatture.* — Una piccola istruzione che un tempo richiedeva di sapere dove
i contatti vivono nel menu.

**6.** *Show me the ten customers with the highest total invoiced amount this year.* — Una
classifica, con i numeri alle sue spalle.

## Vendite

**7.** *Crea una quotazione per Ashfield Academy per 400 raccoglioni con anelli e 20 scatole di
penne per lavagne bianche, ai prezzi standard.* — Il primo vero pezzo di lavoro, nel capitolo
quattordici.

**8.** *Show me the quotation I created for Ashfield Academy today, with its lines and total.* — Il
controllo. Chiedi sempre il controllo.

**9.** *Confirm the Ashfield Academy quotation and tell me the sales order number.* — La transizione
dalla proposta alla promessa.

**10.** *Create a quotation for Northgate Library Service for 12 boxes of A4 paper and 6 packs of
pens, delivery next Monday.* — *Next Monday* is interpreted and reported back as a date, which is
how you find out that the machine and you disagree about which Monday.

**11.** *What is the total value of all quotations that are still open, and who are they for?* — The
pipeline, without a CRM module.

**12.** *Which products did we sell most of last month, by quantity?* — The simplest useful report
in any wholesale business.

**13.** *Change the delivery date on the open Ashfield Academy order to the end of the month.* — A
change to a confirmed document, which the ERP allows only while it is not yet delivered.

**14.** *Cancel the quotation for Northgate Library Service and tell me what state it is in now.* —
*What state is it in now* is the verification, and it is what makes a cancel safe.

## Fatturazione

**15.** *Create an invoice from the confirmed Ashfield Academy sales order.* — The link between the
order and the bill, which is the whole reason an ERP exists.

**16.** *Post the Ashfield Academy invoice and tell me its number and total.* — Posting, the moment
the ledger changes.

**17.** *Which invoices are unpaid and more than thirty days old? Show me the customer, the invoice
number, the date and the amount outstanding.* — The ageing report, in a sentence.

**18.** *Register a payment of the full amount against the Ashfield Academy invoice, dated today, by
bank transfer.*

**19.** *Show me the payment status of every invoice for Northgate Library Service.* — A customer
statement, without generating one.

**20.** *Create a credit note for Ashfield Academy for 20 ring binders that were returned damaged,
and post it.* — The correction that does not rewrite history.

**21.** *How much money is owed to us in total, and how much of it is overdue?* — The two numbers a
business owner looks at first.

**22.** *Send a polite payment reminder to every customer with an invoice more than fifteen days
overdue.* — At Riverton this produces drafts, not emails: the sending is a person's decision. The
instruction works either way; the configuration decides which.

## Magazzino

**23.** *How many ring binders do we have in stock right now, and where are they?* — The question
that made Tom believe the system.

**24.** *Which products are below their reordering point?* — The list that becomes a purchase order.

**25.** *Confirm the delivery of the Ashfield Academy order and tell me which stock moves it
created.* — The moves are the evidence that the stock left.

**26.** *Record a stock adjustment of minus 5 boxes of whiteboard markers, reason: damaged in the
rain.* — The reason is not optional; it is what makes the adjustment reviewable.

**27.** *What is the total value of the stock in the warehouse at cost?* — A number most small
companies cannot produce, and which changes how they buy.

**28.** *Show me every stock move for the ring binders in the last thirty days.* — The audit of a
single product, which is how a discrepancy is explained.

**29.** *Which products have not moved at all in the last year?* — Dead stock, which is money
asleep.

## Acquisti

**30.** *Create a purchase order for 500 ring binders from our usual supplier, at the last price we
paid.* — *Last price we paid* is a fact from the history, not a list.

**31.** *Confirm the purchase order and tell me when the goods are expected.* — Confirming creates
the expected receipt, which is what makes the next delivery answerable.

**32.** *Receive the goods for the purchase order and show me the stock it added.*

**33.** *Create the supplier bill for that purchase order and post it.* — The third leg of the
three-way match.

**34.** *Which suppliers have raised their prices in the last six months, and by how much?* — The
question that found the pallet charge in chapter nineteen.

**35.** *How much do we owe each supplier right now?* — The mirror of the ageing report.

**36.** *Which purchase orders are late, and by how many days?* — Suppliers who are late are a
purchasing problem, not a warehouse problem, and the distinction matters.

## Contabilità

**37.** *Show me the trial balance for this month.* — The oldest report in accounting, produced in
a second.

**38.** *What is the balance of the bank account today, according to the books?* — *According to the
books* is the honest qualifier: the bank and the books agree after reconciliation, not before.

**39.** *Show me every journal entry posted in the last seven days, with the document they came
from.* — The trace from a number back to a document.

**40.** *What is our revenue for this month so far, and how does it compare with last month?*

**41.** *List the taxes configured for this company and the rate of each.* — The check that prevents
a fourth VAT rate being invented at the counter.

**42.** *Which expense accounts have no activity this year?* — Either a chart of accounts that is
too big, or an expense that has been booked somewhere else. Both are worth knowing.

## Rendicontazione

**43.** *Give me a one-page summary of the business this week: sales, invoices, overdue money, stock
alerts.* — The Monday list, on demand.

**44.** *Which five products have the best margin, and which five have the worst?* — The report that
changes a price list.

**45.** *Show me sales by month for this year, as a table.*

**46.** *Which salesperson has invoiced the most this quarter?* — Only meaningful if the invoices
carry a salesperson, which is a configuration decision made in week one.

**47.** *What percentage of our invoices are paid late, and what is the average delay?* — The
measurement that turned Riverton's "we get paid eventually" into twelve days of turnover.

**48.** *Compare the number of orders this month with the same month last year.*

**49.** *Which customers owe us money and have also stopped ordering? That is the risk list.* — The
instruction that saved the garden centre. Naming the list in the instruction—*that is the risk
list*—tells the assistant what the list is for, and the answer comes back annotated.

## Manutenzione

**50.** *Find any duplicate customers with the same name and show them to me.* — Show, not merge. A
machine should not decide which of two records is real.

**51.** *Which products have no price set?* — The error that stops a quotation.

**52.** *List the products whose name does not match their internal reference.* — A small
consistency check that catches years of accumulated carelessness.

**53.** *Are there any quotations older than ninety days that are still open? Archive them.*

**54.** *Check the connection to Odoo and tell me which version is running.* — The first instruction
anybody should type, on any installation, ever.

## Lavoro ricorrente

**55.** *Every Monday at eight, send me a list of invoices that became overdue in the previous week.*

**56.** *Every Friday afternoon, tell me which products fell below their reordering point during the
week, and propose the purchase orders in draft.*

**57.** *On the first working day of the month, produce the previous month's sales summary by
customer.*

**58.** *Every morning, check the connection to Odoo and tell me if anything is wrong.* — Useful
only if the answer is silent when everything is fine; a daily "everything is fine" trains people to
ignore the messages.

**59.** *Every Thursday, list the purchase orders that are late and the suppliers who are
responsible.*

---

## Come usare questo elenco nella prima settimana

Un lettore che provi a lavorare attraverso questo capitolo in ordine fallirà, ed è utile dire il
perché.

Le istruzioni assumono una compagnia con dati al suo interno: clienti, prodotti, magazzino, ordini.
Su un'installazione nuova la maggior parte di esse restituisce nulla, che è corretto e
demotivante. L'ordine che funziona è l'ordine seguito dal libro: crea un cliente, crea un prodotto,
metti stock su una mensola, fai una quotazione, confermala, consegnala, fatturala, registrala,
paga. Dopo quello, ogni istruzione di questo capitolo ha qualcosa su cui lavorare.

La seconda settimana è quando l'elenco diventa utile: scegli un dipartimento, leggi le sue
istruzioni, e prova le quattro che descrivono il lavoro che fai ogni settimana. Scarta il resto. Una
compagnia non ha bisogno di una biblioteca di cinquantanove istruzioni; ha bisogno delle otto che
usa davvero, scritte a mano, con le parole sue.

La terza settimana è quando la compagnia scrive la propria. È il momento in cui la tecnologia cessa
di essere qualcosa che è stata installata e diventa qualcosa che è usata—e il test è semplice:
l'elenco contiene un'istruzione che non è in questo capitolo? Se la contiene, l'ufficio ha iniziato
a pensare nel linguaggio del sistema, che è l'unico risultato durabile di tutto questo.

## Quelle che hanno bisogno di un secondo tentativo

Quattro istruzioni non sono riuscite al primo tentativo durante i test dietro questo libro, e ogni
fallimento vale la pena registrare perché è dello stesso tipo.

**"Show me the products we never sold."** — Ambiguous, as chapter thirteen describes: no sales order
line, or no movement of any kind? The fixed version names the test: *products with no sales order
line and no direct delivery in the last year.*

**"Send the invoice to the customer."** — At Riverton the assistant has no email tool, by design. The
instruction was refused, correctly, and the working version is *produce the invoice PDF and tell me
it is ready.*

**"Delete the duplicate customer."** — Refused: the Agent user cannot delete. The working version is
*archive the duplicate*, which is also the right answer.

**"How much did we make last month?"** — Ambiguous between revenue, gross margin and profit. The
fixed version is *what was our net profit last month, and what is it made of?* — and the answer comes
back with the components, which is more useful than the number.

The pattern in all four: the assistant was literal, the person was vague, and the fix was to say
what was meant. That is not a limitation of the technology. It is the same requirement that
management has always had of the people it delegates to, and it is the reason this chapter is
organised the way it is—by department, in the language of the work, with the checks attached.

---

One last note, about the library as a *document*.

Riverton keeps its own version of this list in a shared file, and it grows by about one instruction a
month. Every instruction in it was tried, and the ones that did not work were deleted rather than
kept "in case". The file is four pages long, and it is the most-read document in the company after
the price list.

That is what a prompt library should be: not a manual, not a list of tricks, but the accumulated
vocabulary of a company that has learned to say what it means.
