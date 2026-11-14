# 29. The Arithmetic of Not Doing It

Gerald Pryce, the accountant above the chemist's shop, had a rule about investments: *show me the
cost of the thing you are already paying for.*

Maggie had gone to see him in the spring, with the invoices for the year and a question that she
was slightly embarrassed by, because it sounded like the question of somebody who had already
decided. "Was it worth it?"

Gerald put his glasses on, which meant he was going to enjoy himself.

"Not yet," he said. "First we do the arithmetic of not doing it."

---

Most business cases for software are written the wrong way round. They list the cost of the new
thing—the licence, the hardware, the training, the consultant—and then they list the benefits in
the language of hope: efficiency, visibility, agility. The numbers on the cost side are precise,
because somebody has quoted them. The numbers on the benefit side are adjectives.

The arithmetic of not doing it is the other way round. It starts from the position that the
company is already paying for its current way of working, every single day, and that this payment
does not appear in any account because it is made in hours.

So Gerald and Maggie spent a morning with a spreadsheet—the tool that replaced the accountant's
arithmetic and did not replace the accountant—and they counted.

**The first line was the invoice run.** Riverton produced, on average, four hundred and eighty
invoices a month. Each one took, from the moment the delivery was confirmed to the moment the
envelope was in the post, between four and six minutes of somebody's time: printing, checking
against the delivery note, folding, addressing, stamping. Call it five minutes, which is sixty
hours a month, which is most of a working week and a half.

After the change, the run took eleven minutes in total, because the documents were generated and
emailed, and the checking was done by looking at a list rather than at each piece of paper. The
sixty hours did not become zero; some of them became checking, and some of them became the work
Doreen had always wanted to do. But forty hours a month came back to the company.

**The second line was the searching.** Nobody had ever measured this, because nobody measures
searching. Doreen estimated it at an hour a day, which was probably an underestimate, because
people do not count the interruptions. Twenty hours a month, gone. After the change it was
perhaps three, mostly spent looking at things that needed a decision rather than a location.

**The third line was the errors.** Twelve credit notes in the previous year, caused by wrong
prices, wrong quantities or wrong addresses, at an average of a hundred and forty pounds each,
plus the time to fix them and the small damage to the relationship. The change did not eliminate
errors, but it removed the class of errors caused by retyping, because nothing was retyped.

**The fourth line was the money that arrived late.** This is the line that surprised Maggie,
because it is not a cost in the accounts; it is a cost in the bank. The average time from invoice
to payment had been fifty-three days. After six months of statements going out on time, and of a
polite reminder that the assistant produced every Monday without being asked, it was forty-one.
Twelve days of a company's turnover, sitting in the bank instead of in the customers' accounts, is
worth more than the entire cost of the system, and it appears nowhere in a profit and loss
account.

---

Against that, the costs.

The software was free. Odoo Community, the database, the assistant and the connector are all open
source, and the licence for all of it is zero. This is not a trick and it is not a trial: it is
the business model of open source, and it is why a company the size of Riverton can afford a system
that would have been unimaginable in 1995.

The hardware was a computer that the company already owned, with enough memory and disk to run
three programs at once. If a company has to buy one, it is a capital expense of the same order as
a delivery van's annual service, and it lasts longer.

The language model was a service, paid by usage. The amount depends on the provider and on how
much the assistant is asked to do, and it is the one line that a company should watch, in the way
that it watches electricity. What matters is the ratio: the assistant is asked to do things that
would otherwise take a person minutes, and the cost of a request is measured in fractions of a
penny, so the ratio is not close.

The honest costs were the two that nobody quotes.

The first was *time to install*, which was a day of Sam Okafor's attention and a week of Maggie's,
spread over a month, mostly in the evenings. The second was *the discipline*, which is not a cost
you pay once. Somebody has to keep the product list clean, decide what the assistant is allowed to
do, read the log, and say no to the request to add one more exception. That is a permanent, small,
unglamorous job, and it is the price of the whole thing.

---

There is a trap in this arithmetic, and it is worth naming because it catches clever companies.

The trap is to automate the part that is easy to automate rather than the part that costs the most.
An assistant can be taught, in an afternoon, to produce a beautiful weekly report. The report takes
ten minutes to produce by hand. Meanwhile the process that costs forty hours a month—the invoice
run, the reconciliation, the chasing of overdue accounts—is left alone, because it is messier and
because it touches money and because somebody would have to make a decision about how it should
work.

The companies that get a return are the ones that start with the expensive, boring, repetitive
process, and accept that the first version will be imperfect. The companies that get a
demonstration are the ones that start with the report.

There is a second trap, which is the mirror image: automating something that should not be done at
all. An assistant will happily produce a report that nobody reads, at a speed that makes it
impossible to argue that it is not being produced. Before automating a task, the question is not
"can it be automated?" but "if this happened automatically, every day, would anybody be better
off?" A surprising number of office tasks fail that test, and the correct automation for them is
deletion.

## The numbers that are easy to get wrong

Three mistakes are made in almost every business case for this kind of system, and each of them is
worth avoiding because each one destroys the credibility of the whole calculation.

**Counting the hours saved as if they were money.** An hour saved is not an hour paid. If the
company does not reduce anybody's hours, the saving is *capacity*, not cash—and capacity is only
worth money if somebody uses it for something that earns. Riverton's honest version of the
calculation was: forty hours a month of capacity, of which about half was used for work that would
otherwise have been done by an agency or not at all, and half was simply a less tired office. The
second half is real and it does not appear in a spreadsheet.

**Ignoring the cost of the change.** Installation, configuration, the first month of corrections,
the training, the resistance. A business case that assumes the new system works from day one is a
business case that will be wrong by a month of somebody's time. Riverton's was two months of
Doreen's attention at about half-time, which is the largest single line in the whole calculation and
which no vendor ever mentions.

**Assuming the benefit is permanent.** A system that is not maintained decays: the product list
fills with junk, the tax codes drift, the assistant's permissions get widened "just this once". The
decay is slow and it is invisible until somebody tries to answer a question and gets a wrong answer
with confidence. The hour a week in the diary is the maintenance cost, and it belongs in the
calculation.

## What the arithmetic actually says

With the mistakes avoided, the arithmetic of Riverton's first year looks like this.

| Line | Amount |
|---|---|
| Software licences | £0 |
| Hardware (a machine the company already owned) | £0 |
| Language model usage for the year | about £90 |
| Installation and configuration (Sam's time) | £1,200 |
| Internal time to configure and correct (two months, part-time) | about £4,000 |
| **Total cost** | **about £5,300** |
| Hours returned to productive work | about 480 |
| Value of those hours at Riverton's wage rates | about £9,600 |
| Earlier collection of receivables (twelve days of turnover) | about £14,000 of working capital |
| Errors avoided (credit notes, wrong prices, missed recharges) | about £3,400 |
| **Total benefit, first year** | **about £27,000, of which £13,000 is cash** |

The working-capital line is the one that surprises people, and it is worth explaining because it is
not profit. Twelve days of turnover arriving earlier does not make the company richer; it makes the
company *safer*, because the money is in the bank when the supplier's bill arrives. For a business
with tight cash, that is worth more than the profit line, and it is invisible in a profit and loss
account.

The second-year calculation is much better, because the installation cost has gone and only the
maintenance remains: about £500 of cost against the same benefits. That is the shape of every good
software investment: expensive in the first year, cheap afterwards, and worth nothing at all if
nobody maintains it.

## The comparison that matters

The comparison a company should make is not between this system and no system. It is between this
system and *the way the company works now*, with all its costs counted—including the ones that do
not appear in the accounts.

Riverton's old way cost, per year: sixty hours a month of invoicing and filing (about £18,000 at
loaded wage rates), an unknown quantity of searching and asking (probably £6,000), twelve credit
notes from retyping errors (£1,700), and twelve days of receivables permanently in the customers'
accounts (which is a permanent loan of about £14,000 of working capital, at whatever the overdraft
costs).

Against that, the new way costs £500 a year after the first, plus an hour a week of attention.

The comparison is not close, and it never is—for any company that produces documents and wants to
know what is true. What stops companies is not the arithmetic. It is the change, and the fear of it,
and no spreadsheet addresses that.

---

Gerald added up the columns, took his glasses off, and gave Maggie the answer in the way that
accountants do: not a number, but a sentence with a number inside it.

"The hours you got back are worth about thirty-one thousand pounds a year at the wages you pay,"
he said. "The money that arrived twelve days earlier is worth more than that, and it is not
income, it is oxygen. The errors are worth four thousand. Against that, your costs are the machine,
the model and your own time, which you have not charged for and should."

"So it was worth it."

"It was worth it *if you keep doing the discipline*," he said. "If you stop, the system will drift
back to being a very expensive filing cabinet within a year. I have seen it happen. The software
does not fail. The habits do."

That is the sentence to remember from this chapter, and it is the least commercial sentence in the
book. The arithmetic of not doing it is favourable, decisively so, for almost every company that
produces documents and wants to know what is true. But the arithmetic only holds while somebody
keeps the model honest, and that somebody is a person, and that person has to be given the time.

---

Maggie wrote the numbers on a card and put it in the drawer with the napkin. Then she did something
that Gerald had not suggested, and that he approved of when she told him.

She gave Doreen a title.

It was not a grand title—*office systems and exceptions*—and it came with no more money, because
Riverton is a small company and money is real. But it came with an hour a day that was protected,
in the diary, for the work of noticing: checking prices, reading the log, asking the assistant
questions whose answers might be uncomfortable.

The card in the drawer said what the system was worth. The hour in the diary was what made the card
true.
