# 8. What Happened While the Bar Moved

The installation took forty minutes, most of which was spent looking at a screen that did not
change.

This chapter is what happened during those forty minutes, explained for somebody who will never
need to do it by hand but who deserves to know what is now running on the machine—because a system
you do not understand is a system you cannot trust, and a system you cannot trust is a system you
will abandon in March.

There are five things to explain: the database, the Python environment, the ERP, the connector, and
the assistant. They live in one folder, and knowing that folder is knowing the installation.

---

## The folder

Everything the installer creates goes into one place:

```
%LOCALAPPDATA%\odoo-tool-stack
```

On a typical Windows machine that is `C:\Users\<you>\AppData\Local\odoo-tool-stack`. Inside it,
four subfolders, one per component, plus the log files. Nothing is scattered across the disk, no
files are put in `Windows`, and nothing is registered except the database service and two
shortcuts.

That is a deliberate design decision and it has one enormous practical consequence: **uninstalling
is deleting a folder.** A company that tries the system in January and abandons it in February
does not leave a fossil in the machine for the next five years. It deletes a directory and
uninstalls the database.

The user's own data—the assistant's settings, its conversations, the connector's configuration—lives
separately, in `%LOCALAPPDATA%\agent`, so that updating or reinstalling the stack does not destroy
it.

## The database

PostgreSQL is installed the way PostgreSQL is meant to be installed on Windows: as a service, with
a data directory of its own, listening on a port. The service means it starts with the machine and
runs without anybody logging in; the data directory means the company's memory is a set of files
in a known place, which is what makes a backup possible.

The installer chose the port. It wanted 5432, found it taken by the database inside Windows
Subsystem for Linux, and took 5433. Then it did three things that a person would otherwise have to
do by hand:

1. It created a database user called `odoo`, with a password, so that the ERP never connects as the
   superuser. This is the difference between giving the accountant a key to the office and giving
   her the master key to the building.
2. It created a database called `odoo`, owned by that user.
3. It wrote the port and the credentials into the ERP's configuration file.

The superuser password is `odoo` unless the person installing chose otherwise, and the installer
prints it in the summary. It is a local account. It has nothing to do with any account on the
internet, and it is the password you will need if you ever have to restore a backup by hand.

## The Python environment

Odoo is written in Python, and Python programs need libraries. The installer creates an isolated
environment—a *virtual environment*—inside the stack folder, and installs into it exactly the
libraries Odoo needs, at the versions Odoo expects.

The word "isolated" is doing real work here. Without it, installing Odoo would change the Python
that other programs on the machine use, and one day something unrelated would stop working. With
it, the stack carries its own Python and cannot break anything outside its folder.

If the machine had no usable Python at all, the installer installed one first—and it checked by
running it, not by looking for it, because on a modern Windows machine the command `python` is
often an advertisement for the Microsoft Store rather than a program.

## The ERP

Odoo itself is a folder of Python source and a large set of modules. The installer fetched the
version being installed, created the database schema, and loaded the base modules—the ones that
provide the model of a company: partners, products, documents, the ledger, the web interface.

This is the step that takes the longest and looks the most like nothing happening. A database is
being built: hundreds of tables, thousands of rules, the chart of accounts of a generic company,
the taxes of a generic country, the menus of a generic user. When it finishes, the ERP is a working
program that knows how to be a company but does not yet know which company it is. That is what the
first-steps page is for.

## The connector

The connector is the small program that translates between the assistant and the ERP. It is
installed as a plugin—a folder of files the assistant loads at startup—and it is configured with
two facts: the address of the ERP (`http://localhost:8069`) and a key.

The key is generated during the installation and written into the connector's configuration. It is
an Odoo API key: a credential that belongs to a user, can be revoked without changing that user's
password, and carries that user's permissions. When the assistant asks Odoo to create an invoice,
it is that key that travels with the request, and Odoo checks it exactly as it would check a
person's login.

This is the part of the architecture that a company's auditor will ask about, and the answer is
reassuring: the assistant is a *user*. It appears in the ERP's user list. It has a role. Every
record it creates is stamped with its name. It can be disabled in one click, and the audit trail
will still show what it did.

## The assistant

The assistant arrives as a public release: an executable, a folder of tools, and the desktop chat
client. The installer unpacks it, installs the connector into it, and creates the **AI Odoo**
shortcut.

The shortcut is the piece that makes the system feel like a product rather than a science project.
Double-clicking it starts the ERP if it is not running, opens the ERP page in the browser, and
opens the assistant in a terminal window. One icon, three windows, and the work can begin.

The assistant's own configuration—which AI provider, which model, which key—is asked for on its
first start, by the assistant itself, in the same terminal window where you will type your
instructions. That is a good place to ask, because it is the only place where the key can actually
be tested: the assistant fetches the provider's list of models with the key you pasted, and if the
list comes back, the key works.

---

## What could have gone wrong

Everything above worked on the second attempt. It is worth listing what went wrong on the first,
because each item is a place where a company installing this for real will lose an afternoon, and
each one was fixed rather than documented as a known issue.

**The download that started over.** Described in the previous chapter: the installer deleted its
partial download before each retry, so a slow line meant three failures instead of one slow
success. Fixed by keeping the partial file, naming it after its version, and resuming it.

**A version list that goes stale.** The installer knew the file names of three recent PostgreSQL
builds. The vendor had published a fourth, which was not on the list. A reader installing in six
months would have hit a list of files that no longer exist. Fixed by adding the current build and
by making the failure message say exactly which file to fetch by hand.

**The package manager's message in the machine's language.** When `winget` fails, it explains why
in the language of Windows. The installer repeated the last two hundred characters of that
explanation, and on a console whose code page is not UTF-8 the accented letters arrived as
rubbish—so the screen showed a fragment of Italian, mangled, in the middle of an English
installation. Fixed twice: the console is now set to UTF-8, and the installer no longer repeats the
package manager's text at all. The exit code is the fact; the next line says what happens instead.

**Silence during the database installation.** The database's own installer runs without output, so
the screen sits still for several minutes. This one is not fixed, because the fix would be to
invent a progress bar that lies. It is documented instead, here and in the appendix: if the screen
has not changed for five minutes, look at the folder `C:\Program Files\PostgreSQL`—if it is
growing, the installation is working.

None of these is dramatic. Together they are the difference between a procedure that a
non-technical person can complete on a bad connection and one that ends with a support ticket.

---

## The two files worth understanding

Inside the connector's folder there are two small files, and they are the only configuration a
company is likely to touch.

**`odoo.json`** holds the address of the ERP, the database name and the key. It is four lines of
text. If the ERP moves to another port, this is the file that changes; if the key is revoked, this
is the file that gets the new one.

**`toolset.json`** holds the list of tools the assistant is allowed to use. This is the file that
decides whether the assistant can touch a file, browse the web, or only talk to the ERP. It is the
single most important security setting in the whole installation, and it is one line of text.

Riverton's first week produced a lesson about that second file which is worth telling, because it is
the kind of thing that no manual predicts.

The installer had enabled four tools: the ERP connector, a file tool, a web tool and a version
control tool. That is a reasonable default for a general-purpose assistant. But the first
instruction the company gave—*create a customer called Ashfield Academy, Mill Lane, Ashfield*—was
answered by the assistant going to look the address up on the internet, because a web tool was
available and an address is a thing you look up.

It was not wrong, exactly. It was unhelpful, and it was slow, and it used a tool the company had not
thought about. The fix took one line: the toolset was cut to the connector and the file tool, and
the assistant stopped browsing and started asking the ERP.

That is a design decision every company has to make, and the default should be the narrow one. An
assistant with a tool it does not need is an assistant that will eventually use it, at the worst
possible moment, for a reason that seemed sensible to a language model.

## The shape of the thing

When the installer finished, Riverton had five programs where it used to have a filing cabinet.

A database, which remembers. An ERP, which knows what the facts mean. A Python environment, which
runs the ERP. A connector, which translates. An assistant, which acts. And a folder, which holds
all of it and can be deleted.

Maggie wrote the folder's path on the sheet of paper, under the password, and looked at it for a
moment. It was a strange feeling, to have replaced thirty-one years of paper with a directory in
her user profile—as if the company's memory had become a thing that could be copied onto a memory
stick in four minutes.

It could, in fact, be copied onto a memory stick in four minutes. That is what a backup is, and it
is the subject of a conversation she would have with Sam three weeks later, after the first scare.

But before backups, before invoices, before any of the work, there was a page in the browser asking
what currency the company uses.

---

## The first scare, and what a backup actually is

The scare came on a Thursday, three weeks in, and it was not a crash.

Maggie had asked the assistant a question—how much did we invoice last month?—and the answer was
smaller than she expected. Not wrong, exactly: smaller. She checked the invoice list, and there were
fewer invoices than she remembered approving.

The cause, when Sam found it, was innocent: Doreen had been experimenting with a filter in the
invoice list, and the filter had stayed on. The assistant had answered the question it was asked,
against the list it was given, and the list was filtered. Nothing had been deleted. Nothing had been
lost.

But for twenty minutes, Maggie had believed that three weeks of invoicing had disappeared, and the
feeling of that twenty minutes is what this section is about. Because the second question she asked,
before she asked Sam anything, was: *do we have a backup?*

The answer, that day, was: not really. There was a copy of the folder from the day of installation,
made by the installer itself, and nothing since.

What a backup is, in a system like this, is three things and not one.

**The database.** A dump of everything the ERP knows, taken with the database's own tool, on a
schedule. It is a single file, it can be restored into an empty installation, and it is the only
copy that matters for the ledger.

**The folder.** The ERP source, the configuration, the assistant's settings, the connector's key.
Small, and tedious to recreate by hand, which is exactly why it is worth copying.

**The check.** Once a month, restore the backup into a scratch installation and look at it. A
backup that has never been restored is a file with a hopeful name. Sam's rule—*an unverified backup
is a wish*—came from having watched a company discover, at the worst possible moment, that its
nightly job had been writing to a disk that was full.

The tools for all three are in the stack folder: a script that dumps the database, a folder to copy,
and a document with the four commands to restore. Riverton's version runs at two in the morning,
keeps thirty days, and writes to a folder that OneDrive synchronises. It took Sam an hour to set up
and it is, by a wide margin, the cheapest insurance the company has ever bought.
