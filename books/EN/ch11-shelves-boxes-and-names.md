# 11. Shelves, Boxes, and Names

Tom Beck had worked in Riverton's warehouse for nineteen years, and he had one rule about
computers, which he announced on the morning of the fourth day, standing in the doorway of the
small room with his arms folded.

"I'm not typing in eleven thousand products."

"Nobody's asking you to," Maggie said. "We're going to type in forty."

Tom unfolded his arms, which was as close to enthusiasm as he came before lunch.

---

## Why forty and not eleven thousand

A wholesaler's catalogue is not the same thing as its *range*. Riverton listed eleven thousand
references because over thirty years it had bought whatever customers asked for, and the list had
grown the way a hedge grows. Of those eleven thousand, four hundred had sold more than ten units in
the last year. Four hundred is still too many to type in a week, and most of them share a shape:
a brand, a size, a colour, a pack quantity.

So the plan was not to copy the catalogue. The plan was to model the *families* properly and let
the variants do the work.

The whiteboard in the warehouse office ended up with four lines on it:

| Family | Variants | Unit of sale | Unit of purchase |
|---|---|---|---|
| Ring binders | 2 sizes × 3 colours | each | box of 20 |
| Whiteboard markers | 4 colours | pack of 4 | box of 12 packs |
| A4 paper | 1 | ream | pallet of 40 reams |
| Ballpoint pens | 2 colours | box of 50 | box of 50 |

Four families, and between them a few dozen variants. That is what a modern ERP calls a product
list: not a list of everything you have ever bought, but a model of the things you sell, with the
differences expressed as variants rather than as separate entries.

The difference is not cosmetic. If "Ring binder A4 blue" and "Ring binder A4 red" are two
products, then the system cannot answer "how many A4 binders did we sell?" without somebody
knowing that the two are related. If they are one product with a colour variant, the question is
trivial—and the question is the whole point.

## Categories, and why a report needs them

A product category is a folder, and folders are boring until somebody asks a question.

In Odoo a category does three things: it groups products for reporting, it can carry default
accounts (so that every product in the category posts its sales to the same income account), and it
can carry a default unit of measure and cost method.

Riverton's categories ended up being six: *Paper*, *Binders and filing*, *Writing instruments*,
*Ink and toner*, *Furniture*, and *Services*. Six is enough to answer the question *which part of the
business made money this month?* and few enough that nobody argues about where a product belongs.

The alternative—one category called *All products*—is what a company gets if it does not decide, and
it means that every margin report is a report about the company as a whole. That is a fine report
and it is not the one a wholesaler needs, because a wholesaler's profit is made and lost in the mix
between categories, not in the total.

There is a second reason to care, and it is accounting. If the category carries the income account,
then a new product is posted correctly by default, and the person creating it does not have to know
anything about the chart of accounts. If it does not, every new product is a small accounting
decision made by somebody who is thinking about stationery.

## Units of measure, and the arithmetic of the warehouse

The second thing to get right is the unit.

Riverton buys ring binders in boxes of twenty and sells them singly. If the system does not know
that a box is twenty, then every receipt, every count and every delivery is an argument, and
somebody will eventually convert in their head at the wrong moment.

Odoo handles this with two units per product: the unit of measure used to buy and stock (the box),
and the unit of sale (the each), with a conversion factor. The warehouse counts boxes; the customer
orders eaches; the invoice is in eaches; the stock is in boxes. One number, three views.

There is a trap here that has cost companies more money than any other single setting: **the unit
of measure on an existing product cannot be changed after it has moved.** Once a hundred receipts
have been recorded in "each," telling the system that the product is actually bought in "boxes of
twenty" does not convert the history; it corrupts it. The time to get this right is before the
first receipt, which is why Tom spent an hour on it and why the hour was worth more than the two
days he would have spent later reconciling a stock count.

## The warehouse itself

An ERP does not have "the warehouse." It has *locations*, and a location is any place where stock
can be.

Odoo installs two by default: a virtual location called *Partners* (where goods come from and go
to, because a supplier is not a shelf) and *Stock*, the physical warehouse. From there a company
adds what it actually has: *Stock/Shelf A*, *Stock/Shelf B*, *Stock/Returns*, *Stock/Damaged*.

![The warehouse locations: a place for everything, including the places goods are not](../../assets/screens/odoo-06-locations.png)

Riverton added four: two shelves, a returns area and a quarantine area for damaged goods. The last
one matters more than it sounds. Without it, damaged stock sits in the main location and is counted
as sellable, and the company discovers the problem when a customer opens a box of crushed binders.
With it, the damage is a *move*—a document, with a date and a reason—and the stock report tells the
truth.

## The first products

The products were entered in an afternoon, by Priya and Tom together, which is the only way it
works: the salesperson knows what the customer calls it, the warehouse knows what the supplier calls
it, and the product record needs both.

Six fields on that form decide almost everything that happens later.

**Product type.** *Goods* for things you can put on a shelf; *Service* for things you cannot. A
service has no stock and no delivery; a good has both. Getting this wrong makes a product
permanently undeliverable or permanently uncountable.

**Sales price and purchase price.** The defaults. The real price for a given customer may be
different—that is what pricelists are for—but the default is what the salesperson sees when they
are in a hurry.

**Tax.** The rate that applies to this product. As chapter ten said: configured here, once, and
inherited by every document.

**Unit of measure.** As above.

**Internal reference.** The code the warehouse uses. It is the field that makes the difference
between a system that humans can use and one they cannot, because it is what people say out loud
when they are standing in front of a shelf.

**Barcode.** Optional, and transformative if you have a scanner: a delivery can be checked by
beeping each box rather than by reading a list.

## The first stock

A system that believes the warehouse is empty will refuse to deliver anything, which is correct and
inconvenient. So the first stock has to be entered, and there are two honest ways to do it.

The first is an *initial inventory*: you tell the system how many of each product you have, on a
given date, and it creates the corresponding stock. That is what Riverton did, over two evenings,
with a clipboard and a torch.

The second is a *stock count*: the system asks you to count, and you enter what you find, and it
records the difference between what it believed and what is true. That is what Riverton does every
quarter now, and it is a different operation with a different purpose.

Both are documents. Neither is a number typed into a field. This is the discipline that makes the
whole thing work: **stock is never a number you set; it is the sum of the moves you have recorded.**
If that sounds pedantic, consider what happens when a number can be set: somebody sets it, somebody
else sets it back, and the warehouse and the accounts disagree forever.

## The things that are not things

There is a category of product that causes more confusion than any other, and it is worth a page of
its own: the products that are not physical.

Riverton has three of them, and every wholesaler has the same three.

**Carriage.** The charge the customer pays for delivery. It has no stock, it is never received, and
it must be invoiced. In Odoo it is a product of type *Service*, with a tax rate and a price, and the
only thing that distinguishes it from a box of pens is that it never appears in a delivery.

**The discount.** Not a product at all, in most systems: a negative line on the order, or a
pricelist rule. But a company that issues credit notes for volume rebates needs a product to put on
the credit note, and it is usually called something like *Volume rebate* and typed as a service.

**The sample.** A product given away. It has stock, it leaves the warehouse, and it must not be
invoiced. If it is modelled as a normal product with a zero price, the margin reports will show a
hundred per cent loss on a hundred units; if it is modelled as a service, the stock will never
leave. The clean way is a *delivery* of the product with no order behind it, with a reason, which is
also the only way the cost ends up in the right place.

None of these is difficult. All of them are invisible on the first day and produce strange numbers
on the thirtieth, which is why the person configuring the system should sit with the person who
invoices and ask a simple question: *what do we put on an invoice that is not on a shelf?*

## The four hundred products nobody buys

Every wholesaler has them: the catalogue of things that were bought once for a customer who asked,
and then never again. Riverton's eleven thousand references contained, by Tom's estimate, about
four hundred of those.

The temptation is to clean them up in the first week, and it is the wrong first move for two
reasons. The cleanup takes weeks, and it teaches the office that the new system is a chore before
it has taught them that the new system is useful.

The right move is to bring in the four hundred lines that matter—the ones with activity in the last
year—and to leave the rest in the old system, archived, for as long as the law requires. A product
that has not moved since 2019 does not need a record in the new system on day one; it needs a
decision, and the decision can wait until somebody has time.

There is a second benefit to waiting. After three months of the new system, the report *products
with no movement in the last year* is a list of exactly the candidates for retirement, produced in
a second, with the stock value attached. The cleanup becomes a decision with numbers, rather than a
week of typing.

## The reordering rule

The last thing Tom set up was the reordering rule, and it is the first place where the system starts
to be useful rather than merely accurate.

For each product he set two numbers: a *minimum* (below this, we are at risk) and a *maximum* (order
up to this). Odoo watches the stock, and when a product falls below the minimum it proposes a
purchase order for the difference. It does not send it. It proposes it, in a list, and a person
decides.

That distinction—propose, do not act—is the same distinction that will matter enormously when the
assistant arrives in Part III. A machine that proposes is a colleague. A machine that acts without
asking is a risk with a plug.

---

On the Friday of that week, Tom did something he had not done in nineteen years: he printed a stock
report and read it in the van, on the way to a delivery.

"Four hundred and twelve lines," he said, when he came back. "I know all of them. But I've never
seen them on one page before. I've seen them in my head, one at a time, when somebody asked."

He put the report on Maggie's desk.

"Look at the paper," he said. "We've got eleven hundred reams and we sell about ninety a week. That's
three months of paper. It's not wrong, exactly, but it's a lot of money sitting on a shelf."

It was, and it was the first time anybody at Riverton had been able to say so with a number
attached. The stock had always been there; the *fact* about the stock had been in Tom's head, and
Tom's head had been in a van.

That is what a warehouse becomes when it is modelled properly: not a place where things are, but a
place where things are *known*. And the knowledge, once it exists, immediately starts asking
questions that nobody had thought to ask—about paper, about cash, about the eleven hundred reams
that could have been four hundred.

Maggie wrote the number on the back of the stock report and put it in the drawer with the napkin
and the card from Gerald. The drawer was getting full. That, she decided, was a good sign.
