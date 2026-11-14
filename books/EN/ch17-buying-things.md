# 17. Buying Things

Buying is the half of a business that nobody writes books about.

Selling has a romance to it: customers, quotations, the thrill of the order. Buying has a purchase
order, a delivery note, an invoice from a supplier, and a payment run. And yet every pound a
wholesaler spends arrives through that door, and the difference between a company that buys well and
one that buys badly is the difference between a margin and a habit.

Riverton's buying was done by Maggie, on the telephone, from memory, for eleven years. She knew the
paper supplier, the pen supplier and the binder supplier, and she knew what she had paid last time
because she had a folder. What she did not have was any way of knowing whether the price had crept
up, or whether the last delivery had actually arrived, or whether the invoice she was about to pay
matched the order she had placed.

The assistant's first purchasing job was a reordering rule that fired on a Wednesday.

---

## The reordering rule, and what it proposes

Chapter eleven set two numbers on every product: a minimum and a maximum. Odoo watches the stock,
and when a product falls below its minimum, it proposes a purchase order.

It proposed one for ring binders, on the Wednesday, in a list that Tom looked at with his coffee.

> *Three products are below their reordering point: Ring binder A4 (blue) 62 available, minimum 100;
> Whiteboard markers (assorted) 44 available, minimum 60; A4 paper 9 reams available, minimum 40.*

Tom looked at the list, decided that the paper could wait until the pallet price was confirmed, and
asked for the other two.

> *Create a purchase order for 500 A4 ring binders, blue, and 200 packs of whiteboard markers,
> assorted, from our usual suppliers, at the last price we paid. Do not confirm it yet.*

> *Purchase order P00008 created, in draft. Two vendors, because the products come from different
> suppliers: 500 × Ring binder A4 (blue) from Pennine Paper at £2.10; 200 × Whiteboard markers
> (pack of 4, assorted) from Kestrel Supplies at £6.80. Total net £2,410.00, VAT £482.00, total
> £2,892.00. Nothing has been sent; say "confirm" to place the orders.*

Two things in that answer are worth noticing, and both of them are the system doing something a
person would have had to do by hand.

The first is *two vendors*. Tom asked for two products; the system knew they come from different
suppliers and produced two purchase orders. A person would have done the same, after looking at the
product records. The difference is that the person might have forgotten, and ordered binders from
the marker supplier.

The second is *the last price we paid*. That is not a price list; it is a fact from the history. The
system looked at the most recent purchase of that product and used the price. If the supplier has
raised his prices, the order will be wrong—but it will be wrong in a way that can be seen, because
the previous price is on the record next to the new one.

## What confirming does

Confirming a purchase order does three things, and the third is the one that matters.

It **commits** the company to buy, at a price, by a date—which is a promise, and therefore a
document that should be looked at before it is made.

It **creates an expected receipt**: the warehouse now knows that five hundred binders are coming,
and when. That is what makes it possible to answer the question *can we promise this to a customer
next week?* with something better than a guess.

And it **opens a door for the invoice**: when the supplier's bill arrives, it can be matched against
the order. Not because the system is suspicious, but because the *three-way match* is the oldest
control in commerce and still the best one.

## The three-way match

The idea is simple enough to fit on a napkin, and it has saved companies more money than any
software feature ever invented.

You ordered five hundred binders at £2.10 each. The warehouse received five hundred binders. The
supplier's invoice says five hundred binders at £2.10 each. Three documents, three numbers, and they
must agree before the bill is paid.

If the invoice says £2.30, somebody asks why. If the warehouse received four hundred and eighty,
somebody asks where twenty went. If the order was for five hundred and the invoice is for six
hundred, somebody asks who authorised the extra hundred—and the answer is often *nobody*, which is
exactly the point.

The control is old. Cost accounting textbooks described it in the 1920s, and it was formalised in
the purchasing manuals of the 1950s, when large manufacturers discovered that the difference between
what they ordered and what they paid was a significant fraction of their profit. It survives because
it is cheap: three documents that already exist, compared by a machine that does not get bored.

What is new is that the comparison takes a second and can be *explained*.

> *Create the supplier bill for purchase order P00008 and check it against the order and the
> receipt.*

> *Vendor bill BILL/2026/0031 created from P00008 for Pennine Paper: 500 × Ring binder A4 (blue) at
> £2.10, net £1,050.00, VAT £210.00, total £1,260.00. Matched: ordered 500, received 500, billed
> 500. No difference. The bill is in draft.*

No difference. On a good day, that is the whole of the work: three numbers that agree, in a
sentence, in a second.

On a bad day it says something like: *ordered 500, received 480, billed 500 — a difference of 20
units at £2.10.* And then a person has to decide: did the supplier short-ship, did the warehouse
miscount, or did somebody accept a partial delivery and forget to record it? The system cannot
answer that. It can only make the question impossible to avoid.

---

## Paying

Paying a supplier is the mirror image of being paid, and it has the same shape: a document (the
bill), a payment, and a match between them.

> *Register a payment of the full amount of BILL/2026/0031, dated today, by bank transfer.*

> *Payment registered for BILL/2026/0031: £1,260.00 to Pennine Paper, from the bank journal, dated
> 14 November 2026. The bill is now fully paid; the supplier's balance is zero.*

The bank journal is not the bank. It is the company's *record* of what the bank did, and the two
have to be reconciled—which is the monthly ritual described in the next chapter but one. The
distinction matters because it is where a company discovers that a payment it recorded was never
made, or a payment the bank made was never recorded.

## A short history of the purchase order

The purchase order as a document is a child of the railway age. Before railways, a merchant bought
from people he could see, and a handshake plus a ledger entry was enough. Railways created distance:
a buyer in Manchester ordering from a mill in Leeds needed a document that said what was ordered, at
what price, and when, because the goods would arrive days later and the man who ordered them might
not be there.

The form of the modern purchase order—number, date, supplier, lines, quantities, prices, terms—was
fixed by the early twentieth century and has not changed since, because it encodes the minimum
information needed to resolve a dispute. Software did not change the document. It changed the cost
of producing, sending, matching and finding it.

Which is, in a sentence, the argument of this whole book.

## The supplier record, and what it is for

A supplier in an ERP is not an address book entry. It is a set of terms, and the terms are what
makes the paperwork work.

Riverton's supplier records were built in an afternoon, and each one holds five things that matter:
the **payment terms** (thirty days from the invoice date, or end of month following, which are very
different things), the **currency**, the **tax treatment** (whether the supplier charges VAT and
under which regime), the **delivery lead time** that the buyer expects, and the **contact** who
answers when something is wrong.

None of those is decoration. Payment terms decide the due date on every bill, and a supplier whose
terms are recorded as "30 days" when they are actually "60 days net" will be paid early every month
for a year—which sounds harmless and is in fact a small, permanent loan to a supplier who did not
ask for it. The currency decides whether a bill in euros is converted at the rate on the invoice
date or the payment date, which is a difference that shows up as a gain or a loss. The lead time
decides when the system expects the goods, which is what makes the "late purchase orders" report
mean anything.

The old system had none of this. It had a folder of invoices and a telephone number written on the
inside of the folder.

## What a purchase order does not do

It is worth being clear about the limits, because a company that expects too much from a document
will be disappointed by the software that produces it.

A purchase order does not **negotiate**. It records the price that was agreed, and the assistant can
show you what you paid last time, and what you paid the time before—which is the ammunition for a
negotiation, not the negotiation.

It does not **guarantee** delivery. It creates an expectation, and the expectation is what the late
orders report measures.

It does not **check the goods**. That is the receipt, and the receipt is a person with a clipboard.

And it does not **pay**. Payment is a separate decision, made later, usually by somebody who looks at
the bank balance first.

What it does is make all four of those things *visible*, and visibility is what turns a relationship
conducted by telephone into a relationship that can be examined.

## The price that crept up

The pallet charge that Doreen found in chapter nineteen had a counterpart on the buying side, and it
was found by the same kind of question.

> *Which suppliers have raised their prices in the last six months, and by how much?*

The answer listed four suppliers and eleven products, and one of them was the paper: the purchase
price had gone from £2.05 to £2.18 a ream in July, which is six per cent, on a product that Riverton
buys by the pallet.

Six per cent on paper was, at Riverton's volumes, about £1,900 a year. Nobody had noticed, because
nobody had a list of what they paid before. The buyer—Maggie, in this case—had noticed that the
invoice "looked a bit higher" and had assumed it was her imagination.

That is the pattern that this whole book keeps returning to: the money is not lost in large,
dramatic mistakes. It is lost in changes that are too small to notice one at a time and too large to
ignore when they are added up. A system that remembers the previous price makes them notice-able,
and noticing is most of the work.

## The one thing to get right on the first day

If a company takes one thing from this chapter, it should be this: **record the payment terms on the
supplier, not on the invoice.**

An invoice with terms typed on it is a document that will be paid on those terms once. A supplier
with terms on the record is a supplier whose every invoice is due on the right day, forever, without
anybody thinking about it. The difference is thirty seconds of configuration and a year of not
having this conversation:

"Why are we paying Pennine early?"
"I don't know, the system says the bill is due."
"The bill is due in sixty days, not thirty."
"Then the supplier record is wrong."
"Since when?"

Since the first day, usually, and nobody noticed because paying early is not an error that anybody
complains about—except the person who looks at the cash flow in February.

---

Tom's verdict, at the end of the first month of buying through the system, was characteristically
practical.

"I used to think a purchase order was paperwork," he said. "It's not. It's the only thing that stops
me paying for something I didn't get."

Maggie asked him whether the system had caught anything.

"Twice. Once the invoice was for twenty more than we received, and once the price had gone up
without anybody telling us. Both times I'd have paid it, because I'd have looked at the invoice and
thought, yes, that's about right."

*About right* is the phrase to remember. Most of the money lost in a small company is lost in the
gap between *about right* and *right*, and the gap is not closed by being more careful. It is closed
by having three numbers to compare, and a machine that compares them every time.
