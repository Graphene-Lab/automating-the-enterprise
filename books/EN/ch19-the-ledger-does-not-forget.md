# 19. The Ledger Does Not Forget

The first time Doreen asked the assistant for a trial balance, she did it the way she had done it
for thirty-one years: she asked for the thing, and then she checked it against a piece of paper.

> *Show me the trial balance for this month.*

> *Trial balance, November 2026 (posted entries only):*
>
> | Account | Debit | Credit |
> |---|---|---|
> | 1100 Bank | £18,240.00 | |
> | 1210 Debtors | £9,412.80 | |
> | 2100 Creditors | | £4,718.40 |
> | 2200 VAT | | £2,906.20 |
> | 3000 Equity | | £12,000.00 |
> | 4000 Sales | | £16,512.00 |
> | 5000 Purchases | £6,720.00 | |
> | 6100 Carriage | £410.00 | |
> | 7500 Wages | £1,354.80 | |
> | | **£36,136.80** | **£36,136.80** |

She added up the columns with a calculator, because that is what she does, and they agreed. Then
she sat back and said something that sounded like a complaint and was not.

"It's the same as mine. It's exactly the same as mine."

---

## What a trial balance is, and why it is the first thing to ask for

A trial balance is a list of every account in the ledger with its balance, split into debits and
credits, with the two columns summing to the same number. If they do not sum to the same number, the
books are wrong, and the size of the difference tells you something about what went wrong.

It is the oldest report in accounting—older than the printed invoice, older than the joint-stock
company—and it is still the first thing an accountant asks for, because it is the fastest way to
answer the question *is this ledger internally consistent?*

The answer is not "is it correct?" A trial balance can balance and still be wrong: a payment posted
to the wrong customer, a sale recorded twice, an invoice dated in the wrong month. What it proves is
that every transaction has two sides, and that no side has been lost. That is the guarantee Pacioli
published in 1494, and it is why the report has not changed in five hundred years.

## The three statements, in plain words

The ledger feeds three documents that a company cannot run without, and it is worth saying what each
one is for, because they are usually explained badly.

**The profit and loss account** answers: *did we make money this period?* It takes the income
accounts (sales) and the expense accounts (purchases, wages, carriage, rent) and subtracts. It is a
film, not a photograph: it covers a period, and it starts again from zero next month.

**The balance sheet** answers: *what do we own and owe at this moment?* It takes the asset accounts
(bank, debtors, stock, equipment) and the liability and equity accounts (creditors, VAT, loans,
capital) and shows them side by side. It is a photograph: it is true at a date, and it never starts
again.

**The cash flow statement** answers: *where did the money actually go?* It is the statement small
companies ignore and should not, because a company can be profitable and still run out of money—if
its customers pay in ninety days and its suppliers want paying in thirty.

The three are connected, and the connection is the thing that makes double entry beautiful: the
profit for the period appears in the balance sheet as an increase in equity, and the movement in the
bank appears in the cash flow. If they do not reconcile, something is wrong, and the wrongness is
locatable.

## What the assistant can answer, and what it cannot

The assistant can produce any of these on request, and it can answer the questions that used to
require a spreadsheet:

> *What is our revenue this month, and how does it compare with the same month last year?*
>
> *Which expense accounts have grown the most in the last three months?*
>
> *What is the balance on the carriage account, and what does it consist of?*

That last question is the interesting one. *What does it consist of* is a request for the
transactions behind a number, and it is the question that turns an assistant from a reporting tool
into something closer to a colleague. The answer is a list of documents: carriage charged on eleven
invoices, carriage paid on four supplier bills, with dates and amounts.

What the assistant cannot do is tell you whether the number is *right*. It can tell you that the
carriage account holds £410 and that it consists of those fifteen documents. Whether £410 is a
sensible amount for a month in which the company made sixteen deliveries is a judgement about the
business, and the judgement is yours.

## The month-end, from the ledger's point of view

Closing a month is not a single action. It is a sequence of checks, each of which answers a
question, and the sequence has been the same since ledgers were written by hand:

1. **Have all the invoices been issued?** Every delivery should have an invoice; every invoice
   should have a delivery.
2. **Have all the bills been entered?** Every supplier invoice that arrived should be in the system,
   whether or not it has been paid.
3. **Does the bank agree?** The bank journal should match the statement, line by line.
4. **Do the debtors and creditors agree?** The list of who owes what should match the ledger
   accounts, to the penny.
5. **Is the stock right?** The stock valuation in the accounts should match the warehouse.
6. **Are the accruals right?** An expense that belongs to this month but has not been invoiced yet
   still belongs to this month.
7. **Is the VAT right?** The tax on the sales and purchases should match the return.

Seven questions, and each of them is a report the assistant can produce in a sentence. That is the
difference between a month-end that takes a week and one that takes an afternoon—not because the
checks are easier, but because the *asking* is.

## The five reports a wholesaler actually reads

The ledger can produce hundreds of reports. Five of them earn their place in a small wholesaler, and
the rest are occasional.

**The aged debtors list** — who owes what, by how late. It is the report that changes behaviour,
because it turns a vague worry into a name and a number.

**The stock valuation** — what the shelves are worth at cost, by category. It is the largest number
on the balance sheet of a wholesaler, and the one most often out of date.

**The margin by product or category** — sales minus cost, as a percentage. It is the report that
tells you which half of the catalogue is subsidising the other half.

**The bank position** — the book balance, the statement balance, and the difference. In a small
company this is read more often than any other, and it is the one that prevents the Friday afternoon
discovery that the payroll will not clear.

**The sales by customer, year to date** — with last year beside it. It answers the question that
matters most in a wholesale business: who is growing, who is shrinking, and who has quietly stopped.

Five reports, and the assistant can produce any of them in a sentence. The rest of the list—the
hundreds of standard reports, the pivot tables, the dashboards—are for the day somebody asks a
question that the five cannot answer, and that day is rarer than the software industry would have
you believe.

## A short history of the ledger

The word *ledger* comes from the Dutch *legger*, a book that lies flat—as opposed to the day book,
which was carried. The distinction is medieval: the day book recorded transactions as they happened,
in order; the ledger sorted them by account, so that a merchant could see the state of a relationship
rather than the sequence of events.

That two-book system survives in every ERP, and the names have barely changed: the *journal* is the
day book, and the *general ledger* is the ledger. What has changed is the effort. A medieval
merchant's clerk copied every transaction twice, by hand, and a mistake in the copying was found by
a trial balance performed at the end of the month, by adding up two columns of figures with a quill.

Doreen did the same thing with a calculator, and then with a spreadsheet, and now she asks a machine
that does it in a second and shows its working. The arithmetic has not changed. The *cost* of the
arithmetic has fallen to nothing, and the time has moved to the questions.

## Reading a trial balance

Doreen learned to read a trial balance in 1994, from a man who taught her with a pencil and a
sentence: *the numbers are not the point; the shape is.*

The shape of a healthy wholesaler's trial balance is a set of proportions. Sales are large, purchases
are most of sales, wages are a fraction, carriage is small, bank and debtors and creditors are
roughly in line with the volume of trade. If any of those proportions moves, the balance sheet is
telling you something before the profit and loss account does.

Three shapes are worth recognising.

**Debtors growing faster than sales.** The company is selling, and not collecting. It is the most
common early warning in a small business, and it appears in the trial balance a month or two before
it appears in the bank.

**Stock growing faster than sales.** The company is buying, and not selling. Sometimes that is a
purchase opportunity; more often it is a buyer who is optimising for the price of paper rather than
the cost of capital.

**Carriage rising while sales are flat.** Deliveries are getting more expensive, or smaller, or
further away. Riverton's pallet charge lived here for four months, invisible, because nobody was
reading the shape.

None of those is visible in a bank balance, and none of them requires a management accountant. They
require a report that is produced often enough to be read, and a person who knows what normal looks
like.

## The accounts a wholesaler actually needs

Doreen's final chart of accounts had thirty-one entries, and it is worth listing the ones that
earned their place, because the list is shorter than most accountants would expect.

| Class | Accounts | Why |
|---|---|---|
| Assets | Bank, Debtors, Stock, Equipment | the four things a wholesaler owns |
| Liabilities | Creditors, VAT, Payroll taxes | the three things it owes |
| Equity | Share capital, Retained earnings | the two things that make the balance sheet balance |
| Income | Sales — goods, Sales — carriage, Discounts given | three questions the owner actually asks |
| Cost of sales | Purchases — goods, Purchases — carriage, Stock adjustment | where the margin comes from |
| Expenses | Wages, Rent, Utilities, Insurance, Motor, Office, Professional fees, Bank charges | one per line of the annual accounts |

Thirty-one accounts, and every one of them is a question somebody asks. The four that were *not*
created are worth naming too: *Sundry*, *Other*, *Miscellaneous* and *General*. A company that has
those accounts has decided not to decide, and the money that goes into them is the money nobody will
ever understand again.

## The audit trail, and the question it answers

The ledger does not forget, but that phrase is doing a lot of work, and it is worth saying what it
means concretely.

For every document in the system, Odoo keeps: who created it, when, who changed it, when, and what
the previous values were. For every journal entry, it keeps the document that produced it. For every
payment, the invoice it settled and the bank line it matched.

The consequence is that a question which used to be unanswerable becomes a search. *Why is the
carriage account £410 this month?* is answered by eleven documents. *Who changed this customer's
credit limit?* is answered by a name and a timestamp. *When did this invoice stop being a draft?* is
answered by the log.

That is what an auditor is buying when they ask for a system with an audit trail, and it is what a
business owner is buying when they buy one: not the ability to catch people, but the ability to
answer questions without an argument.

---

That evening, Doreen printed the trial balance and put it in the drawer with the napkin and the
card from Gerald, and then took it out again, because it was the first month-end she had closed
without working late.

"It's not that it's faster," she told Maggie. "It's that I'm not tired. I used to do the last three
hours with a headache, and the mistakes I made in the last three hours were the ones I found the
next morning."

Maggie asked her what she had done with the time.

"I checked the carriage," Doreen said. "It's been going up since the summer and nobody's looked at
it. It's the pallet charge—the supplier's been adding it since July, and we've been paying it."

She had found, in the hour she did not spend with a headache, a recurring charge that had been
running for four months. It was not a large amount. It was, in the language of the first chapter,
the invisible tax—except this time it was visible, because somebody had the time to look.
