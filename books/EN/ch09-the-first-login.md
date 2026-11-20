# 9. The First Login

The icon opened two windows, which is one more than most programs open.

The first was a page in the browser: the start page from the previous chapter, with its one door
and the account. The second was a black window with a cursor in it and a short question about the
AI provider. Between them they were the whole system—the page was where the data would be looked
at, the black window was where it would be asked for.

Before Maggie clicked anything she asked the question that stops most people at this point, and it
is worth answering slowly, because everything else in this book assumes the answer.

"What am I looking at?"

## A program that lives in a browser

Odoo is a **web application**. The phrase covers two different arrangements of the same software,
and the difference decides who is responsible for it.

In the familiar arrangement—the cloud one—the program runs on a computer belonging to somebody
else, in a building you have never visited, and your browser is a window onto it. You type an
address such as `riverton.odoo.com`, the request travels over the internet, and a machine in a data
centre answers. Nothing is installed on your desk. You rent the program by the month, somebody else
keeps it running, and in exchange your customer list lives on their disk.

In the arrangement this book uses, the program runs on the computer in front of you. There is no
building and no monthly invoice: there is a folder on your disk, a database on the same disk, and a
small program that listens for requests and answers them. The browser is still the screen, but the
machine behind the screen is yours.

That is why the address looks strange. `localhost` is the name a computer uses for **itself**:
`localhost:8069` means *the program on this machine, listening at door 8069*. It is not a company,
it is not a website, and it does not open from anybody else's computer—which is exactly the point.
The address is the door, and the door is in your office.

Two consequences follow, and both surprise people who have only used cloud software.

The first is that **the program has to be running**. A cloud service is always up because somebody
is paid to keep it up; your copy is up when the black window, or a hidden background process, is
running it. If the machine is off, or the program was stopped, the browser shows a page that cannot
connect—not a fault in your data, just a door with nobody behind it. Double-clicking the icon again
starts it, which is the answer to most of the questions in this chapter.

The second is that **the address is not optional**. There is no menu entry that opens Odoo directly,
because Odoo has no window of its own: its window is a browser tab, and a browser tab needs an
address. This is the small piece of knowledge that the previous edition of this book assumed, and a
reader's report proved the assumption wrong. A person who has never looked after a server has no
reason to know that a web application is reached by typing its address, and no way to guess
`localhost:8069` from a desktop icon that opens something else.

That is the whole reason the start page exists. It is not decoration: it is the address, written
down, with the account next to it.

## The black window is the assistant

The second window has no title, no menus and no buttons: a black rectangle with a cursor. It is the
assistant, and it is the only place where a sentence can be typed.

It looks unfinished because it is not a consumer program. It is a *terminal*—the plain text surface
that programs have used since before the mouse existed—and the assistant speaks there because that
is where a conversation with a machine is cheapest and clearest: no layout to maintain, no button
to hunt for, and the answer printed in the order it was produced, wrong turns included.

The three windows have three different owners, and knowing which one may be closed is most of what
a new user needs:

| Window | What it is | If you close it |
|---|---|---|
| The start page | a file on your disk, opened by the browser | nothing happens; the icon opens it again |
| The browser tab with Odoo | the ERP, served by the program on this machine | nothing happens; the data stays and the program keeps running |
| The black window | the assistant | the assistant stops. Odoo keeps running, and the icon starts the assistant again |

Maggie left the start page open, because the address was on it, and clicked *Open Odoo*.

## The login page, and the part of the address that matters

The browser went to `http://localhost:8069/web/login?db=odoo_agent`, and the page was almost empty:
a white card, a logo made of two purple shapes, and two fields.

![The ERP's login page. The address bar is part of the picture: this is a program on this computer, at the door 8069](../../assets/screens/odoo-01-login.png)

The `db` part of the address names the database. `odoo_agent` is the one the installer created, and
naming it means the browser cannot land on a different one by accident—a machine can hold several
databases, a test copy and a real one, and without the name Odoo asks which you mean. It is not a
setting to remember: the start page and the icon write it for you.

One thing on this page is a trap, and it is worth naming before it is clicked. At the bottom, in
small grey letters, is a link called *Manage Databases*. It opens Odoo's own database manager, which
can create, duplicate, back up and **delete** databases, and it asks for a master password that has
nothing to do with your login. The installer has already created the database; the manager is a tool
for an administrator who knows why he opened it. Nothing in this book needs it.

Maggie typed the administrator address the installer had printed, and the password, and pressed
Enter.

If the page in your browser is not this one, it is one of three things, and none of them means the
installation failed: a page about Odoo on the vendor's website, a website with a logo you did not
choose, or a list of databases. Appendix C takes them one at a time.

Nothing dramatic happened. That is the first thing worth saying about the ERP: it does not greet
you. It does not congratulate you. It opens a page with a menu across the top and a few coloured
cards, and waits to be told what it is.

![The first screen after the login: the company has no data yet](../../assets/screens/odoo-02-dashboard.png)

This is the moment where a small company usually loses its nerve. The system looks empty, the
cards are meaningless, and there is a temptation to conclude that something has gone wrong—or,
worse, to start clicking, which is how a company ends up with four warehouses, three currencies and
a customer called "test".

The empty page is not a fault. It is the truth. The system knows nothing about Riverton yet: not
its name, not its money, not what it sells. What it knows is how to *be* a company. The next hour
is the hour in which it learns which company.

---

## The first thing to change: the language of the machine

Odoo speaks many languages, and the installer took the one from the machine, which on this PC was
Italian. A company in a market town in England wants its invoices in English, its tax names in
English, and its error messages in English, so the language is the first setting to change, before
anything has been named.

The setting lives in the user's preferences—the little circle in the top right, *My Profile*,
*Preferences*—and it is per user, not per company. That distinction is worth understanding early:
Odoo is full of settings that belong to *you* (language, time zone, which notifications you want)
and settings that belong to *the company* (currency, taxes, the chart of accounts). Changing your
language changes nothing for anybody else; changing the currency changes everything for everybody.

## The second thing: the company itself

Under *Settings*, the first entry is the company. It is a form with a name, an address, a tax
number, a currency, a country and a logo, and it is the most important form in the whole system,
because every document that leaves the building is stamped with what it says.

![The company form: name, address, currency, country](../../assets/screens/odoo-03-company.png)

Three fields on that form deserve a paragraph each.

**The name** is what appears on invoices. It is not necessarily the name the company uses in
conversation; it is the name the customer's accounts department will see and the name the tax
office will match against a registration. If they differ, use the registered one.

**The country** decides a surprising amount: which chart of accounts the system offers, which taxes
exist, the format of the addresses, the way dates are printed. Choosing it late is possible and
painful; choosing it first is free.

**The currency** is the one in which the company keeps its books. Not the currency of every
transaction—Odoo handles foreign currency, with exchange rates and gains and losses—but the
currency of the ledger. For Riverton, that is the pound.

There is a warning attached to changing the currency after documents exist, and it is not a
formality: the ledger is denominated in it, and changing it retroactively is like changing the unit
of measure of a warehouse after the shelves are full. Do it now, on an empty system, and it is a
drop-down.

## The third thing: the people

Odoo comes with one user—the administrator—and the temptation is to keep using it for everything,
because it is the only one that exists.

Resist it, and resist it for a reason that has nothing to do with security theatre. Every record in
the ERP remembers who created it and who changed it. If everybody works as the administrator, that
memory becomes useless: the system will say that *admin* created the invoice, *admin* approved the
discount and *admin* deleted the customer, and the question "who did this?" will have no answer.
The audit trail is only worth something if the people are separate.

For Riverton, four users were enough to start:

| User | Role | Why |
|---|---|---|
| Administrator | full rights | configuration, and nothing else |
| Doreen | accounting, invoicing | her job, and her signature on the ledger |
| Priya | sales | quotations, orders, customers |
| Tom | inventory | receipts, deliveries, stock adjustments |

Each of them has a login, a password and a role. Each of them appears in the audit trail by name.
And each of them can be given more or fewer rights without touching anybody else's.

There is a fifth user, which nobody logs in as: the assistant. It was created by the installer, it
has its own key, and it has exactly the rights it needs to do the work described in this book. We
will meet it properly in chapter twelve.

## The fourth thing: what the company does

The last question of the first hour is the one that decides which parts of the ERP are switched on.
Odoo is modular: it can be an invoicing program, or a warehouse, or a factory, or a shop, and the
difference is which applications are installed.

For a wholesaler, the answer is short: *Sales*, *Purchase*, *Inventory*, *Invoicing*, and
*Accounting*. Not *Manufacturing* (Riverton does not make anything), not *Point of Sale* (there is
no shop), not *Website* (the web shop is a separate thing and can be connected later). Each
application that is installed adds menus, and each menu is an invitation to confusion if nobody
needs it.

Maggie installed five applications in the first hour and resisted the other twenty. That restraint
is worth more than any configuration: a system with five applications that everybody uses is worth
more than a system with twenty that nobody trusts.

## The dashboard, and why it is empty on purpose

The coloured cards on the first screen are Odoo's attempt to answer the question *what should I look
at?* before you know enough to ask. There is a card for sales, one for invoices, one for stock, and
each one shows a number and a small chart.

On a new company every card shows zero, and the charts are flat lines. That is not a bug and it is
not a bad first impression; it is the only honest thing the system could show. A dashboard that
invented a plausible number for an empty company would be a dashboard you could never trust again.

The cards become useful at different times, and knowing which to ignore is part of the first month.

**Sales** is useful from the first quotation. It shows the pipeline in money: quotations sent, orders
confirmed, invoices to raise.

**Invoicing** is useful from the first posted invoice, and it is the card Maggie looked at every
morning: how much is owed, how much is late.

**Inventory** is useless until products exist and stock has been counted, which is why chapter eleven
comes before the assistant.

**Accounting** is useless until the chart is configured and the first entries are posted.

A company that tries to make all four cards meaningful in week one will spend a fortnight on
configuration and lose its nerve. A company that ignores three of them and makes one work will have
a system that is useful by Friday.

## The first person who is not the owner

Priya logged in on the second afternoon, from her own desk, with the account Maggie had made for
her, and the first thing she said was: "Where's everything?"

The screen she saw was not the screen Maggie had been looking at. The menus were shorter. There was
no *Settings*, no *Users*, no *Accounting* beyond the invoices she was allowed to see. There was
*Sales*, with quotations and orders, and *Customers*, and a search box.

That is the whole point of a user, and it is worth watching somebody meet it for the first time.
For thirty years Priya had worked in a system where everybody could do everything, because the
system was a shared folder and a set of files. The idea that a program would show her *less*, on
purpose, took about ten minutes to stop feeling like an insult and start feeling like a relief.

"I can't break anything," she said, at the end of the afternoon.

"You can break a quotation," Maggie said. "You can't break the ledger."

There is a deeper point in that exchange, and it is the reason the users were set up before any data
was entered. In a system where everybody can do everything, nobody is responsible for anything: when
a price is wrong, it is wrong because somebody, somewhere, typed it. In a system where each person
has a role, the price is wrong because Priya typed it—which sounds harsher and is in fact kinder,
because it means the price can be fixed, and the person who fixed it can be thanked.

The assistant, when it arrived, was given exactly the same treatment. It is a user in that list,
with a role, and it appears in the audit trail like everybody else.

## The page that tells you what to do next

The first screen after the login is not the dashboard. It is a page called *First steps*, and it is
the most thoughtful thing in the whole application.

It lists five things: choose your company's country, set up your chart of accounts, add your
products, add your customers, and invite your colleagues. Each one is a link, and each one disappears
when it is done. When all five are done, the page disappears too.

There is a design principle in that, and it is worth naming because most software gets it wrong:
**the system should know what it does not know yet.** A dashboard that shows zeros is a dashboard
that tells you nothing. A checklist that says *you have no customers* is a checklist that tells you
exactly what to do next, in the order that makes sense.

The order matters, too. Country first, because it decides the chart of accounts; chart of accounts
before products, because products need income accounts; products before customers, because a
quotation needs both. A company that starts with customers—which is the natural instinct, because
customers are what a business is about—will discover in an hour that it cannot quote anything.

Maggie did the five steps in one afternoon, in the order given, and the only one she skipped was
*invite your colleagues*, because she wanted a day to make her own mistakes before anybody watched.

That was a good decision, and it is the one piece of advice in this chapter that is not in the
software.

---

By the end of the afternoon the page looked different. There were menus: *Sales*, *Purchase*,
*Inventory*, *Accounting*. There were four users. There was a company with a name, a currency and a
country. There was still no data—no customers, no products, no invoices—but the system now knew
what kind of company it was working for, which is the difference between a blank page and an empty
ledger.

Doreen came in at half past four, as arranged, and sat down in front of it.

She looked at the screen for a while without saying anything. Then she said: "It's very empty."

"It is."

"And this is going to know more about this company than I do."

Maggie had been expecting the question in one form or another, and had decided to answer it
honestly.

"It's going to *remember* more than you do," she said. "It isn't going to know more. It doesn't
know that Ashfield's finance officer is called Carol, or that the school gate is locked before
eight, or that the manager there prefers a telephone call to an email. It doesn't know that the
blue binders are the ones that sell, or that the paper supplier is unreliable in August. It knows
what we tell it, and it never forgets what it's told."

Doreen considered this.

"So I'm the one who tells it," she said.

"You're the one who decides what's true. That's a different job from the one you had on Monday."

It was, and it took her a few weeks to stop feeling that the system was watching her. But she was
the first to admit, by the spring, that the ledger had become a place she could *ask*—and that
asking is a better way to spend a morning than searching.

The next morning they started with the money, because money is where every company's arguments
begin.
