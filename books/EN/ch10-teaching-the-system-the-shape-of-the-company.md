# 10. Teaching the System the Shape of the Company

The argument about the chart of accounts lasted two days and was, in the end, about whether
Riverton was a stationery shop or a business.

A chart of accounts is the list of buckets into which a company sorts its money. Every pound that
moves is put into one of them: sales of goods, sales of services, carriage charged, carriage paid,
wages, rent, electricity, bank charges, stock, debtors, creditors, VAT. A small company has perhaps
forty buckets; a large one has four hundred; the difference is not sophistication, it is the number
of questions the accounts have to answer.

Doreen wanted forty. Maggie wanted twelve.

"It's not a matter of wanting," Doreen said, on the second morning, with the patience of somebody
explaining something for the third time. "If I can't separate the carriage we charge from the
carriage we pay, I can't tell you whether the deliveries make money."

"Can't you look at the invoices?"

"Not without reading four hundred invoices."

That, Maggie conceded, was a fair point, and it is the rule that settles every argument about a
chart of accounts: **a bucket earns its place if somebody will ask a question that only that bucket
can answer.** Carriage charged and carriage paid earn theirs. "Sundry expenses" does not; it is a
bucket that exists so that nobody has to decide, and it becomes the place where a company's money
goes to be forgotten.

---

## What the system brings with it

Odoo does not ask you to invent a chart of accounts. It asks you which country you are in, and then
it installs the chart that accountants in that country expect—the same numbering, the same names,
the same tax codes—so that your auditor recognises the place, and so that the tax return has
somewhere to come from.

For Riverton that meant installing the United Kingdom accounting localisation. It is one of a
hundred such packages; the installer had already downloaded the code, and switching it on took a
minute in the *Apps* screen.

![The Apps screen, where a localisation is installed](../../assets/screens/odoo-04-apps.png)

When it finished, the accounting module had a chart of accounts, a set of taxes, four journals and
a fiscal year. None of it was Riverton's yet, and all of it was a reasonable starting point—which
is exactly what a chart of accounts should be.

![The chart of accounts, as installed by the localisation](../../assets/screens/odoo-05-chart-of-accounts.png)

The accounts are numbered, and the numbering is not arbitrary. The first digit is the class:
1 for assets, 2 for liabilities, 3 for equity, 4 for income, 5 for expenses, 6 for the cost of
goods. A bookkeeper reading a trial balance can tell at a glance what kind of number they are
looking at, in any company in the country, without knowing the company.

Doreen went through the list with a pencil, and did three things.

**She deleted nothing.** An account with no activity costs nothing, and deleting one that an
auditor expects to find is a conversation nobody wants.

**She renamed four accounts** to match the words Riverton actually uses. The system called one
"Merchandise"; Riverton calls it "Stock — bought in". The name on the screen should be the name in
the conversation, or people will not use it.

**She added two accounts**: one for carriage charged to customers, one for carriage paid to
carriers. Those were the two questions she wanted to answer, and now she could.

## The three questions that decide the chart

Doreen and Maggie settled their argument with three questions, and they are worth writing down
because they work for any company.

**What will you ask every month?** The answers became accounts: sales of goods, sales of carriage,
purchases of goods, purchases of carriage, wages, rent. Anything nobody would ask about did not get
an account.

**What does the tax office need to see separately?** The answers were few—standard-rated sales,
zero-rated sales, exempt—and they are not optional. A chart that cannot produce the boxes on the
return is a chart that will be rebuilt in a panic.

**What would an auditor ask for first?** The answers were the bank, the debtors, the creditors and
the stock. Those four have to be clean, reconciled and understandable at a glance, because they are
where the money is.

Sixteen accounts came out of those three questions, plus the tax accounts the localisation had
already created. It is a smaller chart than an accountant would draw and a larger one than a
bookkeeper with a spreadsheet would need, which is about right.

## The settings that are easy to miss, and cost the most

Five settings on the company form are easy to skip and expensive to discover later, because they
appear on every document that leaves the building.

**The logo.** Small, and the first thing a customer notices. A company that sends invoices with the
default Odoo logo has told the customer something about how much attention it pays.

**The bank details.** They go in the footer of every invoice. A company that adds them by hand to
each document will eventually add the wrong account to one of them, and that is a conversation with
a customer who paid the wrong company.

**The default payment terms.** Thirty days, or end of month following, or fourteen days. Setting
them on the company means every new customer inherits them, and the exceptions are the exceptions
rather than the rule.

**The default taxes.** The tax applied to a new product if nobody chooses one. If this is wrong,
every new product is wrong, and the error is invisible until the first return.

**The fiscal year end.** Most companies use the calendar year, and some do not. The setting decides
when the year closes, and changing it later is a genuinely painful operation.

None of these is difficult, and all of them are the sort of thing that gets skipped on a busy
afternoon and discovered in March. The rule that saves the afternoon: **fill in the company form as
if a customer will see it, because a customer will.**

## The taxes

A tax in an ERP is not a percentage. It is a small machine with an input and an output: it takes a
line of an invoice, works out the tax, decides which account the tax goes to, and remembers the
period it belongs to so that the return can be produced.

The localisation installed the standard rates: twenty per cent on most goods, five per cent on some
(such as children's car seats and certain energy-saving materials), zero on books and on most food.
Riverton sells stationery, which is standard-rated, and paper, which is standard-rated, and the
occasional service, which is also standard-rated. The five per cent rate is there and will almost
never be used, which is fine; the important thing is that it exists, so that nobody invents a
fourth rate at the counter.

There is one trap worth naming, because it catches companies every year: **the tax is configured
per product, not per invoice.** If a product is set to the wrong tax, every invoice that contains
it will be wrong, and the error will be found by the tax office rather than by the customer. The
product form has a field for it, and filling that field correctly once is worth more than any
amount of checking later.

## The journals

Money arrives and leaves through a small number of doors, and Odoo calls them journals: *Customer
Invoices*, *Vendor Bills*, *Bank*, *Cash*, *Miscellaneous Operations*. Each journal has a code—INV,
BILL, BNK, CSH, MISC—and each document posted through it gets a number in sequence.

The sequence matters more than it looks. An invoice number must be unique and must follow the
previous one, because that is what makes the ledger auditable: if invoice 2026/0042 is missing, an
auditor will ask where it went. Odoo enforces this by refusing to post a document that would break
the sequence, which is one of the small strictnesses that makes the system worth having.

## What was not configured, and why

There is a long list of things a company *can* configure on the first day, and almost all of them
should wait.

**Multi-currency.** Riverton buys from a supplier in the euro area, so eventually yes. On the first
day, no: exchange rates, gains and losses, and the treatment of foreign-currency invoices are a
subject of their own, and doing them before the basic invoicing works is how a company ends up with
a ledger nobody understands.

**Analytic accounting.** The ability to tag every line with a project, a department or a cost
centre. Useful for a company with projects; a tax on a company without them.

**Multiple companies.** Odoo can hold several companies in one database, with intercompany
transactions. Riverton is one company. Adding a second one on the first day is how a company
discovers, in March, that half its invoices belong to the wrong legal entity.

**Budgets, assets, deferred revenues, landed costs.** All real, all useful, all later.

The principle is the one Sam had written on the napkin and Maggie had pinned to the board: install
what you will use this month. A setting that nobody uses is not a capability; it is a place where
somebody will eventually make a mistake.

---

## The bank, and the opening balance

There is one more piece of configuration that a company discovers late and wishes it had done
earlier: the bank.

Odoo installs a bank journal with no bank behind it. Connecting it to the real account means
entering the account's details, and then—this is the part nobody expects—deciding how the company's
*existing* money gets into the system.

A company that has been trading for thirty years does not start with zero in the bank. It starts
with whatever the statement says on the day the system goes live, and with a history that lives in
the old accounting program. There are two honest ways to handle that, and one dishonest one.

The honest way, for a small company, is an **opening entry**: one journal entry, dated the day
before go-live, that states what the company owns and owes—bank balance, stock value, what customers
owe, what suppliers are owed—and balances to the equity account. It is a snapshot, it is auditable,
and it takes an afternoon with the previous year's balance sheet.

The other honest way is to **bring the history in**: import the old invoices and bills so that the
aged debtors and creditors are real documents rather than one lump. More work, more useful, and
worth it if customers routinely pay late—because the moment the assistant can list overdue invoices,
it needs invoices to list.

The dishonest way is to type the bank balance into a field that looks like it will accept it. It
will. And then the ledger will not balance, and somebody will spend a weekend finding out why.

Doreen chose the opening entry, with the aged debtors imported as documents, and the afternoon it
took her was the first time she used the system for something she actually cared about. She was not
configuring software any more. She was moving her company's numbers from one set of books to
another, and checking, line by line, that nothing had been lost on the way.

---

## The first entry

On the third afternoon, Doreen posted the first document.

It was not an invoice, and it was not a sale. It was a bank payment: two hundred pounds from the
company's account to the account of a supplier, for paper delivered in October. She created the
supplier, created the bill, registered the payment, and watched the three documents link to each
other—bill to supplier, payment to bill, both to the bank.

Then she opened the ledger and looked at what the system had written.

Two entries. Two hundred pounds out of the bank; two hundred pounds off what the company owes the
supplier. Equal and opposite, in two different accounts, dated the day of the payment. Pacioli's
rule, performed by a machine in a fraction of a second, in a database in a folder in a user
profile.

She sat back and said something that Maggie wrote down, because it was the moment the system
stopped being software and became the company's memory.

"It's the same as my book," she said. "It's exactly the same as my book. Only I can ask it
questions."

That is the whole of the first week. Not a transformation: a recognition. The rules the system
follows are the rules she had been following by hand for thirty-one years, written down by
somebody else, six centuries ago, and now enforced by a machine that never gets tired and never
forgets to write the second line.

The rest of the book is what happens when you can ask it questions—and when something else can ask
them for you.
