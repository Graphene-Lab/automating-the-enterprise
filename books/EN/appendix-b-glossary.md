# Appendix B — A Glossary for People Who Do Not Program

Every word below is one that this book has used, or that somebody will use at you while you are
installing the system. The definitions are deliberately plain and occasionally imprecise; where a
precise definition would help a programmer and confuse an office manager, the plain one has won.

**Agent.** A program that can be given an instruction in ordinary language and can act on it—look
things up, create records, run a process—rather than only replying with text. In this book, the
agent is AgentBridge, the program you talk to in a terminal window.

**API.** Application Programming Interface. A documented way for one program to ask another
program to do something. Think of it as the service hatch of a restaurant: the kitchen does not
want you in the kitchen, but there is a proper way to hand in an order and receive a plate.

**API key.** The password that a program uses instead of a human. It is a long string of
characters, it is shown once, and it should be treated like a key to the safe: kept in a
password manager, never in an email, never in a document that gets forwarded.

**Backup.** A copy of the data taken at a point in time, kept somewhere other than the machine that
holds the original. An unverified backup is a wish; a backup you have opened and read is a backup.

**Database.** A program whose job is to store facts and give them back accurately, even when the
power fails in the middle of a change. In this book, PostgreSQL.

**Document (in an ERP).** Not a piece of paper: a record of something that happened or is going to
happen—an order, a delivery, an invoice, a payment—with a date, a party, a list of lines and a
state. Documents keep their own copy of the facts they were created with, so that last month's
invoice still shows last month's price.

**ERP.** Enterprise Resource Planning. Software that keeps the customer, the product, the order,
the stock, the invoice and the ledger in one connected model, so that a fact entered once is
visible everywhere. The name was coined by the analyst firm Gartner in 1990.

**Field.** One piece of information on a record: the customer's telephone number, the price of a
product, the date of an invoice.

**Journal entry.** The two-sided accounting record that every financial event produces: an amount
in one account and the same amount, opposite, in another. Invented long before software; codified
by Luca Pacioli in 1494; still the reason the books can be checked.

**JSON.** A way of writing data as text, so that one program can send it to another. You will only
ever see it in a log file, where it looks like a paragraph of punctuation.

**Language model (LLM).** A program trained on an enormous quantity of text, able to produce
plausible text in response to an instruction. It is good at language and unreliable at facts unless
it is *grounded*—that is, unless it is made to look the facts up instead of remembering them.

**MCP.** Model Context Protocol. An open standard, published by Anthropic in November 2024, that
lets a program describe the tools it offers to an assistant in a uniform way. It is why a tool
written for one assistant can be used by another.

**Model (in this book, two meanings).** 1. The representation of a company inside an ERP: parties,
products, documents, money. 2. The trained artefact behind an assistant: the "language model." The
context makes clear which; when it does not, the first meaning is usually the one that matters.

**Module.** A package that adds a capability to an ERP—accounting, inventory, manufacturing,
purchasing. Installing a module adds screens, records and rules; it does not change the underlying
data.

**Odoo.** An open-source ERP, started in 2005 under the name TinyERP, renamed OpenERP in 2008 and
Odoo in 2014. The Community edition is free; the Enterprise edition is licensed. Version 20, used
in this book, was released in September 2026.

**PostgreSQL.** The open-source database used by Odoo. It began as a research project at the
University of California at Berkeley in the 1980s and is now one of the most widely used databases
in the world.

**Prompt.** The instruction you type to the assistant, in ordinary language. A good prompt says
what you want, for whom, and by when; a bad prompt says "do the invoices" and hopes.

**Record.** One row in a table: one customer, one product, one invoice.

**Schema.** The list of tables and fields a database contains, and the rules about what may go in
them. When somebody says "the schema says a customer must have a name," they mean the database will
refuse to save a customer without one.

**Stock move.** The record of goods moving from one place to another: from a supplier to a
warehouse, from a shelf to a van, from a van back to a shelf because the school gate was locked.
The stock level of a product is the sum of its moves; it is never typed in directly.

**Token.** The unit in which a language model's work is measured. Roughly, a token is three
quarters of a word. Providers charge per token, which is why a very long document costs more to
process than a short question.

**Tool (in the context of an assistant).** One action the assistant is allowed to perform, with a
name and a description: *search customers*, *create an invoice*, *post a payment*. An assistant
without tools can only talk. An assistant with tools can work.

**Transaction.** A change that either happens completely or not at all. It is the promise that
makes a database trustworthy: there is no state in which half an invoice exists.

**Variant.** A version of a product that differs in one attribute—size, colour, voltage. One
product with twelve variants is not twelve products, and modelling it correctly is the difference
between a useful report and a useless one.

**Web interface (or web UI).** The screens you see in a browser. Odoo's web interface is where you
configure the company, look at records, and print documents; the assistant is a second way to reach
the same records.

**Workflow.** The sequence of states a document passes through—draft, confirmed, delivered,
invoiced, paid—and the rules about who may move it from one to the next. In a good ERP, the
workflow is the company's policy, written down and enforced.
