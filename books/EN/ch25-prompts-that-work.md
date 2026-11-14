# 25. Prompts That Work

By the spring, Riverton had a document on the shared drive called *How to ask*, and it was four
pages long. Nobody had written it as a manual; it had grown out of an email thread in which people
posted the instructions that had worked, and the ones that had not, and by the time Maggie printed
it out it had become the most-read document in the company.

This chapter is that document, rewritten.

---

## The four parts of an instruction

Every instruction that worked, in the months of testing behind this book, had four parts, whether
or not the person writing it was aware of them.

**A verb.** What to do. *List. Create. Change. Cancel. Total. Compare. Send.* An instruction without
a verb is a topic, and the assistant will answer it with a paragraph of conversation rather than
with work.

**An object.** What to do it to, named the way the company names it. *The invoices for Ashfield
Academy. The ring binders. The purchase order from Tuesday.* If the object is ambiguous—*the
order*—the assistant has to guess, and it will guess plausibly rather than correctly.

**A scope.** Which ones, how many, over what period. *Unpaid invoices older than thirty days. Orders
from last month. The five products with the lowest stock.* Scope is where most instructions fail,
because a human being asking a colleague would rely on shared context, and the assistant has none
unless it is given.

**A constraint, when there is one.** *At the standard prices. Delivery next Monday. Do not post
it yet.* A constraint is the difference between a draft and a commitment, and it is the part people
forget, and then blame the machine for doing what it was told.

Compare:

> *Do the invoices.*

> *Create invoices from every confirmed sales order dated last week, leave them in draft, and tell
> me the total.*

The first is what people type when they are in a hurry, and the answer they get is either a
question or a guess. The second is forty seconds of typing and it produces work.

## The difference between a question and an action

The assistant can do two quite different things, and the same words can trigger either.

A **question** produces an answer: *how many customers owe us money?* Nothing in the ERP changes.

An **action** produces a document: *create the invoice.* The ERP changes, permanently, with a
timestamp and a user name attached.

The difference matters because the two have different costs of error. A wrong answer costs a
minute; a wrong invoice costs an afternoon. The safe habit—and the one the book recommends from the
first day—is to ask the question first, and then act on the answer:

> *Which invoices are overdue by more than thirty days? List them with the amount and the customer.*

and then, having read the list:

> *Create a reminder for the three largest, in draft, and show me the text before sending.*

That two-step habit is not timidity. It is how a good employee works with a new system: look, then
act.

## Naming things the way the company names them

An ERP has three names for everything: the name on the record, the internal reference, and the name
people use. The assistant works with the first two, and the third is the one in your head.

Riverton discovered this the first week. Somebody asked for *the blue binders* and got a list of
nothing, because the product is called *Ring binder A4*, with a colour variant, and the word "blue"
lives in the variant, not in the name. Once the request became *A4 ring binders, blue variant*, it
worked.

The fix is not to teach the assistant synonyms. The fix is a company habit: when a product, a
customer or a document has a name in the system, use that name in the instruction. It is the same
discipline as using the customer's account number when you telephone the bank.

## The instructions that work best

Four kinds of instruction produced the best results in testing, and they are worth learning
deliberately.

**The sweep.** *List everything that matches this condition.* Sweeps are where the assistant beats a
person outright, because a person has to open screens and the assistant does not. *Every invoice
unpaid for more than thirty days. Every product below its reordering point. Every customer who has
not ordered since January.*

**The chain.** *Do this, then that, then tell me.* Chains are the assistant's second great strength:
it does not lose track between steps. *Create the order, confirm it, deliver it, invoice it, and
give me the invoice number.*

**The comparison.** *Compare this period with that one.* Comparisons are where a person would have
to export two spreadsheets. *Compare this month's sales with the same month last year, by product.*

**The exception.** *Tell me only about the things that are wrong.* This is the most valuable and the
least used. *Show me the stock adjustments where the reason is missing. Show me the invoices whose
total does not match the order.*

## What not to ask

Four kinds of instruction produced nothing useful, and the failures are consistent enough to be
worth naming.

**The vague verb.** *Handle the invoices. Sort out the stock. Deal with the overdue accounts.* The
assistant will ask what you mean, which is the correct behaviour and a waste of a minute.

**The request for a judgement it cannot make.** *Which customers are worth keeping?* It can give you
the numbers—revenue, margin, payment behaviour, how long they have been quiet—and it can rank them.
It cannot tell you what your company values, because that is not in the database.

**The instruction that depends on something not in the system.** *Invoice the job we did for the
school last Thursday.* If the job was never recorded, the assistant will find nothing, and the
correct answer is nothing. This is not a limitation of the assistant; it is the same limitation a
new employee has, and the remedy is the same: write it down.

**The instruction that asks it to guess.** *Create the customer from this email.* It can read the
email if you give it the email; it cannot read your inbox unless somebody has given it that tool,
and it will not invent an address to be helpful. If you want it to extract, say so: *read this
email and propose the customer record, but do not create it until I say so.*

## The verification habit

Every instruction that produces an action should be followed by a check, and the check should be
the assistant's own answer to a question about what it did.

> *Confirm the order.*
>
> *Which order did you confirm, and what is its total?*

The second instruction costs five seconds and closes the gap between what you meant and what
happened. In the months of testing, this habit caught every one of the mistakes that mattered, and
the mistakes it caught were almost always *definitions*, not arithmetic: the assistant had done
exactly what was asked, and what was asked was not what was meant.

## The instruction that asks for a judgement

There is a category of instruction that people write constantly and that almost never works, and it
is worth naming because it feels so reasonable: the instruction that asks the assistant to decide.

*Which customers should we chase?* *Which products should we discontinue?* *Is this supplier too
expensive?*

Each of those is a decision, and a decision needs three things the assistant does not have: what the
company values, what the alternatives are, and who bears the consequences. What the assistant has is
data, and the useful version of each question gives it the data and keeps the decision:

*List the customers with an overdue invoice and no order in ninety days, with the amount and the
last order date.* The decision—chase, wait, or write off—is then made by a person, in a minute,
with the facts in front of them.

The distinction is not pedantry. An assistant that answers a judgement question produces a
*plausible* answer, which is worse than no answer, because it invites somebody to act on it without
having thought. An assistant that produces the facts produces something a person can think with.

## Teaching a colleague

The document on Riverton's shared drive was four pages long because somebody wrote it down, and the
act of writing it down is worth a section of its own.

When a company adopts this technology, the knowledge of how to use it lives in one or two people,
and it is usually tacit: they know that *the blue binders* does not work and *A4 ring binders, blue
variant* does, and they could not tell you why. That knowledge is worth more than the software, and
it evaporates when the person leaves.

The remedy is the oldest one in the world: keep a list of the instructions that worked, in the
language of the office, with a line about what each one is for. Not a manual—a manual is written by
somebody who has stopped doing the work. A list is written by somebody who is doing it.

Riverton's list has three sections, and the third is the one that matters.

**Instructions that work**, grouped by department, one line each, with the output noted.

**Instructions that failed**, with what was wrong—because the failures are where the learning is,
and because a list of successes teaches nobody anything.

**Instructions we have not tried yet**, which is a wish list. *Can it tell me which customers are
profitable?* *Can it compare a supplier's invoice to the order without me asking?* *Can it prepare
the VAT return and reconcile it?* Some of those will work and some will not, and the list is how a
company discovers which.

## The anti-patterns, in a company rather than a prompt

Four habits appear in every company that adopts an assistant, and they are all reasonable and all
harmful.

**The hero.** One person becomes the person who knows how to ask, and everybody else asks them. The
company now has a bottleneck with a salary, and the knowledge is in one head—which is exactly the
condition the system was bought to cure.

**The sceptic.** One person decides the technology is a toy, and asks it questions designed to make
it fail, in public. They will succeed, because any system can be made to fail by a question that is
outside its data. The cost is not the failure; it is that the rest of the office learns to be afraid
of looking foolish.

**The over-trust.** One person decides the machine is always right, and stops checking. This lasts
until the first definitional error reaches a customer, and then the reaction is severe—usually a
return to paper for a month, which costs more than the error.

**The ghost.** The system is installed, praised at a meeting, and never used, because the person who
was supposed to use it was busy that week and the old way still worked. Six months later it is
discovered that the licence is being paid for a program nobody opens.

The antidote to all four is the same: a *named* person, a *protected* hour a week, and a
*demonstration* once a month in which somebody shows the office something the assistant did that was
useful. Not a training session; a demonstration. The difference is that a demonstration is about
work, and a training session is about software.

## The prompt journal

There is one more habit worth adopting, and it costs nothing.

Keep the instructions you typed. Not because you will need to repeat them—though you will—but
because the journal is the record of what the company asked for, and the record of what the machine
understood.

Odoo keeps the *result*: the invoice, the order, the payment. It does not keep the sentence that
produced it. The assistant keeps its own log, but a log is a technical artefact with timestamps and
tool calls; it is not the story of the day.

A journal is one line per instruction, in a text file, with the date. Six months later it answers
questions that nothing else can: *when did we start chasing at fifteen days?* *what did we ask it to
do in the week the Ashfield invoice went wrong?* *has anybody ever asked it to compare two months?*

It is the cheapest form of institutional memory there is, and the only one that a small company will
actually keep.

## Where the instructions live

The next chapter is the library: more than fifty instructions, grouped by department, each one
executed on a real installation during the writing of this book, with the result recorded.

They are not a script to be read out. They are a vocabulary. Read the ones for your department,
adapt the names to your company, and add the ones that are missing—because the library that matters
is the one your office writes for itself, in the language it actually speaks.

There is one more thing to say about prompts, and it is the thing that took Riverton longest to
learn.

The instruction is not a magic formula. It is a *delegation*, and it carries the same obligations as
delegating to a person: say what you want, say what you do not want, give the person the information
they need, and check the result. The companies that get value from this technology are not the ones
with the cleverest prompts. They are the ones that delegate well—which, as it happens, is also the
difference between a good manager and a bad one, and has been since long before there were machines
to delegate to.
