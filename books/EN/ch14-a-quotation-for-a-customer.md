# 14. A Quotation for a Customer

The first real piece of work the assistant did at Riverton was a quotation, and it was for the
customer whose invoice had started the whole story.

Ashfield Academy wanted four hundred ring binders and twenty boxes of whiteboard markers, for the
start of the summer term. Priya had the request in an email, which she had read twice, because the
quantities were unusual: four hundred binders was a term's worth, and twenty boxes of markers was
more than the school had ever ordered at once.

On the old system this would have taken her twelve minutes: open the accounting program, find the
customer, create a quotation, add two lines, look up the prices in the spreadsheet that held the
contract prices, apply the discount, print it, email it, file it. On the new system it took forty
seconds, and the twelve minutes went somewhere more useful—into a telephone call to Carol at
Ashfield to ask whether the markers were for the whole school or for the art department, which is
the kind of question that prevents a return.

Here is what Priya typed.

> *Create a quotation for Ashfield Academy for 400 A4 ring binders, blue, and 20 boxes of whiteboard
> markers, assorted colours, at the contract prices. Delivery to the school, end of next week.*

And here is what came back.

> *Quotation S00012 created for Ashfield Academy: 400 × Ring binder A4 (blue) at £3.40, 20 ×
> Whiteboard markers (pack of 4, assorted) at £11.40. Net £1,588.00, VAT £317.60, total £1,905.60.
> Delivery date set to Friday 27 June. The quotation is in draft — say "confirm" when you want it to
> become an order.*

Forty seconds, and every number in it was checkable.

---

## The pricelist, and why the contract price is not a discount

The price the assistant used for Ashfield—£3.40 for a binder that lists at £3.95—came from neither
the product record nor a discount. It came from a *pricelist*, and the distinction is one that
companies get wrong for years.

A pricelist in Odoo is a set of rules attached to a customer (or to a customer group, or to a
currency): for this product, or this category, or everything, apply this price, or this percentage
off, or this formula. Ashfield has a contract pricelist from January, agreed in a meeting, signed on
a single page, and it says what the school pays for the twelve products it buys regularly.

The difference between a pricelist and a discount is not cosmetic.

A **discount** is an adjustment to a price, applied to a document, by a person, at the moment of the
sale. It is visible on the quotation, it is auditable, and it is a decision somebody made.

A **pricelist** is the price. It is not an adjustment; it is what the customer pays, and the list
price is a different number that this customer never sees. A quotation for Ashfield that showed
£3.95 with a fifteen per cent discount would be *correct* and would also be a small insult: it would
tell the customer that the company's real price is higher and that they are being given a favour.

There is a third possibility, which is what most small companies actually do: a spreadsheet with
the contract prices in it, consulted by a person, and typed onto the quotation by hand. That works
until the person is on holiday, the spreadsheet is out of date, or the contract is renegotiated and
the spreadsheet is not.

## What happens when the price is wrong

Every company has a story about a price that was wrong on a quotation, and the stories all have the
same shape: the error was found after the order was confirmed, the customer was telephoned, and
somebody had to decide whether to honour the price or explain the mistake.

The decision is usually to honour it—the difference is small and the relationship is not—and the
cost is written off as a lesson. What the company learns from the lesson is usually the wrong thing:
*be more careful*, rather than *make the price a fact rather than a memory*.

A pricelist makes the price a fact. It lives in one place, it is dated, it applies to every document
for that customer, and when the contract is renegotiated somebody changes it once. The assistant
reads it the same way a person would, except that it cannot forget which spreadsheet is current.

The one thing a pricelist cannot do is *decide*. Whether Ashfield gets fifteen per cent off list, or
a fixed price, or a price that rises with the paper index, is a commercial decision made by people.
The system's job is to apply it exactly, every time, and to make it visible when it changes—which is
the subject of the next section.

## The quotation that changed a price

Three months later, Priya asked a question that had not been possible before.

*Which customers are paying a price that has not changed since January, and what would it cost us
to raise it by three per cent?*

The answer was a list of nine customers and a number: about £4,100 a year of additional revenue,
with the arithmetic per customer. The prices had not changed because nobody had looked, and nobody
had looked because looking required opening nine pricelists and comparing them with the purchase
prices, which would have taken an afternoon.

Whether to raise the prices is a commercial decision, and Riverton raised them for four of the nine
and left the others alone for reasons that had nothing to do with the arithmetic. But the decision
was made with a number in front of it, in ten seconds, instead of being postponed for another year.

That is the pattern again: the machine does not decide. It makes the decision cheap enough to take.

---

## What actually happened

It is worth slowing that down, because the speed is not the interesting part.

The assistant did not know what a ring binder was. It had never seen Ashfield Academy's contract,
and it had no idea what a school term is. What it had was a set of tools and a description of what
each one does, and a model of the company that somebody else had built.

So when Priya's instruction arrived, the assistant did what a new employee does on their first day:
it looked things up.

It searched the customers for a name matching *Ashfield Academy* and found one—and, because it is
cautious by design, it would have asked if it had found two. It searched the products for *ring
binder* and found a product with variants, and it picked the blue one because Priya had said blue.
It searched for the markers and found the pack of four, assorted. It asked the ERP for the price of
each, for that customer, on that date, which is a different question from "what is the price of this
product" and the difference is the whole of chapter ten.

Then it created the quotation: a document with a customer, a date, two lines, a tax calculation and
a state. And then it stopped, because a quotation in draft is not a commitment, and it said so.

That last sentence is the most important thing the assistant did. It did not confirm the order. It
did not reserve the stock. It did not send anything to anybody. It produced a *proposal*, and it
told Priya that the proposal was waiting for her.

---

## The state machine, and why it matters

A quotation, an order and an invoice are not three documents. They are three states of the same
intention, and the transitions between them are the moments where a company commits.

**Draft.** A proposal. Nothing has been promised, no stock is reserved, the price can change. In
Odoo this is called a quotation, and it has a validity date, because a price quoted in June is not
necessarily a price in September.

**Confirmed.** An order. The company has promised to deliver, at a price, by a date. Stock is
reserved (or, in a company that does not reserve, at least the intention is recorded), and the
document gets a number that will appear on the delivery note and the invoice.

**Delivered.** The goods have left. Now there is a stock move, and a piece of paper the customer
signed.

**Invoiced.** The money has been asked for. Now there is a ledger entry, and a tax point.

**Paid.** The money has arrived. Now there is a bank transaction that has to be matched to the
invoice, which is the step where most small companies lose track of their cash.

Each transition is a decision, and the ERP's job is to make sure the decision is made deliberately.
A quotation that becomes an order without anybody deciding is a promise the company did not know it
had made. An order that becomes an invoice before the goods leave is a tax point that has moved
without permission.

Priya read the quotation, changed one thing—she reduced the binders to three hundred and fifty,
because the art department had found a cupboard full—and confirmed it.

> *Change the binder quantity to 350 and confirm the order.*

> *Sales order S00012 confirmed: 350 × Ring binder A4 (blue), 20 × Whiteboard markers. Total
> £1,712.40. Delivery date Friday 27 June. Stock reserved: 350 binders available, markers available.*

Notice what the assistant added at the end: *stock reserved, available*. It had not been asked. It
had checked, because the next thing that would happen is a delivery, and a delivery that cannot be
made is worse than a quotation that cannot be confirmed.

![The same operation on the demonstration installation: order S00002 confirmed, with the totals, the state and two things the assistant thought you should know](../../assets/screens/assistant-06-order.png)

The figure above is worth reading carefully, because it is the behaviour this chapter has been
arguing for, captured rather than described. The assistant reports the order number, the state
(*draft → sale*), the untaxed amount, the tax and the total; then it volunteers two things that
were not asked for—that the tax was applied automatically at fifteen per cent, and that confirming
an order creates neither a delivery nor an invoice. And it ends by saying how it checked: *I
verified the record by re-reading it after confirmation.*

That last sentence is the difference between an assistant and a form. A form tells you what it
saved. A colleague tells you what they did and how they know it worked.

---

## A short history of the quotation

The word *quotation* comes from the Latin *quotare*, to number—the same root as *quote* in the
sense of citing a passage. In commerce it has meant, for at least four hundred years, a statement of
price offered to a buyer, and its legal status has been argued in courtrooms ever since.

The argument is always the same: is a quotation an offer, which becomes a contract when accepted, or
an invitation to treat, which is merely an opening position? The answer depends on the wording, the
context and the jurisdiction, and it is the reason a quotation form usually carries a line like
*this quotation is valid for thirty days* and *subject to availability*.

An ERP does not settle the legal question, but it does something related and useful: it records
*which* quotation was sent, *when*, *to whom*, and *what it said*. When a customer telephones in
September and says "you quoted me four hundred pounds," the company can find the document and see
whether it said four hundred or four hundred and fifty, and on what date, and for how many.

That is not a small thing. In the old system, the answer lived in an email thread, in a printed
copy in a tray, and in Priya's memory—in that order of reliability.

---

## What the assistant did not do

Three things are worth noticing in what did *not* happen.

It did not apply a discount. Ashfield has a contract price, which is a different mechanism from a
discount, and the assistant used the contract price because that is what the customer's record says.
If Priya had wanted a discount, she would have had to ask for one, and the discount would have been
recorded—which is the difference between a price and a favour.

It did not choose the delivery date on its own. It took *end of next week* and turned it into a
date, which is a small act of interpretation, and it said which date it had chosen so that Priya
could correct it.

And it did not send the quotation. Sending is an action with a customer at the other end, and the
assistant has no tool for email in Riverton's configuration—deliberately. The quotation was printed
to a PDF by the ERP and attached to an email by a person, which took Priya thirty seconds and kept
the last step, the one where a document leaves the building, in human hands.

Some companies will want that step automated, and the system can do it. Riverton decided, in the
first month, that nothing would be sent to a customer without a person looking at it. It is a
decision a company can revisit; it is not a decision a company should make by accident.

---

The order sat in the system for two days, waiting for the delivery date.

On the Thursday, Tom asked the assistant a question that Priya had not thought to ask.

> *Which orders are due for delivery in the next three days, and is the stock there for all of
> them?*

The answer was a list of four orders and a sentence that changed the week: the binders for Ashfield
were there, the markers were there, but the order for Northgate Library Service needed twelve boxes
of A4 paper and there were nine.

Nine boxes, and a promise to deliver on Monday. That is the kind of fact that used to be discovered
by a driver at the loading bay, and it was discovered instead on a Thursday afternoon by somebody
who thought to ask.
