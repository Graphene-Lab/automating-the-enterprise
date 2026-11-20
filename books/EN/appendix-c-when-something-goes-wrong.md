# Appendix C — When Something Goes Wrong

This appendix is organised by symptom, because that is how trouble arrives. Each entry says what
you will see, what it usually means, and what to do. The entries marked *seen* are failures that
occurred during the writing of this book, on the installation that produced its screenshots; they
are not hypothetical.

Before anything else, one habit. When something goes wrong, do not reinstall. Read the last twenty
lines of the log, and look at which of the three boxes on the napkin is unhappy: the memory (the
database), the model (the ERP), or the assistant. Nine times out of ten the answer tells you what
to do, and reinstalling destroys the evidence.

---

## The installer stops with "psql was not found"

**What you see.** The installer reports that PostgreSQL is not installed, tries `winget`, then tries
to download the official installer directly, and finally stops with a message saying that `psql`
was not found and that nothing after that step would work.

**What it means.** PostgreSQL is not on the machine. The installer tried to install it and could
not: either `winget` failed to reach its source, or the download from the vendor's site did not
finish. On a slow or unstable connection this is the most common failure of the whole procedure.

**What to do.** Run the installer again. It continues where it stopped and reuses what is already
there; a partial download is resumed rather than restarted, so each attempt gets further than the
last. If you are on a connection slower than about half a megabit per second, download the
PostgreSQL installer yourself, with a browser, from the vendor's site, and place it in the folder
the installer reports; the next run will find it and use it. If you would rather install PostgreSQL
by hand, any 16.x release works, and the installer will detect it on the next run—including its
port, which it reads from the server's own configuration file.

*Seen during the writing of this book:* the first run failed at exactly this point, after three
download attempts, on a connection running at about sixty kilobytes per second. The second run
resumed the partial file and completed.

---

## "TCP port 5432 is already in use"

**What you see.** Early in the run, a warning that port 5432 is taken and that PostgreSQL will
listen on 5433 instead.

**What it means.** Something else on the machine is using the standard database port. Very often it
is a database inside Windows Subsystem for Linux, forwarded to the Windows side, or a Docker
container.

**What to do.** Nothing. The installer chooses the first free port and carries it through the whole
stack—the database role, the database, the ERP and the launcher. This is not an error; it is the
installer doing the right thing on a busy machine. Write the port down if you plan to connect to
the database with other tools.

---

## `winget` cannot install anything

**What you see.** A message that `winget` exited with a connection error, followed by the installer
falling back to a direct download.

**What it means.** The package source could not be reached. Corporate networks, hotel networks and
some antivirus products interfere with the Windows Package Manager.

**What to do.** Let the fallback do its work. If both routes fail, install the component by hand
(PostgreSQL and Python are the only two the installer needs from outside), then run the installer
again.

---

## The page that opens is not the login page

**What you see.** You double-click **AI Odoo**, or open `http://localhost:8069`, and the browser
shows something that is not the white login card: a page about Odoo, a website with a placeholder
logo, or a list of databases.

**What it means.** The address you asked for is not the address of your ERP, or it is an address
that several things can answer. There are exactly three cases, and each has its own cause.

*It is Odoo's own documentation, on odoo.com, in the language of your browser.* That is a page about
the product, not about your machine: nothing on it is your data and it is not part of the
installation. It is what an earlier version of the installer opened at the end, and it is still
printed at the end as a link for later reading. Close it and open the start page from the icon.

*It is a website with a logo you did not choose, a menu and a "Sign in" link in a corner.* That is
Odoo's **website** application: a module that serves a public site at the root address. Once it is
installed, `http://localhost:8069` shows the site instead of the login page, and the ERP hides
behind the small sign-in link. Nothing is broken and no data is lost. The login page has its own
address, and it always works: `http://localhost:8069/web/login?db=odoo_agent`. The start page and
the icon use that address for this reason.

*It is a list of databases, or a form asking which database you mean.* The machine holds more than
one Odoo database—a test copy, an older installation—and the address did not name one. Add
`?db=odoo_agent` to the address, or use the start page, which names it.

---

## The login and password printed at the end do not work

**What you see.** The credentials in the installer's summary are rejected, and the login page says
the username or password is wrong.

**What it means.** On a first installation the installer creates the administrator and prints what
it created, so the two agree. On a second run the account already exists, and it keeps the login and
password it had: printing a newly invented password there would be printing a password that was
never applied. The installer now reads the account back from the database and says either the
password it set, or that the password is unchanged since the first installation.

**What to do.** If the summary says *unchanged*, use the password from the first installation. If it
is lost, set a new one deliberately: run the installer again with `ADMIN_PASS` set in the
environment, and it will apply and print that password. Nothing else in the database is touched.

---

## The black window disappeared

**What you see.** Odoo still answers in the browser, but there is no window to type in.

**What it means.** The black window *is* the assistant: closing it stops the assistant, and only the
assistant. The ERP runs as a separate program, which is why the browser keeps working.

**What to do.** Double-click **AI Odoo** again. It starts what is missing and does not start a
second copy of what is already running.

---

## The ERP does not answer on its port

**What you see.** After the installation, the browser cannot reach the address printed at the end
(the default is `http://localhost:8069`), or the launcher opens a blank page.

**What it means.** The ERP process is not running, or it started and then stopped because of an
error in its own log.

**What to do.** Open the file called `odoo.log` in the folder the installer created (by default
under your local application data, in `odoo-tool-stack`). The last lines say why. The three common
causes are: the database service is not running; the database password in the configuration no
longer matches the database; and the port is taken by another program. All three are fixable
without reinstalling.

---

## The assistant answers, but cannot find the ERP

**What you see.** You ask "list the customers" and the assistant replies that it cannot connect, or
that the configuration is missing.

**What it means.** The assistant's connector has no address, no key, or a key that the ERP no
longer accepts. The connector reads its settings from the environment or from a small file in the
assistant's data folder.

**What to do.** Check that the ERP is running and reachable in a browser first. Then check the key:
in the ERP, open the user menu, go to the account security page, and create a new API key. Paste it
into the connector's configuration. If you changed the ERP user's password, existing keys usually
survive; if you deleted and recreated the user, they do not.

---

## The assistant creates a duplicate customer

**What you see.** Two customers called almost the same thing: "Ashfield Academy" and "Ashfield
Academy Ltd."

**What it means.** The assistant was asked to create a customer and did what it was told. It does
not automatically decide that a similar name is the same company, and it should not: two branches
of the same organisation can legitimately be two records.

**What to do.** Phrase the instruction to search first—"find the customer Ashfield and add a
contact"—or ask the assistant to show you the matches before creating anything. When a duplicate
does appear, merge or archive it in the ERP rather than deleting it, so that the history of
invoices stays intact.

---

## A document cannot be posted

**What you see.** The ERP refuses to post an invoice, or a delivery, and shows a message about a
missing account, a missing tax, or a period that is closed.

**What it means.** The model is incomplete. A product has no income account, or the company has no
tax configured, or the accounting period has been locked.

**What to do.** Read the message; it names the field. Fix the configuration in the ERP's settings,
then post again. This is the ERP doing its job: it refuses to write an entry that Pacioli would not
recognise.

---

## Everything is slow

**What you see.** Screens take seconds to load; the assistant takes a long time to answer.

**What it means.** Two different things, usually confused. If the ERP screens are slow, the problem
is local: the database, the disk, or the machine's memory. If only the assistant is slow, the
problem is the language model—either the remote service, or the local model if you run one.

**What to do.** Look at the machine's memory and disk first. Then look at the assistant's log: it
records how long each request took and which tools were called. A single request that takes thirty
seconds because it made twelve tool calls is not a fault; it is a request that should have been
phrased more narrowly.

---

## You have lost the administrator password

**What it means.** The password printed at the end of the installation was not written down.

**What to do.** On a self-hosted installation you are the owner of the machine, so you can reset it
from the database. Stop the ERP, connect to the database with the database's own administrator
account, and set a new password hash for the administrator user. The procedure is documented in the
ERP's own documentation under "reset the administrator password", and it takes two minutes. Do not
delete the database to solve a password problem.

---

## The one rule

Whatever happens, keep two things: the log file, and a copy of the database from before the
change. With those two, almost any problem can be diagnosed and most can be undone. Without them,
every problem becomes an argument about what used to be true.
