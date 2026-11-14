# Appendix D — The Prompt Index

Every instruction that appears in this book, in one place, with the chapter where it is used and
what it produces. It is meant to be scanned rather than read: find the question you have, and look
at the instruction that answers it.

The instructions are written as they were typed, in the language of an office. Names of customers
and products are Riverton's; substitute your own.

## Questions about customers

| Instruction | Produces | Chapter |
|---|---|---|
| How many customers do we have, and how many have placed an order in the last ninety days? | two numbers, with the second as the useful one | 13 |
| Find the customer called Ashfield Academy and show me their address, telephone number and payment terms. | the record, in the shape of a telephone call | 13 |
| Create a customer called Ashfield Academy, at Mill Lane, Ashfield, thirty days payment terms. | a new record, plus a duplicate check | 13 |
| Add a second contact to Ashfield Academy: Carol Whitfield, finance office, invoice contact. | a contact linked to the customer | 26 |
| Which customers have not ordered anything in the last six months, and what was their last order? | the quiet-customer list | 20, 26 |
| Show me the ten customers with the highest total invoiced amount this year. | a ranking with totals | 26 |
| Which customers owe us money and have also stopped ordering? | the risk list, annotated | 20, 26 |

## Quotations and orders

| Instruction | Produces | Chapter |
|---|---|---|
| Create a quotation for Ashfield Academy for 400 ring binders and 20 boxes of markers, at the contract prices, delivery end of next week. | a draft quotation with lines, tax and a date | 14 |
| Show me the quotation I created for Ashfield Academy today, with its lines and total. | the check | 14 |
| Change the binder quantity to 350 and confirm the order. | a confirmed order with reserved stock | 14 |
| Which orders are due for delivery in the next three days, and is the stock there for all of them? | a delivery plan with stock warnings | 14 |
| What is the total value of all quotations that are still open, and who are they for? | the pipeline | 26 |
| Which products did we sell most of last month, by quantity? | a ranking | 26 |
| Cancel the quotation for Northgate Library Service and tell me what state it is in now. | a cancelled document, with its state confirmed | 26 |

## Invoicing and money in

| Instruction | Produces | Chapter |
|---|---|---|
| Which delivered orders from this week are not yet invoiced? | the invoice run candidate list | 15 |
| Create invoices from every delivered order not yet invoiced, leave them in draft, and give me the list with totals. | the weekly run | 15 |
| Post the Ashfield Academy invoice and tell me its number and total. | a posted invoice with a sequence number | 15 |
| Which invoices are unpaid and more than thirty days old? | the ageing report | 20 |
| Register a payment of the full amount against invoice INV/2026/0007, dated today, by bank transfer. | a payment, matched | 17, 26 |
| Create a credit note for 20 ring binders returned damaged, and post it. | a credit note, with the original invoice intact | 15 |
| How much money is owed to us in total, and how much of it is overdue? | two numbers | 26 |
| Send a polite payment reminder to every customer with an invoice more than fifteen days overdue. | drafts, or sent mail, depending on configuration | 20 |
| Which customers are paying a price that has not changed since January, and what would it cost us to raise it by three per cent? | a pricing review | 14 |

## Stock

| Instruction | Produces | Chapter |
|---|---|---|
| How many ring binders do we have in stock right now, and where are they? | on hand, reserved, available, by location | 16 |
| Which products are below their reordering point? | the reorder list | 17, 22 |
| Confirm the delivery of the Ashfield Academy order and tell me which stock moves it created. | a validated delivery and its moves | 16 |
| Record a stock adjustment of minus 5 boxes of whiteboard markers, reason: damaged in the rain. | an adjustment with a reason | 26 |
| What is the total value of the stock in the warehouse at cost? | the stock valuation | 26 |
| Show me every stock move for the ring binders in the last thirty days. | the audit of one product | 16 |
| Which products have not moved at all in the last year? | dead stock | 26 |

## Buying

| Instruction | Produces | Chapter |
|---|---|---|
| Create a purchase order for 500 ring binders and 200 packs of markers from our usual suppliers, at the last price we paid, do not confirm it. | draft purchase orders, split by vendor | 17 |
| Confirm the purchase order and tell me when the goods are expected. | a confirmed order and an expected receipt | 17 |
| Receive the goods for the purchase order and show me the stock it added. | a receipt and its stock moves | 17 |
| Create the supplier bill for that purchase order and check it against the order and the receipt. | a bill, matched three ways | 17 |
| Which suppliers have raised their prices in the last six months, and by how much? | the creeping-price list | 17 |
| How much do we owe each supplier right now? | the creditor list | 26 |
| Which purchase orders are late, and by how many days? | the late-delivery list | 26 |

## Accounting

| Instruction | Produces | Chapter |
|---|---|---|
| Show me the trial balance for this month. | the oldest report in accounting | 19 |
| What is the balance of the bank account today, according to the books? | the book balance | 26 |
| The bank reconciliation has six unmatched lines. What are they? | six stories, one per line | 21 |
| Show me every journal entry posted in the last seven days, with the document they came from. | a trace from number to document | 26 |
| What is our revenue for this month so far, and how does it compare with last month? | two numbers and a comparison | 26 |
| List the taxes configured for this company and the rate of each. | the tax table | 26 |

## Reporting and analysis

| Instruction | Produces | Chapter |
|---|---|---|
| Give me a one-page summary of the business this week: sales, invoices, overdue money, stock alerts. | the Monday list | 22 |
| Which five products have the best margin, and which five the worst? | the margin ranking | 26 |
| Show me sales by month for this year, as a table. | a monthly series | 26 |
| What percentage of our invoices are paid late, and what is the average delay? | two measurements | 26 |
| Compare the number of orders this month with the same month last year. | a comparison | 26 |
| What was our net profit last month, and what is it made of? | profit with its components | 26 |

## Housekeeping

| Instruction | Produces | Chapter |
|---|---|---|
| Check the connection to Odoo and tell me which version is running. | the first instruction to type | 12 |
| Find any duplicate customers with the same name and show them to me. | a list, not a merge | 26 |
| Which products have no price set? | the errors that stop a quotation | 26 |
| List the products whose name does not match their internal reference. | accumulated carelessness, found | 26 |
| Are there any quotations older than ninety days that are still open? Archive them. | a tidier pipeline | 26 |

## Standing work

| Instruction | Schedule | Chapter |
|---|---|---|
| Send me a list of invoices that became overdue in the previous week. | Monday, 08:00 | 22 |
| Tell me which products fell below their reordering point, and propose the purchase orders in draft. | Friday, 16:00 | 22 |
| Produce the previous month's sales summary by customer. | first working day of the month, 07:00 | 22 |
| List the purchase orders that are late and the suppliers who are responsible. | Thursday | 22 |
| Check the connection to Odoo and tell me if anything is wrong. | daily (only if it stays silent when fine) | 22 |

## The four that needed a second try

| First attempt | Why it failed | Working version |
|---|---|---|
| Show me the products we never sold. | ambiguous: no order line, or no movement at all? | products with no sales order line and no direct delivery in the last year |
| Send the invoice to the customer. | the assistant has no email tool, by design | produce the invoice PDF and tell me it is ready |
| Delete the duplicate customer. | the Agent user cannot delete | archive the duplicate |
| How much did we make last month? | ambiguous between revenue, margin and profit | what was our net profit last month, and what is it made of? |

---

Every instruction above was typed on the installation described in this book, against a company
with customers, products, stock and documents. The ones in the last table are here because they did
not work, and a library that hides its failures is not a library; it is a brochure.
