# 16. The Warehouse Answers

The question that changed Tom Beck's job was asked on a Tuesday, and it was not a question about
computers.

> *How many A4 ring binders do we have, and where are they?*

He had asked it a thousand times in nineteen years, and the answer had always come from a person:
from himself, or from whoever was on the pick line, or from a notebook that was sometimes right. Now
he typed it into a window and got this:

> *Ring binder A4: 412 on hand in total. 350 reserved for order S00012 (Ashfield Academy). 62
> available. Locations: Stock/Shelf A — 380, Stock/Returns — 24, Stock/Quarantine — 8.*

He read it three times. Then he walked out to Shelf A and counted, which took eleven minutes and
proved the system right on all three numbers.

"Right," he said, when he came back. "Now I believe it."

---

## What a stock move is

The number 412 is not stored anywhere. That is the first thing to understand, and it is the thing
that separates a real inventory system from a spreadsheet with a quantity column.

What is stored is a list of *moves*: two hundred received from the supplier in March, three hundred
and fifty picked for Ashfield in June, twenty returned in July, eight moved to quarantine in
August. The stock level is the sum of those moves, calculated when you ask. If you ask again in a
minute, and nothing has moved, you get the same answer. If something has moved, you get a different
one, and the difference is *the move itself*—which has a date, a user, a reason and a document.

This has three consequences that a spreadsheet cannot reproduce.

**You can always find out why.** When a number looks wrong, the moves explain it. Not "somebody
changed the quantity" but "twenty went to quarantine on 3 August because the pallet was crushed".

**Two people cannot silently disagree.** If Tom counts 380 and the system says 412, the difference
is a document: an adjustment, with a reason, approved by somebody. The count does not overwrite the
system; it produces a move that reconciles them.

**The history survives a change of unit, price or supplier.** The moves keep the quantities they
were made in. Reorganising the catalogue does not rewrite the past.

## Reserved, available, and the difference that matters

The second thing Tom learned is the difference between *on hand* and *available*, and it is the
difference between a warehouse that promises and a warehouse that keeps its promises.

**On hand** is what is physically in the building: 412 binders.

**Reserved** is what has been promised to a specific order: 350 binders, for Ashfield, waiting for
the van.

**Available** is on hand minus reserved: 62 binders that can be promised to somebody else.

A company that only tracks *on hand* will promise the same 350 binders twice—once to Ashfield and
once to Northgate—and discover the problem on the morning of the delivery, when there is only one
pallet. A company that tracks reservations discovers it at the moment of the second promise, when
the system says *62 available* and the salesperson has to make a decision.

That decision—do we deliver Northgate late, or do we buy more, or do we split the order—is a
commercial decision, and the point of the system is not to make it. The point is to put it in front
of a person *before* it becomes an apology.

## The delivery

The delivery itself is the simplest document in the whole system and the one with the most
consequences.

> *Deliver order S00012 and show me the stock moves it created.*

> *Delivery WH/OUT/00004 validated for order S00012. Moves: 350 × Ring binder A4 (blue) from
> Stock/Shelf A to Customers; 20 × Whiteboard markers (pack of 4) from Stock/Shelf A to Customers.
> Stock after the move: 62 binders on hand, 0 reserved; markers 44 on hand.*

Three things happened at once, and they are worth separating.

The **stock** moved: 350 binders left Shelf A. The **reservation** disappeared, because it had been
fulfilled. And the **order** changed state: it is now *delivered*, which means the invoice can be
created against it.

If the delivery had been partial—two hundred binders instead of three hundred and fifty—Odoo would
have created a *backorder*: a second delivery document for the remainder, linked to the first. That
single mechanism is the reason a company can promise *we'll send the rest on Friday* without anybody
having to remember what the rest was.

## The locations, in practice

A location sounds like a technicality until the first time something goes missing, and then it is
the only thing that matters.

Riverton's four locations—two shelves, returns, quarantine—were set up in an hour and used properly
for about a month before anybody appreciated them.

The returns location was the first to earn its keep. A customer sends back twenty binders because
they are the wrong colour; the van brings them to the loading bay; Tom has to decide whether they go
back on Shelf A (they are, after all, sellable) or into quarantine (they are not). On the old
system, the decision was made by where the box was put, and the box was put wherever there was
space. On the new system, the decision is a stock move, and the move has a reason attached.

The consequence appeared in the margin report three months later: the returns location held
forty-one items that had been "returned" and never checked, some of them damaged, some of them
actually a different product. Every one of them had been counted as sellable stock. That is forty-one
items of stock that the company believed it had and could not sell—a small number, and a perfect
illustration of the general principle: **the value of a location is that it forces a decision to be
recorded.**

## The three-way match, from the warehouse's side

Chapter seventeen describes the three-way match from the accountant's point of view. From Tom's
side, it looks different and it is worth a paragraph.

When a delivery arrives, the warehouse's job is to record what actually came: how many, of which
product, in what condition, on what date. That record is the *receipt*, and it is the middle leg of
the match. If it is wrong—if Tom records forty pallets instead of forty reams, or if he validates
the receipt before counting—then the match will "succeed" against a wrong number, and the error will
survive all the way into the accounts.

This is why the receipt is a document with a user and a timestamp, and why the assistant is not
allowed to validate a receipt on its own initiative. It can create one from a purchase order, which
is a proposal; validating it means *I have counted this*, and that is a claim about the physical
world that only somebody standing in front of the pallet can make.

Tom's rule, written on the whiteboard: *the system can guess what should be there. Only I can say
what is.*

## The cost of a wrong count

It is worth putting a number on the quarterly count, because "we should do it more often" is the
kind of advice that dies in a busy month.

Riverton's stock was worth about £180,000 at cost. The first count found a net difference of 1.8 per
cent—about £3,200—spread across eleven products. That is not theft; it is the accumulated effect of
forty small errors: a pallet booked in as forty pallets, a return put back without checking, a
delivery validated before it was counted.

A count costs two people a day, twice a year, which is about £1,200 of wages. It found £3,200 of
error the first time and £900 the second. The arithmetic is not subtle: a company that counts twice a
year is buying a £1,200 insurance policy against a £3,000 error, and the error it prevents is the one
that makes the accounts wrong at the year end.

What changed with the system was not the arithmetic but the *shape* of the count. Instead of
counting everything and reconciling a list, the system proposes what it believes and the counter
confirms or corrects. The corrections are then investigated, one at a time, and each investigation
fixes a habit rather than a number. That is the difference between counting stock and managing it.

## The delivery note, and the three signatures

A delivery in a wholesaler has three moments, and each one has a signature of a kind.

**The picking**: somebody takes the goods off the shelf and puts them on a pallet. The signature is
the picking list, initialled line by line, and it is the warehouse saying *this is what I put
together*.

**The loading**: the goods go on the van. The signature is the driver's, and it is the company
saying *this left the building*.

**The delivery**: the customer's caretaker signs the note. The signature is theirs, and it is the
customer saying *this arrived*.

In Odoo the three moments collapse into two documents—the delivery order and its validation—and
that is a simplification worth understanding, because it is where most discrepancies are born. A
pallet that is picked, loaded and never delivered has left the system's stock but not the company's
yard; a pallet that is delivered and never validated has left the yard but not the system.

Tom's habit, after the first year, was to treat the validation as the moment of truth: the delivery
is validated when the signed note comes back, not when the van leaves. It makes the stock report a
day late and it makes it right, and he would rather have a right number on Wednesday than a wrong
one on Tuesday.

## What the warehouse knows that the system does not

There is a limit to all of this, and Tom is the first to describe it.

The system knows quantities, locations and dates. It does not know that the corner of Shelf B is
where the damp gets in, that the pallet of paper from the August delivery is heavier than the
February one because the supplier changed the ream weight, or that the driver who delivers on
Fridays will not wait while you count.

A warehouse manager carries that knowledge, and the system's value is not that it replaces it but
that it *frees* it: a person who does not have to remember where four hundred and twelve binders
are can spend the attention on why the pallet from August feels wrong.

"It's the same as the office," Tom says. "The system does the counting. I do the noticing."

## The count

Once a quarter, Riverton counts.

It is not a pleasant afternoon. It involves a clipboard, two people, a torch, and a warehouse that
is colder than it looks. But it is different now, in a way that took Tom a while to articulate.

"The first time, I counted everything and typed it in, and the system told me where I was wrong,"
he said. "The second time, I only counted the things the system said I should have, and it told me
where *it* was wrong. That's a different job. The first one is a chore. The second one is a
conversation."

What he meant is this: with a stock count, the system proposes a list of products and the quantities
it believes are on the shelf, and the counter confirms or corrects. The corrections are then
reviewed, and each one is a small investigation: was it a picking error, a delivery signed for but
not recorded, a return that never came back to the shelf?

That investigation is where the money is. In Riverton's first year, the quarterly count found three
recurring problems, and none of them was theft:

- A product whose unit of measure had been set up wrong in 2022, so that every receipt was recorded
  as one pallet instead of forty reams. The system had been "losing" paper for three years.
- A delivery note that was signed at the school but never validated in the system, so the goods were
  on the shelf and also in the customer's cupboard.
- A returns process that put returned goods back into stock without checking them, so damaged items
  were sold twice.

Each of those was found by comparing what the system believed with what was true, and each was fixed
by changing a habit, not by buying something.

---

## A note on the word "warehouse"

Tom's warehouse is a room with shelves, a loading bay, and a corner where the damaged things go. In
Odoo it is a *location*, and locations can be nested: a warehouse contains a stock area, which
contains shelves, which contain bins.

A company with one room does not need the nesting, and Riverton did not use it at first. But the
structure was there, and in the second year, when the company rented the unit next door, adding a
second warehouse was a matter of creating a location and moving stock—not of buying a second system
or starting a second spreadsheet.

That is the quiet advantage of modelling reality instead of recording it. A spreadsheet that says
"412 binders" cannot grow a second shelf without being rebuilt. A system that says "412 binders,
here are the moves that put them there" can grow a second building in an afternoon.

---

Tom's report, at the end of that first quarter, was four pages long and he read it in the van.

"The thing I keep coming back to," he said, when he brought it back, "is that I used to *know*
things and I couldn't *show* them. Now I can show them. It's the showing that changes the
conversation."

Maggie asked him what he meant.

"Before, if I said we had too much paper, it was Tom's opinion. Now it's a number on a page with a
date on it. Nobody argues with a number on a page. They argue with Tom."

He grinned. "It's very restful."
