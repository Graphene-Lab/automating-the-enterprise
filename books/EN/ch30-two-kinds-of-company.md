# 30. Two Kinds of Company

There are two kinds of company, and the difference between them has nothing to do with size,
sector or technology.

The first kind *hopes*. It hopes that the invoice went out. It hopes that the stock count is
roughly right. It hopes that the customer paid, and that the payment was matched to the right
invoice, and that nobody has been quietly over-ordering since the spring. When it needs to know
something, it asks a person, and the person looks, and the answer is as good as that person's
memory on that day. This is not incompetence. It is the normal condition of a business that has
grown faster than its systems, which is to say: almost every business that has ever succeeded.

The second kind *remembers*. Not because it is cleverer, but because it has arranged its affairs
so that the facts are written down in one place, at the moment they happen, by the person who
caused them—and so that anybody with the right permission can ask a question in plain English and
get the answer in a second.

Maggie Ellery spent a year moving Riverton from the first kind to the second, and the most
surprising thing about the move was how little of it was about software.

## The three things that make the move possible

If the difference between the two kinds of company is not size, sector or technology, what is it?

Three things, and Riverton had all three by accident, which is why the book can describe them with
some confidence.

**A person who is allowed to change how the office works.** Not the owner, necessarily—Doreen
changed more habits than Maggie did—but somebody who has the authority to say *we are going to do
this differently from Monday*, and whose judgement is trusted when the first week is messy.

**A willingness to write things down.** The whole system is a model, and a model is only as good as
the facts put into it. A company that treats data entry as a chore will have a system that is
technically installed and practically useless.

**A tolerance for being wrong in public.** The first month is full of small mistakes: a product with
the wrong unit, an invoice posted twice, a report that was nonsense because a filter was left on.
A company where a mistake is a scandal will hide the mistakes, and the system will learn nothing.

None of those is a technology decision. All three are cultural, and the technology is downstream of
them.

## What a company should do on Monday

The book has described a year, and a reader who has come this far is entitled to a shorter answer.

**Week one.** Install the stack on a machine that is not doing anything else. Do not touch the
company's real data. Create a customer, a product, a quotation, an invoice, and post it. Look at the
ledger. Break something and fix it.

**Week two.** Configure the company properly: the country, the currency, the chart of accounts, the
taxes, the users. Take the seven checks of chapter twenty-one and see which ones the system can
already answer.

**Week three.** Put the assistant in front of one real question that the company cannot answer
today—the one you wrote down at the start of this chapter. Do not automate anything yet. Just ask.

**Week four.** Pick one process—the invoice run, the overdue list, the stock reorder—and move it
entirely into the new system. Not partially. The old route must close, or the new one will not open.

**Month two.** Add the second process. Start the Monday list. Give somebody the hour in the diary.

**Month three.** Look at what has changed, and decide what to do next. By then the answer will be
obvious, and it will not be the answer you expected in week one.

That is the whole method, and it fits on an index card. The rest of this book is the argument for
why each line of it is there.

## The thing that does not scale, and the thing that does

There is a final observation, and it is about size.

Everything in this book scales down: a company with two people can run the same stack, and the
installation takes the same afternoon. What does not scale down is the *discipline*—the hour a week,
the checking, the writing down. In a company of two, that hour is a larger fraction of the whole
week, and it is the first thing to be sacrificed when a customer telephones.

What scales up is the *questions*. A company of two hundred can ask the same questions as a company
of two, and get the answers in the same second, and the answers are worth more because there is more
money behind them. That asymmetry is why this technology will change medium-sized companies more
than small ones: the small ones already know everything, and the large ones already have systems.
The ones in the middle—too big to hold in a head, too small for a project—are the ones this book is
for.

## What to tell a sceptical colleague

Every company has one, and the argument is worth having properly, because the sceptic is usually
right about something.

The sceptic says: *we tried software before and it did not work.* They are right. Most business
software fails, and it fails for reasons that have nothing to do with the software: nobody owned it,
nobody maintained the data, the old route stayed open, and the first month was judged as if it were
the hundredth.

The sceptic says: *the machine will make things up.* They are right. It will, unless it is grounded
in the company's own data through tools, and unless somebody checks what matters.

The sceptic says: *this will take time we do not have.* They are right. It takes two months of
somebody's attention before it pays back, and a company that cannot afford two months should wait
until it can.

What the sceptic is usually wrong about is the conclusion. The evidence is not that the technology
works; it is that the *combination*—a model of the company, a strict set of rules, an assistant that
reads and writes through those rules, and a person who checks—works, and works at a scale a small
company can afford.

The way to win the argument is not to win it. It is to install the system on a spare machine, give
the sceptic one question they cannot answer today, and let them ask it. The answer will take a
second, and the sceptic will spend the next week trying to find the flaw in it—which is exactly the
behaviour you want from the person who will eventually be responsible for the data.

---

On the last Friday before Christmas, the company held its usual lunch in the back office, with the
tables pushed together and the good plates brought up from the kitchen. Twenty-two people, which
was four more than the year before.

Tom made a short speech, because Tom always made a short speech, and it was about the stock take.

"We did it in a day this year," he said. "Last year it took three, and we still found eleven
things that didn't match. This year we found two, and both of them were my fault, and I know
exactly which ones because the system told me the day I made them."

He raised his glass. "I'd like to thank the machine. I never thought I'd say that."

Everybody laughed, and then Priya said, "You'll be thanking the printer next," and the moment
passed into the general noise of a Christmas lunch, which is where most true things go to be
comfortable.

But Maggie had heard it, and she thought about it on the drive home.

What Tom had said, stripped of the joke, was that the company had moved from *discovering* its
errors once a year to *knowing* them once a day. That is the whole of the change. Everything
else—the installation, the screenshots, the assistant, the prompts—is machinery in service of that
one sentence.

---

It is worth being clear about what the second kind of company is not.

It is not a company without people. Riverton employed more people at the end of that year than at
the beginning, and the four new ones were not doing the work the assistant had taken over.

It is not a company without error. The Friday mistake in the previous chapter was real, and there
were others. The difference is that the errors were *visible*—in a log, in a list, in a
reconciliation—rather than buried in a filing cabinet until the year end.

It is not a company without paper. There is still paper at Riverton: delivery notes that travel
with the vans, invoices that a few customers insist on receiving by post, the certificates that
hang in the corridor. The paperless office, as predicted in 1975, has not arrived and probably
never will. What arrived instead is something less dramatic and more useful: paper stopped being
the *memory* of the company and became one of its outputs.

And it is not a company that runs itself. The subtitle of this book is a joke with a serious
point. Nothing runs itself. What happens is that the running becomes cheap enough that a person
can spend their attention on the parts that need judgement, and the machine spends its attention
on the parts that need patience.

---

There is a question that Maggie was asked at every event she attended that year, in one form or
another, and it deserves a straight answer in this last chapter.

*Where do I start?*

Not with the software. Start with the question you cannot answer.

Every company has one. Which customers are overdue? How much stock do we actually have? What did
we sell last month, by product, by customer, by salesperson? Which of our prices have not changed
since 2022? Which supplier is late most often? Ask the question out loud in a meeting and watch
what happens: somebody says "I'll find out," and the meeting moves on, and the answer arrives three
days later in a spreadsheet that nobody trusts.

That question is your starting point, because it is the place where the company is currently
paying the tax of hoping. Write it down. Then ask a second question: what would have to be true,
in one place, for that answer to be available in a second? The answer to the second question is
almost always: a system that knows about parties, products, documents and money—which is to say,
an ERP—and a way to ask it questions without learning to program, which is to say, an assistant.

Then install it. It takes an afternoon. That is not an exaggeration for effect; it is the actual
finding of this book, and it is the reason the installation chapter is so long and the philosophy
chapters are so short. The hard part of this technology, in 2026, is no longer the technology. It
is the decision to write things down.

---

On the wall of the invoice room, next to the napkin and the delivery schedule from 2019 that
nobody had taken down, there is now a photograph.

It is the same photograph that was there before—four women at four desks in 1978, Maggie's mother
second from the left—but it has been reframed, and underneath it, in Maggie's handwriting, is a
caption.

*They typed it three times so that we would only have to type it once.*

Doreen objected to the caption on the grounds that it was sentimental, and Maggie agreed, and left
it up.

The invoice room itself has changed. The three grey cabinets are still there—Maggie could not bring
herself to throw them out, and there is a legal requirement to keep some of the paper for a few
years yet—but the Current Year cabinet closes now, because there is nothing in it that is not also
in the system. The trays are gone. Even the Trevor tray, which survived six years after Trevor,
has been replaced by a plant.

The room is where Doreen works, and where the assistant's log is read every Friday, and where
Priya comes when she wants to argue about a price.

It is, in the way of small companies, still the room where the paper lives. But the paper is no
longer the point.

---

The last scene of this book is not in the office. It is in a car park, at a roundabout by a retail
park, on a Monday in November a year after the beginning.

Maggie is sitting in her car with the engine off, watching the traffic, and she is not angry. She
has just come from Ashfield Academy, where Carol showed her the new invoice—emailed on Thursday,
paid on Friday, matched automatically, no telephone call, no forty-minute drive, no invoice in a
tray with a name that belongs to somebody who left six years ago.

Carol had said, "That was quick."

And Maggie had said, "Yes," and had not explained, because there was nothing to explain. The
company had done what it said it would do, on time, and the machinery behind it had been invisible,
which is the highest compliment that can be paid to machinery.

She starts the car. On the passenger seat there is a folder, and in the folder there is a napkin
with three boxes on it and a word in the corner, and a card with some numbers on it, and a
photograph of four women at four desks in 1978.

She is going back to the office, where there is work to do: a supplier whose prices have crept up,
a customer who has gone quiet, a stock adjustment that needs a reason, and a young man starting on
Monday who will ask, on his first afternoon, how many binders are in the warehouse—and will get an
answer in a second, and will never know how much that answer used to cost.

That is the ending. Not a revolution. A Tuesday.
