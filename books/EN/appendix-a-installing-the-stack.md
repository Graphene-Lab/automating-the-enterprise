# Appendix A — Installing the Stack, Step by Step

This appendix is the installation without the story: the same procedure as chapter seven, written
as a list you can follow with the book closed. It assumes Windows 10 or 11; the Linux procedure is
the same script with a different name, and the installer is designed to behave identically.

## Before you start

| Requirement | Why | How to check |
|---|---|---|
| Windows 10 or 11, 64-bit | the database engine and the assistant are Windows programs | Settings → System → About |
| About 12 GB of free disk | database, ERP source, Python packages, assistant | File Explorer → This PC |
| An administrator account | the database installs a Windows service | the installer says so at the end if it lacks the right |
| An internet connection | the parts are downloaded once | any browser |
| A company name | it appears on your documents | decide it now |

You do **not** need: a database password, a port number, .NET, Git, Docker, a Python installation
or any command-line knowledge.

## Step 1 — Get the installer

Download `install.bat` from the OdooTool releases page and put it in an empty folder, for example
`C:\Users\<you>\Downloads\odoo-install\`.

The file is a few kilobytes. It downloads the rest of itself if it has to, so it works even when it
arrives alone.

## Step 2 — Run it

Double-click `install.bat`. A console window opens with the title *OdooTool installer*.

If Windows asks for permission to make changes, allow it: the database needs to register a service.

## Step 3 — Answer the questions

On a normal run the installer asks for the **company name** and accepts the suggested default for
everything else by pressing Enter. On an unattended run the answers can be given in advance through
environment variables, and the installer asks nothing at all.

The installer prints a heading called *Questions* with the answers it is going to use, so you can
see what it decided before it starts working.

## Step 4 — Watch the four stages

The screen prints one heading per stage. Each heading is followed by lines that say what is
happening; nothing needs to be typed.

1. **Free space.** It refuses to start below twelve gigabytes.
2. **Checking PostgreSQL, Python and Git.** It reports what it found and what it will install.
3. **Installation.** The long part: the database, the Python runtime if needed, the ERP source, the
   Python packages, the database itself, the assistant, the connector.
4. **Summary.** Addresses, credentials and what is still missing, if anything.

Two messages during stage 2 are normal and are not faults:

- *TCP port 5432 is already in use; the new PostgreSQL will listen on 5433 instead.* Something else
  on the machine holds the standard port. The installer picks the next free one and uses it
  everywhere.
- *PostgreSQL is not installed. It is installed now with the 'postgres' superuser password set to
  'odoo'.* The password is assigned by the installer, is local to this PC, and is printed at the
  end. Nothing has to be remembered or looked up.

## Step 5 — If the download is slow

The database installer is about 390 MB and comes from the vendor's own site. On a slow line the
download can take an hour or fail. The installer keeps the partial file and resumes it on the next
run, so **running it again is the correct response**—it continues where it stopped and reuses what
is already there.

If the machine cannot reach the vendor at all, download the PostgreSQL 16 Windows installer
yourself from enterprisedb.com, leave it in the folder the installer reports, and run `install.bat`
again. It will find it and verify its size before using it.

## Step 6 — Keep the summary

At the end the window prints something like this. Write it down, or photograph the screen.

```
  Odoo (the ERP, in the browser):  http://localhost:8069
  Login: admin@yourcompany.example
  Password: (the one the installer generated, or the one you gave it)
  Assistant (talk to it here):  http://localhost:5290/OfficeManager
```

If the administrator account already existed from an earlier run, the installer prints the login
that really is in the database and says the password is unchanged, rather than inventing a new one
that would not work.

The browser opens the **start page**: a file on this computer with the address, the account and two
links. That page is the beginning of the configuration, not the end of the installation.

## Step 7 — The icon, and the three windows

Double-click the **AI Odoo** icon on the desktop. Three things happen:

1. the ERP starts, if it was not running;
2. the start page opens in the browser;
3. the assistant opens in its own black window.

*Open Odoo* on the start page goes to the login page at
`http://localhost:8069/web/login?db=odoo_agent`. The assistant is the black window, and that is
where you type; it should stay open while you work, because closing it stops the assistant, while
Odoo keeps running.

On its first start the assistant asks for the AI provider: choose the service, paste the key, and
it fetches that service's list of models. Nothing else is needed—the address of the ERP and the
access key were written by the installer.

## Step 8 — Check that it works

Three checks, in order, and each one tells you which of the three machines is unhappy if it fails.

1. **The ERP.** Click *Open Odoo* on the start page, or open
   `http://localhost:8069/web/login?db=odoo_agent` in a browser, and log in. If the page does not
   load, the ERP or the database is not running; the file `odoo.log` in the installation folder says
   why.
2. **The connector.** In the assistant, ask: *check the connection to Odoo and tell me which version
   is running.* A version number means the key and the address are right.
3. **The model.** Ask: *how many customers do we have?* A number means the assistant can read the
   ERP's data as its user, with that user's permissions.

If all three answer, the installation is complete.

## Uninstalling

Two scripts undo the installation, and they are the supported way: `uninstall.bat` on Windows and
`uninstall.sh` on Linux. They sit next to the installer in the same release, and each can be
downloaded and run on its own.

What they remove:

- the Odoo database, with every customer, product, order, invoice and stock move in it;
- the installation folder (`%LOCALAPPDATA%\odoo-tool-stack`, or `~/odoo-tool-stack`);
- the **AI Odoo** shortcuts and the firewall rule.

They ask twice, and the second question is not a formality. The first is a yes/no that lists what
disappears. The second requires the phrase **DESTROY ALL**, typed in capital letters. If the phrase
is not exact, nothing is touched—not one file, not one row. The deletion is irreversible and the
uninstaller makes no backup, so a copy of the database taken beforehand is the only way back.

AgentBridge is asked about separately, because it can host other tools and holds its own settings
and API keys: answering *no* keeps it and removes only the Odoo half.

PostgreSQL is left installed. It is a service other programs may share, and it is removed from
*Apps & features* like any other program, once nothing else needs it. The `odoo` database role stays
behind and is harmless: a future installation reuses it.
