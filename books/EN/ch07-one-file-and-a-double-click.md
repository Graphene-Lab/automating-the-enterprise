# 7. One File and a Double Click

The spare desk at Riverton faced a window that looked onto the yard where the vans were loaded.
Maggie had cleared it herself, which is to say she had moved four boxes of catalogues onto the
floor and wiped the desk with a cloth that was not quite clean. On it she put a laptop, a mug, and
a sheet of paper with three lines written on it.

Sam Okafor looked at the paper.

"That's it?"

"That's it."

The three lines were: *company name, admin email, admin password*. Everything else, she had
decided, the machine could work out for itself.

---

Before the double click, there are four things a company should check, and none of them is
technical.

**A computer that is not doing anything else.** The stack runs three programs at once—the
database, the ERP and the assistant—and on a busy laptop they will compete with whatever else is
open. Riverton used a machine that had been bought for the web shop and never used for it. Eight
gigabytes of memory is enough; sixteen is comfortable; the disk wants about twelve gigabytes free
before the installer will start, and it checks.

**An internet connection, once.** The installer downloads the parts it needs. After that, the
system works without a connection, except for the language model, which is a service in another
building (or on another machine of your own, if you prefer).

**Permission to install.** On Windows the database engine installs a service, and that needs
administrator rights. If the account you use does not have them, the installer says so at the end
rather than failing silently, and a second run with the right account finishes the job.

**A company name.** Not the legal name, necessarily—the name you want to see at the top of your
invoices. Riverton used "Riverton Office Supply", which is what its customers call it.

That is the whole list. There is no database password to invent, no port to choose, no
configuration file to edit. The installer assigns the database's superuser password itself, prints
it at the end, and picks a free port if the standard one is taken. The AI provider is asked for
later, by the assistant, on its first start—where a key can actually be tested against the service
that issued it.

---

The file is called `install.bat`, and it is one of the few genuinely good ideas in the history of
business software distribution: a single text file, small enough to email, which knows how to fetch
everything else.

Maggie double-clicked it. A black window opened, with a title bar that said *OdooTool installer*,
and the first thing it did was ask a question.

Not a technical question. It printed four headings—*Questions*, *Free space*, *Checking
PostgreSQL, Python and Git*—and under *Questions* it listed what it was going to ask. On an
unattended run there was nothing to type, because the three answers were in the environment; on an
ordinary run it would have asked for the company name and nothing else.

There is a design decision hidden in that order, and it is worth noticing because it is the
difference between an installer people trust and one they abandon. The headings come *before* the
work: the installer tells you what it is going to ask, then what it found, then what it is going to
do. Nothing is discovered halfway through, when it is too late to change your mind. A person who
reads the first screen knows the shape of the next forty minutes.

The window itself is deliberately plain—white text on black, no progress bars, no logo, no
animation. That is not laziness. A console window that prints one line per real event is a window
whose output can be *read*, copied into an email, and compared with somebody else's run. The
installers that hide their output behind a spinning circle are the ones that cannot be diagnosed
when they stop.

The second heading was the disk: *Free space on C: 79.53 GB*. The installer refuses to start below
twelve gigabytes, which is a decision made by somebody who has watched an installation fail at
ninety per cent and had to explain why.

The third heading produced two lines that are worth understanding, because they are the sort of
thing that makes people think a computer is broken.

```
! TCP port 5432 is already in use on this PC; the new PostgreSQL will listen on 5433 instead.
PostgreSQL is not installed. It is installed now with the 'postgres' superuser password set to 'odoo'.
```

The first line is not an error. It is a report of something ordinary: another program on the
machine—in this case a database inside Windows Subsystem for Linux, forwarded to the Windows side
by a small helper called `wslrelay`—was already using the standard port for PostgreSQL. Ports are
numbered doors, and only one program can listen behind each door. The installer looked for the
first free door after 5432, found 5433, and decided to use it for everything: the database, the
ERP, and the launcher. Nobody has to remember the number; the installer writes it where it needs
to be written.

The second line is the installer saying what it is about to do, and—this is the part that matters
to a small company—that it is going to choose the database password itself. The password is
`odoo`, it is a local account on this PC, and it has nothing to do with any account on the
internet. The installer prints it at the end so that the owner of the machine can find it later.

---

Then the waiting started, and the waiting is where this chapter earns its place in the book,
because the first attempt failed.

The installer tried the Windows package manager first, which is the polite way to install software
on Windows. The package manager could not reach its source—a corporate network, a hotel network or
an antivirus product will do that—and returned an error. The installer said so, in one line, and
fell back to downloading the database's official installer directly. That is the correct behaviour,
and it is why the next thing on the screen was a download.

The download was slow. Not "a little slow": sixty kilobytes a second, on a line that had been
measured at four hundred. The database installer is three hundred and eighty-six megabytes, which
at that speed is an hour and three quarters, and the connection dropped three times before the file
was complete. Each drop started the transfer again from zero, because that is what the code did at
the time, and after the third attempt the installer gave up and printed the sentence that sends
people to a support forum:

> PostgreSQL could not be downloaded (winget and the direct download both failed). Install it
> yourself from enterprisedb.com and run this installer again.

This is the first genuine fault in this book, and it is worth being precise about what was wrong,
because it was not the network.

The installer already used `curl`, which can resume a partial transfer. But it deleted the partial
file before each attempt, so the resume had nothing to resume. On a fast connection nobody would
ever notice. On a slow one, it turned a thirty-minute download into three half-hour failures.

The fix is three lines of thinking and a dozen lines of code: keep the partial file, name it after
the version it belongs to so it can never be confused with another, and ask `curl` to continue
from where it stopped (`-C -`). A file that is already the right size is reused without a
transfer at all, and a file that is *larger* than the declared size is thrown away, because it
cannot be a prefix of the real one.

With that change, the second run of the installer printed a single line and moved on:

```
==> reusing the verified download of 16.16-1
```

That line is the whole difference between a product and a prototype. The first version asked the
user to solve a network problem. The second version solved it and said so in seven words.

While the database was installing—three hundred and ninety megabytes to unpack, which takes a few
minutes on an ordinary disk—the installer printed nothing, because there was nothing to print. It
was waiting for the database's own installer to finish, and the database's installer is silent by
design. A progress bar would have been nicer. Silence, at least, was honest.

---

The database finished. The installer checked that it could reach it, with the password it had
assigned, and printed a line to say so. Then it turned to Python.

Python is the language Odoo is written in, and the installer's approach to it is the approach of a
good colleague: if a usable version is already there, use it; if not, install one. On Windows this
is more delicate than it sounds, because the `python` command on a modern machine is often not
Python at all but a Microsoft Store advertisement—a small shim that opens the Store when you type
`python`. An installer that trusts the command will install nothing and then fail mysteriously
later. This one runs it and checks the answer, which is the only reliable test.

Then it fetched Odoo itself—a copy of the source for the version being installed—and the Python
packages it needs, and created the database, and loaded the base modules. Each of those steps
prints a line, and each line is a small piece of reassurance: *this is still going, and it is
going in the right direction.*

The last step was the assistant: download the public release, unpack it, install the connector that
lets it talk to the ERP, write the address of the ERP and a freshly generated key into the
connector's configuration, and start the ERP.

Then the window printed a summary. It is worth quoting, because it is the only part of the
installation that a user must keep.

```
==> Done

Odoo:          http://localhost:8069
Administrator: admin@riverton.example
Password:      OdooDemo2026
Database:      odoo on port 5433
Assistant:     AI Odoo (desktop icon)
```

Three of those lines are the ones Maggie wrote on the sheet of paper and put in the drawer with the
napkin: the address, the user, the password. The fourth is the port, which she did not need to
know, and the fifth is the icon she would double-click every morning for the next year.

## What the installer will not do

It is worth saying plainly what the script leaves to you, because a company that expects the
installer to produce a working business will be disappointed in an hour.

It will not **choose your chart of accounts**, beyond installing the one your country uses. The
accounts your company actually needs—carriage charged, carriage paid, the two or three expenses that
matter—are a conversation with your accountant.

It will not **enter your products, customers or stock**. Those are the facts of your business, and
nobody else has them.

It will not **decide who may do what**. It creates the administrator and the assistant's user; the
rest is a judgement about your people.

It will not **configure the AI provider for you** beyond writing the address and the key you gave it
in advance; on an ordinary run, the assistant asks on its first start.

And it will not **back up your data**, because at the moment it runs there is no data to back up.
That is the first thing to set up afterwards, and chapter eight explains how.

The installer's job is narrow and it does it well: it puts the three machines in the room, wires them
together, and prints the three facts you need to log in. Everything after that is the work this book
is about.

---

There is a small piece of theatre at the end which is easy to miss and which tells you something
about the people who wrote the installer. Having finished, it opens the ERP's first-steps page in
the browser. Not the assistant, not a marketing page: the page where a new company is asked what
currency it uses, what its chart of accounts should look like, and what it sells.

The message is: you are not finished, you have just arrived. The next hour is configuration, and
it is the hour that decides whether the system becomes the truth or becomes another abandoned
program. The installer cannot do that part for you, and it does not pretend to.

Maggie sat in front of the first-steps page for a long moment. Then she called Doreen, because the
chart of accounts was going to be an argument, and it was better to have the argument with the
person who had been keeping the books for thirty-one years than to have it with a consultant.

That conversation is the next chapter.
