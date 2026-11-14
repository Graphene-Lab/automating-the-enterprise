# 18. When the System Says No

The first refusal came on a Thursday afternoon, and it was the moment Doreen stopped being
suspicious of the system and started trusting it.

She had asked the assistant to correct a mistake: an invoice had been posted with the wrong
quantity, and she wanted it fixed.

> *Change the quantity on invoice INV/2026/0007 from 350 to 300.*

> *I cannot change it. INV/2026/0007 is posted, and posted invoices are read-only: the ledger
> entries and the tax point are already recorded. To correct it, cancel the invoice and issue a
> credit note, or issue a credit note for the difference. Which would you like?*

Doreen read it twice and then called Maggie over.

"It won't do it," she said.

"Won't or can't?"

"Can't. It says the ledger's already written."

That distinction—*won't* versus *can't*—is the subject of this chapter, and it is the reason a
business system is different from a helpful colleague.

---

## The three kinds of no

An ERP refuses for three different reasons, and it is worth learning to tell them apart, because
each one calls for a different response.

**The system cannot do it because the model forbids it.** You cannot post an invoice with no lines,
deliver goods you do not have, or change a document that has already produced ledger entries. These
refusals are structural: they protect the integrity of the model, and there is no override, because
an override would break the guarantee that makes the model worth having.

**The system cannot do it because the *user* is not allowed.** The assistant is a user with a role,
and if the role does not include deleting records, the request is refused by the permission system
before it reaches the model. These refusals are about authority, and they can be changed—by somebody
with the right to change them, deliberately, and with a record of having done so.

**The system cannot do it because the *data* is not there.** The customer does not exist, the
product has no price, the stock is in a location the user cannot see. These refusals are about the
state of the world, and they are usually the most useful, because they point at something that
needs fixing rather than something that needs overriding.

A good assistant tells you which kind of no it is. That is what happened above: the refusal named
the document, the reason, and two legal alternatives.

## The refusals that taught Riverton something

Over the first months, the system said no in a handful of ways that were each a small lesson.

**"Not enough stock."** Tom asked for a delivery of six hundred binders when there were four hundred
and twelve. The system refused, and offered to deliver what was available and create a backorder for
the rest. Tom chose the backorder, and the customer was telephoned before the van left—which is the
whole point of the refusal: it moved the conversation from the loading bay to the telephone, where
it could still be useful.

**"The accounting period is closed."** Doreen tried to post an invoice dated in the previous month,
after the month had been locked. The system refused and explained that the period was closed. She
moved the invoice to the current month, and then asked the assistant for a list of everything
posted after the close—which came back empty, which is what a closed period is for.

**"This user cannot delete records."** The assistant, asked to remove a duplicate customer, said it
could not, and offered to archive it instead. Archiving keeps the record and hides it from the
lists, which is the correct answer for a duplicate that has documents attached. The refusal had been
configured on purpose, in chapter twelve, by somebody who thought about it in advance.

**"That product has no tax."** A new product had been created without a tax rate, and the quotation
refused to compute a total. The refusal pointed at the product form, and the fix took thirty
seconds. Without the refusal, the quotation would have gone out with no VAT—and the company would
have discovered it at the end of the quarter, in a return that did not add up.

## Reading the log

Every refusal leaves a trace, and learning to read the trace is the skill that turns an assistant
from a black box into a colleague.

The assistant writes a log: what it was asked, which tools it chose, with which arguments, what came
back, and how long it took. It is not a pretty document—it is a file, in a folder, with timestamps—
and it is the first place to look when something has gone wrong.

Three patterns are worth recognising.

**A loop.** The same tool called with the same arguments, three or four times. That is the assistant
trying to make something work and failing in the same way each time—usually because a document is in
a state it did not expect. The refusal is in the log, three times, and reading it once is enough.

**A wrong tool.** The assistant chose *create* when it should have chosen *update*, and the ERP
refused because the record already existed. The log shows the choice; the fix is in the instruction,
which did not say *update*.

**A silent success that was not what was wanted.** No error, no refusal, and a result that is
technically correct and practically useless. This is the hardest pattern, because nothing in the log
looks wrong. The defence is the check: ask the assistant what it did, and compare that with what you
meant.

Doreen reads the log every Friday, for the same reason she used to read the bank statement: not
because she expects a problem, but because reading it is how you learn what normal looks like—and
therefore how you notice when it is not.

## The refusal that saved a customer

One refusal in Riverton's first year was worth more than any of the successes, and it happened in
the middle of an argument.

A customer—a large one, and a difficult one—had been sent an invoice for a delivery they claimed
never arrived. The delivery note was signed, but the signature was illegible, and the customer's
purchasing manager was insisting that the goods had been refused at the gate.

Priya asked the assistant to issue a credit note, because the customer was threatening to take their
business elsewhere and the invoice was £640.

The assistant refused, and the reason it gave is the reason this story is in the book.

> *I can create a credit note, but you should know what it will look like in the accounts: a credit
> note with no return behind it records that the goods were never supplied. The delivery was
> validated on 3 September by Tom Beck, and the stock move shows 40 items leaving Shelf A. If the
> customer refused the delivery, the goods should have come back and there is no return recorded. If
> they did not refuse it, the credit note would be paying for goods that were delivered. Which is it?*

Priya telephoned the customer, asked the question the assistant had asked, and discovered that the
delivery had been accepted by a temporary security guard who had put the pallet in a store room and
not told anybody. The invoice was paid in full, and the customer apologised.

The refusal did not save £640. It saved a relationship, and it did so by refusing to let a person
skip a question—which is what a good bookkeeper has always done, and what this system does because
somebody configured it to.

## The refusals a company should design on purpose

Most refusals come with the software. A few should be added, deliberately, and they are the ones
that turn an ERP from a system of record into a system of control.

Four are worth considering in any company that lets an assistant write.

**A credit limit on customers.** When an order would take a customer above their limit, the system
can refuse to confirm it, or require approval. The assistant will then report the refusal and the
number, which is exactly the conversation a salesperson should have with the owner—before the goods
leave, not after.

**A maximum discount.** Odoo can be configured so that a discount above a threshold needs a second
person. The assistant cannot grant it, because the assistant is one user with one role; it can only
say who could.

**A closed period.** Once a month is locked, nothing posts into it, by anybody, including the
assistant. That is the single most effective control in the whole system, and it costs one setting.

**A four-eyes rule on payments.** In Odoo this is a configuration of the payment process, not a
feature of the assistant, but the effect is the same: the assistant prepares the payment run, a
person releases it.

None of these is a technicality. Each one encodes a decision the company has already made about how
it wants to be run, and each one turns that decision into something that cannot be forgotten on a
busy Friday.

## What a refusal costs

There is a cost to strictness, and it is worth naming because companies that ignore it end up
turning the rules off.

A refusal stops work. Somebody has to stop what they are doing, find out why, and either fix the
data or ask for an exception. In a small company, that somebody is often the owner, and the owner is
often the busiest person in the building.

The cost is real, and the way to keep it small is not to weaken the rule but to make the refusal
*informative*. A message that says *credit limit exceeded: £2,310 of £2,000, customer Calder and
Sons, last reviewed in March* tells the person what to do. A message that says *access denied* does
not.

That is the argument for an assistant in front of an ERP in one sentence: the rules are the ERP's,
and the *explanation* is the assistant's.

## Why strictness is the feature

There is a temptation, when a system refuses something, to look for the setting that turns the
refusal off. Most ERPs have such settings, and most of them are a mistake.

Consider what the refusals are protecting.

The refusal to edit a posted invoice protects the **audit trail**: the record of what was sent to
the customer, and when. A company that can edit its own history cannot prove anything about it.

The refusal to deliver stock that is not there protects the **promise**: the customer was told a
date, and the date depends on goods that exist.

The refusal to post into a closed period protects the **accounts**: a period is closed because
somebody has reported on it—to the bank, to the tax office, to the owners—and reopening it silently
would make the report a lie.

The refusal to let a user delete protects **accountability**: if a document can vanish, then the
absence of a document means nothing.

None of these is about tidiness. Each is about the one property that makes an ERP worth its cost:
that what it says is true, and can be shown to be true.

## The assistant's part in this

An assistant makes refusals *better*, in a way that is easy to miss.

A person meeting a refusal in a screen sees a red box with a code and a sentence. An assistant
meeting the same refusal can explain it in the language of the business, offer the alternatives, and
do the legal one if you agree. That is the difference between *Error: cannot modify a posted move*
and *the invoice is posted, so it can't be edited; I can issue a credit note for the difference, or
cancel and re-issue—which do you want?*

There is a risk in that fluency, and it is worth naming: an assistant that explains refusals
helpfully can make them feel negotiable. They are not. The explanation is a courtesy; the rule is
the rule. The assistant cannot override the ERP, because the assistant is not the authority—and any
assistant that claims otherwise has been given too much power, which is a fault in the installation,
not a feature of the model.

## The one refusal that is not a refusal

There is a fourth kind of no, and it is the most dangerous because it looks like a yes.

The assistant, asked a question whose answer is not in the system, may answer *plausibly*. Not
because it is lying, but because that is what a language model does when it has no facts: it
produces the most likely sentence. This is the hallucination problem, and the defence is
architectural, not moral: the assistant must be made to get its facts from the ERP, through tools,
and to say so when the tool returns nothing.

Riverton's rule, on the wall next to the napkin, is a single sentence: *if it can't show you where
the number came from, don't use the number.*

That rule is why every answer in this book includes the documents behind it—the invoice number, the
order, the list of moves. It is not decoration. It is the difference between a system you can audit
and a system you have to believe.

---

Doreen issued the credit note, and the invoice stood.

That evening she said something to Maggie that neither of them expected.

"I like that it argues with me."

"Why?"

"Because my old system did whatever I typed. If I typed the wrong number, it took the wrong number,
and it never told me. This one makes me say what I mean."

She thought for a moment.

"It's like having a bookkeeper who's been doing it for six hundred years and has no manners."

Which is, more or less, exactly what Pacioli's rules are: no manners, no memory of your excuses, and
no interest in whether you are in a hurry. Just the two sides of the page, and the refusal to let
them disagree.
