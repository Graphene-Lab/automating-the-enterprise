# 23. The Office Down the Corridor

The assistant has two front doors, and most companies use one of them for a month before they
discover the other.

The first is the terminal window: black background, a prompt, and the answer underneath. It is the
door this book has been using, because it is the one that shows the work—the tool calls, the
intermediate steps, the log. It is a workshop.

The second is a web page, at `http://localhost:5290/OfficeManager`, and it is not a workshop. It is
an office.

---

## What the page shows

The page draws a small room. There are desks, a door, a plant, and several little figures who walk
around, sit down, get up, and occasionally gather at the water cooler. One of them is your agent.
Below the room there is a chat box.

![The office: one room, one worker, and a chat box at the bottom](../../assets/screens/assistant-01-office.png)

When an instruction arrives, a figure appears at the door and takes a desk, the panel on the right
shows what it is doing—*get context*, *search*, *create*—and the chat log records the exchange.

![The instruction as it arrives: the agent has taken a desk and is working](../../assets/screens/assistant-02-prompt.png)

If that sounds whimsical, it is—and it is also the most effective interface for this kind of work
that Riverton tried. The reason is worth understanding, because it is not about cuteness.

A terminal window shows *one conversation at a time*, and it shows everything: every tool call,
every intermediate result, every line of reasoning. That is exactly what you want when you are
building or debugging a job. It is exactly what you do not want when you are an office manager with
a customer on the telephone.

The office page shows *one thing*: the agent, and whether it is busy. The figures walk when the agent
is thinking and sit when it is idle. You can see, from across the room, whether the assistant is
working—which sounds trivial and is in fact the single most useful piece of information in the whole
system.

"You can tell if it's busy without reading anything," Priya said. "In the terminal I have to look at
the last line. Here I just look."

## When to use which

After a month, Riverton's habits settled into a simple division.

**The terminal for anything that touches money or changes a document.** Creating an invoice, posting
a bill, confirming an order. The reason is not that the web page cannot do it—it can—but that the
terminal shows the *steps*, and a person who can see the steps can stop them. On the terminal, you
watch the assistant search for the customer, read the product, create the document, and you can see
the moment it goes wrong. On the web page you see a bubble saying "done", and you have to trust it.

**The web page for questions and sweeps.** *How many overdue invoices do we have? Which products are
low? What did we sell last week?* Nothing is changed, the answer is short, and the office metaphor
makes the whole thing feel like asking a colleague rather than operating a machine.

**The web page for anybody who is not Maggie.** Tom uses it, Priya uses it, and Doreen—after some
resistance—uses it. The terminal is intimidating in a way that has nothing to do with the work: it
looks like the inside of a machine, and most office staff have been taught, over thirty years, that
the inside of a machine is not for them. The office page looks like a place where somebody works.

That last point is not decoration. It is the difference between a tool that four people use and a
tool that one person uses on behalf of four.

## The little people

The figures in the office are not avatars of the staff. They are *agents*: the installation can run
several, each with its own job, and the page shows them all. Riverton runs one, because the machine
has one model and one graphics card, and parallel agents on one machine do not add speed—they take
turns, and they can exhaust the memory.

The page is honest about this if you look: the figures share the room, and the room has one
telephone. Two agents trying to answer it at once is not a feature.

There is a temptation, when you see the office, to populate it—to give each department its own
little figure with its own instructions. It is a bad idea for a small company, and the reason is the
same one that runs through this whole book: an agent is only as good as the model behind it, and one
model answering four conversations is four slow conversations. The office is a window onto one
worker, not a staff.

## The third door, which is not a door at all

There is a third way in, and it is not a screen: the assistant answers HTTP requests.

On the same machine, at `http://localhost:5290/v1/chat/completions`, it speaks the same protocol as
the big cloud services. Anything that can talk to an OpenAI-compatible endpoint can talk to it—a
script, a spreadsheet macro, another program, a telephone system, a website's contact form.

Riverton has not used this, and it is worth explaining why, because the temptation is strong and
the risk is subtle.

The temptation is obvious: a customer emails an enquiry, the website forwards it to the assistant,
the assistant creates a customer record and a draft quotation, and Priya finds the work done when
she opens her screen. That is a real workflow, and it is exactly the kind of thing this technology
is good at.

The risk is that every door into the system is a door, and the door at `localhost:5290` is open to
anything running on the machine—including a browser tab that has been tricked into making a request.
The API has no authentication by default, because it was designed to be reached from the same
machine by programs the owner controls. That is a reasonable design for a workshop. It is not a
reasonable design for a company that will one day connect it to the internet.

The rule Riverton adopted, and the one this book recommends: **the API stays on the machine until
somebody has a specific need and a specific plan.** When that day comes, the plan is three lines
long—put it behind a proxy that requires a token, limit it to one endpoint, and log every request.
Until then, two front doors are enough, and both of them have a person at them.

## Tom's afternoon

The day the office page earned its place in the company was a Thursday in February, and the story
is small.

Tom was in the warehouse with a clipboard, doing the quarterly count, and he needed to know whether
a pallet of paper had been received against an order or was still "in transit" in the system. On the
terminal, that question means walking to the office, sitting at the machine that runs the assistant,
and typing. On the office page, it means opening a browser tab on the warehouse laptop—which is a
cheap machine that exists to look up product codes—and typing the question there.

*Is the pallet of A4 paper from Pennine on order P00008 received yet?*

*Received: 40 reams on 12 November, validated by Tom Beck, stock move WH/IN/00031. The order is
fully received; the bill has not been created yet.*

He had his answer in nine seconds, standing next to the pallet. The old version of that answer was a
walk to the office, a conversation, and a note on a clipboard.

This is the least dramatic benefit in the whole book and possibly the most important: the distance
between a question and its answer, measured in footsteps. A warehouse that can ask the system
something without leaving the warehouse is a warehouse that checks things.

## What the office cannot do

Three limits are worth knowing before a company builds a habit around the page.

**It cannot run two conversations at once, usefully.** The office draws several figures, and the
temptation is to hire one per department. On a machine with one model, that is four conversations
taking turns, and the figures will sit at their desks looking busy while nothing finishes. The page
is honest about this if you watch it: the panel on the right lists the sessions, and only one of
them is *working* at any moment.

**It cannot show you the reasoning.** The terminal shows the tool calls as they happen; the office
shows a label (*search*, *create*, *get context*) and then an answer. That is the right level of
detail for an office manager and the wrong level for somebody debugging a job. The two entrances
are not interchangeable, and a company that uses only the web page will eventually need the
terminal—usually on the day something goes wrong.

**It cannot be left open on a screen in a public room.** The chat shows the company's data: names,
amounts, invoices. A laptop on a desk in a shop is a window into the ledger. The page has no login
of its own, because it is served by the assistant on `localhost` and assumes the machine is yours.
That assumption is correct at a desk and wrong in a reception area.

## The sound, and the switch that turns it off

The page plays small noises: a keyboard when the agent is typing, a bell when a job is done. It is
charming for a week and maddening for a month, and the switch is in the bottom-right corner of the
page, labelled *SOUND: ON*.

The fact that this is worth a paragraph is itself a lesson about office software. The features that
decide whether a tool survives are rarely the ones in the brochure. They are the ones that touch
the office's nerves: whether it makes noise, whether it can be left open, whether the thing it shows
is true.

## A short history of the office metaphor

Putting people in a picture to represent work is an old idea in computing, and it has a good record.

In 1984, Apple's Macintosh introduced the desktop metaphor—files, folders, a wastebasket—and it
worked because it let people use knowledge they already had. In 1987, the Information Visualizer
project at Xerox PARC went further and drew offices, with rooms and documents, as a way of navigating
large information spaces. In 1993, the game *Doom* taught a generation that a first-person view of a
space is more legible than a diagram of it.

What all three discovered is the same thing: **a spatial metaphor carries state**. You do not have to
read a status line to know that a room is busy; you can see it. The office page at Riverton is a
direct descendant of that idea, and it exists for the same reason—not to be charming, but to answer
the question *what is happening?* without requiring the user to read.

## The chat, and the same discipline

The chat box at the bottom of the page takes the same instructions as the terminal, and produces the
same work. Everything in chapter twenty-five about prompts applies unchanged.

Two things are different, and both are consequences of the interface.

**Answers are shorter.** The web page shows a conversation, not a log, so the assistant summarises.
That is good for reading and bad for checking: the invoice number may be in the summary, but the list
of steps that produced it is not. When a result matters, ask a follow-up—*show me the documents behind
that number*—and the answer will be a list.

**The temptation to multitask is stronger.** A chat window invites a second question while the first
is still running, and a second question while the first is running is the thing that makes a
single-model installation feel broken. The page does not prevent it. The habit does.

---

Maggie's own use settled into something she did not expect: she uses the web page in the morning and
the terminal in the afternoon.

"In the morning I want to know things," she says. "I want the list of what's late, what's low, what
came in overnight. That's a conversation, and the office is where I have it. In the afternoon I want
to *do* things—post the invoices, chase the three accounts, fix the thing Tom found—and for that I
want to see the wheels turn."

She thought about it for a moment.

"It's like the difference between asking somebody a question in the corridor and sitting down with
them at a desk. Same person. Different room."

That is as good a description of the two interfaces as this book can offer, and it suggests the
principle behind them: the interface should match the *kind of attention* the work requires, not the
kind of technology behind it. A question needs a conversation. A posting needs a witness.
