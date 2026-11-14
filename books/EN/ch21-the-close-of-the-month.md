# 21. The Close of the Month

Closing a month is the closest thing a small company has to a religious ritual, and like most
rituals it is performed because the alternative is worse.

The purpose is simple: to declare that a period is finished, that its numbers are final, and that
nothing will be added to it afterwards. Everything a company does with its accounts—paying tax,
reporting to a bank, valuing the business, paying a dividend—depends on there being periods with
edges.

Doreen used to close a month in four evenings, with a calculator, a printed bank statement and a
list of things she did not want to look at. The first close with the system took an afternoon, and
the second took ninety minutes. This chapter is what happened in between.

---

## The seven checks

Chapter nineteen listed the questions. Here is what they look like as work.

**One: every delivery has an invoice, and every invoice has a delivery.** The assistant produces
the list of delivered orders not yet invoiced, and the list of invoices with no delivery behind
them. The first should be empty by the end of the month; the second should be empty always, because
an invoice without a delivery is either a service (fine) or a mistake (not fine).

**Two: every supplier bill that arrived is in the system.** This is the check that requires a
physical act—emptying the post tray, opening the emails—and no system can do it for you. What the
system can do is tell you what it expects: the list of purchase orders that have been received but
not billed.

**Three: the bank agrees.** The bank journal is compared with the statement, line by line. Odoo can
import a statement file and propose matches; the proposals are accepted or rejected by a person.
This is the check that used to take Doreen three hours and now takes forty minutes, and the forty
minutes are spent on the six lines that did not match automatically—which are, of course, the
interesting ones.

**Four: debtors and creditors agree.** The list of who owes what, aged, against the ledger account.
If they differ, there is an entry with no partner on it, and finding it is a search rather than an
investigation.

**Five: the stock is right.** The stock valuation in the accounts against the warehouse. A
difference here is usually a delivery that was never validated, or a cost that has not been
recalculated.

**Six: the accruals are right.** An expense that belongs to this month and has not been invoiced
yet—the electricity, the quarterly rent, the accountant's fee—has to be recorded, or the month's
profit is flattered and the next month's is punished.

**Seven: the VAT is right.** The tax on sales and purchases, against the return. This is the check
that has a deadline attached, and the one where an error is most expensive.

Seven checks, and the system's contribution is not that it performs them. It is that it makes each
one a *list* rather than an *excavation*.

## The VAT return, which is the close with a deadline

Everything in this chapter so far is voluntary: a company closes its month because it wants to know
where it stands. The VAT return is not voluntary, and it is the one part of the close where an error
has a price attached.

The return is, in essence, a summary of two numbers: the tax charged on sales, and the tax paid on
purchases, with the difference going to or coming from the tax office. A child could do the
arithmetic; the difficulty is entirely in the *classification*—which sales are standard-rated, which
are zero-rated, which are outside the scope, and which purchases are recoverable.

Odoo produces the return from the tax codes on the documents, which is why chapter ten insisted that
the tax is configured on the product and not typed on the invoice. A single product with the wrong
code produces a return that is wrong in a way that is invisible: the total is plausible, the
arithmetic is correct, and the classification is false.

Doreen's habit, kept from the paper era, is to reconcile the return to the ledger before submitting
it: the sales figure on the return must equal the credit balance on the sales accounts for the
period, and the purchase figure must equal the debit balance on the purchases. If they agree, the
classification is at least internally consistent. If they do not, the difference is a document with
the wrong code, and finding it is a search rather than a guess.

The assistant does that comparison in a sentence, and it is the single most valuable thing it does
in the whole accounting cycle, because it turns a two-hour reconciliation into a check.

## Closing the year

The year-end is the month-end with more ceremony and higher stakes, and the same seven checks apply,
with three additions.

**The stock valuation** has to be right, because it is the largest number on the balance sheet of a
wholesaler. A stock count in the last week of the year is not a formality; it is the difference
between a profit and a loss.

**The accruals and prepayments** have to be complete: an insurance premium paid in November for the
following year belongs partly to next year, and a company that ignores this reports a profit that
does not exist.

**The directors' or owners' accounts** have to be tidy, because the tax office looks at them first.

And then the year is locked, and the accounts are filed, and for eleven months nobody looks at them
again—which is why the *monthly* close matters more than the annual one. A company that only looks
once a year is driving with the windscreen painted over and a annual glance in the mirror.

## The close in a company of one

Most of this book assumes a company with an office: several people, a division of labour, somebody
who can check somebody else's work. The close looks different in a company of one, and it is worth
a section because a great many businesses are exactly that.

In a company of one, there is no separation of duties. The person who raises the invoice posts it,
pays it, reconciles it and closes the month. The controls that protect a larger company—approval
limits, four eyes, a different person releasing the payment—do not exist, and cannot be invented by
software.

What the system can do instead is make the *record* complete, so that the absence of a control is at
least visible. Three habits are worth more than any setting.

**Do the close in one sitting, at a fixed time.** A month-end spread over three evenings is a
month-end with three chances to lose the thread. The system makes the sitting possible: two hours,
once a month, with the seven lists in front of you.

**Write the reasoning down.** When an expense is unusual, when a customer's balance looks wrong,
when a supplier's invoice does not match: a line in a file saying what you decided and why. Six
months later, that line is the only thing that will remind you.

**Keep the bank reconciliation current.** In a company of one, the bank statement is the only
independent witness. Reconciling it weekly rather than monthly turns a two-hour investigation into
four ten-minute ones, and it catches the mistake while you still remember making it.

The assistant helps here in a way that is easy to underestimate: it can be asked *does anything look
wrong this month?* and it will produce the exceptions—the odd amount, the missing reference, the
customer who paid twice. In a company with a finance department, that question is asked by the
finance department. In a company of one, nobody asks it unless the system does.

## The close as a conversation

The most useful thing the assistant did during Riverton's first close was not produce a report. It
answered a question in the middle of one.

> *The bank reconciliation has six unmatched lines. What are they?*

> *Six unmatched lines, total £3,412.60:*
> *1. 2 Nov, £1,200.00 credit — payment from Calder & Sons, no invoice reference.*
> *2. 3 Nov, £14.50 debit — bank charge, no entry in the books.*
> *3. 7 Nov, £2,000.00 debit — transfer to the savings account, not recorded.*
> *4. 9 Nov, £88.10 debit — card payment to a stationery supplier, no bill.*
> *5. 11 Nov, £60.00 credit — refund from the courier, not recorded.*
> *6. 12 Nov, £50.00 credit — unknown payer, reference "INV 2025".*

Six lines, six stories. A customer paid without a reference; the bank charged a fee; Maggie moved
money to savings; somebody bought something on the company card; a courier refunded a charge; and
somebody paid fifty pounds against an invoice from 2025, which is either a very late payment or a
mistake.

The old version of this conversation happened three weeks later, by telephone, with a bank, and it
was called "a query". The new version happens on the second working day of the month, in a window,
and it is called "Tuesday".

## Locking the period

When the seven checks are done, the period is locked. In Odoo this is a setting on the accounting
period—an *end date* beyond which entries cannot be posted—and it is the closest thing the system
has to a seal.

Locking is a promise to the future: whatever the numbers say, they will still say it next year. It
is also a promise to the past: nobody can quietly improve last quarter's results by moving an
expense into it.

Companies resist locking, and the resistance is understandable. Locking means that a mistake found
in March cannot be fixed in January; it has to be fixed in March, with an explanation. That is
inconvenient, and it is the whole point: an account that can be rewritten is not an account.

## The first close, and what it felt like

Doreen's account of the first close is worth quoting at length, because it is the most honest
description of this kind of change that this book has.

"I sat down at nine expecting to be there till seven. I had the calculator, I had the statements
printed, I had a sandwich. And then I asked it for the seven lists and they came back, one after
another, in about ten minutes, and I thought: right, now the work starts.

"But the work was just... looking at the lists. The bank had six lines and I knew what four of them
were. The delivered-not-invoiced list had two orders on it, and one of them was a sample we'd sent
to the garden centre, which shouldn't have been invoiced at all, so I fixed the delivery instead.
The stock was out by forty reams, which was the pallet that came in on the Thursday and got booked
in as forty pallets—that was my mistake, from the unit of measure, and I found it in four minutes
because the system showed me the move.

"By half past two I'd done everything except the VAT, and the VAT took an hour because I always
check it twice. And then I locked the month, and I sat there, and I didn't know what to do with
myself."

She paused.

"Thirty-one years, and I've never finished a close in a day. I've never finished one without a
mistake I found the next morning. The mistakes were always in the last three hours, when I was
tired."

## What the time was for

The interesting question is not how the close got faster. It is what the time was spent on instead.

In Riverton's case, three things.

**The pallet that was booked in as forty pallets** was found and corrected in the same month, rather
than being discovered by a stock count in December. That is a difference of real money.

**Two orders that had been delivered and not invoiced** were invoiced in the month they belonged
to, which moved £3,400 of revenue into the correct period—and, more importantly, into the correct
tax return.

**And the six bank lines** produced a conversation with the courier about a refund nobody had
noticed, and a decision to stop using the company card for small purchases, because the receipts
were a mess.

None of those is dramatic. Together they are the difference between a set of accounts that is a
record and a set of accounts that is a *tool*—something you can use to make a decision, because you
trust it and because it is not three weeks out of date.

---

The month-end ritual has one more function that is rarely spoken about, and it is worth saying
plainly.

It is the moment when somebody looks at the whole business. Not the sales, not the stock, not the
bank—the whole thing, at once, with a deadline. A company that closes its month properly has, twelve
times a year, a moment in which somebody competent sits down and asks *does this make sense?*

Most small companies do not have that moment. They have a tax return, prepared in a hurry, by an
accountant who sees the numbers twice a year. The difference between those two companies is not the
software. It is whether anybody ever looks.

The software's contribution is to make the looking cheap enough that it happens.
