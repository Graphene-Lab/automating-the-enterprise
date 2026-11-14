# 22. Work That Runs While You Sleep

The first scheduled job Riverton set up was not clever. It was the Monday list.

Every Monday at eight, the assistant produces a page: invoices that became overdue in the previous
week, products that fell below their reordering point, orders due for delivery in the next seven
days, and any stock adjustment with no reason recorded. It sends it to Maggie, Priya and Tom as an
email, and it takes the assistant about forty seconds.

Nobody asked for it. It was Sam's idea, and he explained it with a sentence that has stayed with
Maggie ever since.

"The point of a schedule is not that the machine works while you sleep. It is that the *question*
gets asked whether or not anybody remembers to ask it."

---

## Two kinds of scheduled work

There are two mechanisms in this stack, and they are worth telling apart because they answer
different questions.

**The ERP's own schedulers** run inside Odoo. They are the things a business system has always done
on a timer: recalculate reordering points, send the reminder emails, run the depreciation, clean up
old sessions. They are configured in the ERP, they run whether or not the assistant is open, and
they are the right place for anything that is part of the *model*—anything that would have to happen
even if nobody in the company was interested.

**The assistant's task scheduler** runs jobs as conversations. A scheduled task is, literally, a
prompt with a date attached: at eight o'clock on Monday, the assistant is given an instruction, it
does the work, and it reports. That is the right place for anything that requires judgement about
*what to look at*—a summary, a sweep, a comparison, a nudge.

Riverton uses both, and the division between them is the useful part of this chapter.

## What belongs in a schedule

The temptation, when you discover scheduled work, is to schedule everything. Resist it, and use a
test that is easy to apply: **a job belongs in a schedule if its absence would be noticed only when
it is too late.**

The Monday list passes the test. Without it, an overdue invoice is noticed when somebody thinks to
look—which is to say, when it is sixty days old.

A nightly backup passes the test, catastrophically.

A daily "sales report" usually fails it. Nobody reads it; the number is in the dashboard; and a
report that nobody reads is a small daily tax on attention that eventually teaches people to ignore
messages from the system.

The test has a corollary: **a scheduled job should produce a decision, not a document.** The Monday
list produces four decisions (chase this, reorder that, deliver this, explain that). A report
produces a document, and documents accumulate.

## The three jobs Riverton kept

After a month of experimenting, the company settled on three, and it has kept them since.

**The Monday list**, at eight. Four questions, one page, three recipients.

**The Friday stock check**, at four. The assistant lists every product that fell below its
reordering point during the week and proposes purchase orders—in draft, never confirmed. Tom reads
it on Friday afternoon and decides; the orders are placed on Monday morning, which is when suppliers
answer the telephone.

**The first-of-the-month summary**, at seven. Sales by customer, sales by product, the top five and
the bottom five by margin, cash in and out, and the three customers whose payment behaviour has
changed. It is two pages, and it is the document Maggie reads with her first coffee of the month.

Everything else that was tried in that month was deleted, and the deletions are as instructive as
the keepers: a daily summary (nobody read it), an hourly connection check (it produced noise, not
information), and a nightly "clean up duplicates" job that was a genuinely bad idea—a machine
deciding which of two customer records is real, at three in the morning, with nobody watching.

## What happens when a job fails

The interesting part of scheduled work is not the schedule. It is the failure.

A job can fail for three reasons, and each has a different signature.

**The machine was off.** The ERP was not running at eight o'clock, so the job did not run. Odoo's
own schedulers handle this by running missed jobs when the server starts; the assistant's scheduled
tasks are stored as plans and run on the next start, with the date they were meant to run. Either
way, the work happens, late.

**The job ran and the answer was wrong.** This is the dangerous one, because nothing looks broken.
The Monday list arrives, and one of its four sections is empty because a filter was left on. The
defence is the same as everywhere else in this book: the list says *what it looked at*, not only
what it found. An empty section that says "no invoices became overdue in the week to 14 November"
is information; an empty section with no explanation is a question.

**The job ran and nobody read it.** This is the most common failure and the least discussed. A
scheduled job that arrives in an inbox nobody opens is worse than no job at all, because it creates
the *impression* of control. Riverton's answer was to make the Monday list a meeting—fifteen
minutes, three people, the list on the screen—which sounds like bureaucracy and is in fact the
cheapest possible way to make the automation real.

## A short history of the batch job

Scheduled work is older than the personal computer, and its vocabulary comes from the mainframe.

In the 1960s, a computer was too expensive to let a person sit at it, so work was prepared on cards
and run in *batches* overnight: payroll on the 25th, invoices on the 1st, the general ledger at
month-end. The batch was a queue, and the operator's job was to keep the queue moving. When
minicomputers arrived in the 1970s, the batch survived as `cron`—a Unix program, written in 1975 by
Ken Thompson, whose name comes from *chronos*, time—and `cron` is still what runs the world's
servers, including, indirectly, the scheduler inside your ERP.

What is new is not the timer. It is *what* runs on it. A 1975 batch job was a program written by a
programmer to do exactly one thing. A 2026 scheduled task is a sentence in English, and the machine
works out the steps each time it runs. That is a different kind of automation, and it needs a
different kind of supervision: the program did what it was written to do, every time; the sentence
may be interpreted differently as the data changes.

Which is why the first rule of scheduled work in this book is: **schedule questions, not actions.**
The Monday list asks. The Friday stock check proposes. The first-of-the-month summary reports. None
of them posts an invoice, sends a letter to a customer, or places an order, because those are
decisions with consequences, and a decision made at three in the morning by a machine nobody is
watching is not a decision—it is a bet.

## The one exception

There is one scheduled job at Riverton that does act, and it is worth describing because it shows
where the line is.

Every night at two, the system takes a backup: a dump of the database, a copy of the configuration,
and a line in a log. It acts. It changes the world, in the sense that files appear. And it is
allowed to act because the action is *reversible by design*: a backup that is wrong can be deleted
and taken again, and nothing in the business depends on it having happened, until the day something
does.

That is the test for any scheduled action: if this runs wrongly at three in the morning, can I undo
it before anybody notices? If yes, it can be scheduled. If no, it can propose, and a person can
decide.

## The cost of a schedule nobody owns

A scheduled job is a small promise, and promises need an owner.

The failure is quiet and it is common: a job is set up by somebody who then leaves, or changes role,
or simply forgets. It keeps running. Six months later it is producing a report with a filter that
was right in March, or proposing orders for a product line the company discontinued, and nobody
notices because nobody reads it—until somebody does, and trusts it.

The remedy is a list, kept in the same file as the prompts: every scheduled job, what it does, who
reads it, and when it was last reviewed. Four columns, one page, reviewed twice a year. A job that
nobody can name an owner for is a job to delete.

Riverton's list has three entries and a fourth that is a reminder to review the list. It is the least
impressive document in the company and it has prevented two bad decisions, both of which would have
been made by a machine doing exactly what it was told.

## Where the schedule lives, and what happens when the machine is off

A scheduled task is a file, and knowing where it lives is the difference between a schedule you own
and a schedule you are at the mercy of.

The assistant stores its plans as JSON, in its own data folder, and they survive a restart. Each
plan is a sentence, a time, a recurrence, and a list of what to do with the result. That is worth
knowing for two reasons: it can be backed up with the rest of the configuration, and it can be
inspected—which means a company can answer the question *what is this machine doing at eight o'clock
on a Monday?* by reading a file rather than by remembering.

The ERP's own schedulers live in the database, in a table of scheduled actions, and they are visible
in the interface under *Settings → Technical → Scheduled Actions*. Each has a name, an interval, and
a count of how many times it has run. That count is a small but excellent diagnostic: a job that has
run four hundred times and a job that has run zero times tell you different things, and both are
worth looking at once a quarter.

When the machine is off, three things can happen, and the ERP's behaviour is the sensible one.

**Odoo's schedulers** run missed jobs on the next start, in order, and they record the fact. A
reminder that was due at eight will go out at nine, and the log will say so.

**The assistant's tasks** are checked on start: if a plan's next run is in the past, it runs at once
and reschedules itself. A Monday list that was missed because the machine was off will arrive on
Tuesday, with the data as it is on Tuesday—which is a subtle and important difference. The list is
not "what happened on Monday"; it is "what is true now, asked on the schedule that was meant for
Monday".

**A backup** that was missed is simply missed, and the next one covers the gap. That is acceptable
for a nightly backup; it is not acceptable for a weekly one on a machine that is often off, which is
why the backup script writes a line in a log and the log is checked monthly.

## When a job produces noise

The failure mode that kills scheduled work is not a crash. It is noise.

A job that produces a message nobody reads trains people to ignore messages from the system, and
then the one that matters is ignored too. Riverton tried four schedules in the first month and
deleted three, and the deletions were as instructive as the keepers.

**The daily summary** was deleted because it duplicated the dashboard and arrived at a time when
nobody was at a desk. The information was not wrong; the delivery was.

**The hourly connection check** was deleted because it reported success every hour. A message that
says *everything is fine* is not information; it is a habit, and habits are what make people stop
reading.

**The nightly duplicate check** was deleted because it was an action nobody had authorised, running
at a time nobody was watching, on data nobody had cleaned. It found nothing for three weeks and then
proposed merging two customers who were, in fact, two branches of the same organisation.

The three that survived all share a property: they produce a *decision* that a named person makes at
a named time. The Monday list is read at the Monday meeting. The Friday stock check is read by Tom
before he leaves. The monthly summary is read with the first coffee of the month.

A schedule without a reader is a cron job with a hobby.

---

The Monday list has been running for eight months, and Maggie has missed it twice—both times
because she was travelling, and both times she read it on the Tuesday and wished she had read it on
the Monday.

"It's not the information," she says. "I could get the information. It's that on Monday morning,
before anything else happens, somebody puts four questions in front of me. And they're the right
four questions. I'd never think to ask them at eight o'clock on a Monday. I'd think about them at
four o'clock on a Friday, when it's too late to do anything."

That is the real value of scheduled work, and it has nothing to do with machines working while you
sleep. It is that the *question* has a time, and the time is chosen by somebody who thought about it
once, carefully, instead of by whoever happens to be worried at the moment.
