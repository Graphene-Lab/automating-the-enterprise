# Check-list - *Automating the Enterprise with AI and Odoo*

Every requirement given for this book, as a checklist. A box is ticked only when the item has been
verified. The evidence is named next to each tick, and the items still open say plainly what is
missing.

## Content of the book

- [x] English edition, title *Automating the Enterprise with AI and Odoo*, subtitle *The 'easy'
      business that runs itself, thanks to artificial intelligence* - `book.json`, generated cover
- [x] Literary narrative style, not a manual - 30 chapters, one cast, one continuous story
- [x] A logical thread connecting the chapters - Riverton Office Supply, Maggie Ellery, Doreen
      Pratt, Tom Beck, Priya Raman, Sam Okafor, the napkin and the drawer
- [x] Anecdotes - the Ashfield invoice, the Trevor tray, Arthur's binder, the garden centre
- [x] Historical references - Pacioli 1494, MRP 1964, MRP II 1983, ERP 1990, the paperless office
      1975, MCP 2024, each checked against Wikipedia while writing
- [x] Curiosities and passages written to interest the reader - Leonardo, the medieval *sensali*,
      the Dutch *legger*, the 16-bit office
- [x] The reader is guided to understand each fact before it is used
- [x] Small Mermaid diagrams, portrait-friendly - 7 diagrams in `assets/diagrams/src`, rendered by
      DistroBook to SVG and PNG; the two that came out too wide were rewritten vertically
- [x] The contact QR code `assets/qr-telegram.png`, with space before and after - epilogue
- [x] No programming code, scripts or SQL in the book
- [x] A legal disclaimer about the Odoo trademark - Appendix E and the README
- [ ] A chapter dedicated to prompts, with at least 50 examples, **each one executed and verified**
      - chapters 25 and 26 carry 59 instructions in nine departments and Appendix D indexes them,
      but only a handful were executed on the installation: the rest are the vocabulary to try, and
      the four known failures are called out

## Length and structure

- [x] 70,000-150,000 words in total - **70,600** measured over `books/EN/*.md`
- [x] 20-35 chapters - 30 chapters, plus preface, epilogue and five appendices
- [x] 2,000-5,000 words per chapter - every chapter between 2,000 and 3,100
- [x] 2-5 scenes per chapter
- [x] Additional chapters where the narrative needs them - chapters 25 and 26 exist because one
      prompt chapter would have broken the 5,000-word ceiling
- [x] Cover image `assets/book-cover.png`, 1024x1536, generated for the theme, no baked-in text

## DistroBook format and build

- [x] Book folder follows the DistroBook standard - `book.json`, `books/EN/`, `assets/`, `publish/`
- [x] `books/EN/README.md` is the order guide, with every chapter in reading order
- [x] Diagrams written as `assets/diagrams/src/*.mmd` and referenced as rendered images
- [x] `distrobook prepare` builds the reader PDF - `publish/automating-the-enterprise-EN.pdf`
- [x] `distrobook prepare` builds the ePub - `publish/automating-the-enterprise-EN.epub`
- [ ] The PDF and the ePub read page by page - the cover, the table of contents and the figure
      pages were inspected; a full read was not done

## Images and screenshots

- [x] Every image opened and verified with `read_file` before it goes into the book
- [x] Any image that is wrong, empty or unreadable re-taken - the cover gradient was reverted at the
      user's instruction; a blank screen capture was discarded
- [x] All text inside images is in English - assistant started with `--lang en`, Odoo in English,
      and the one Italian line from the package manager was fixed in the installer
- [x] Screenshots of the installation procedure - 40 frames of the real installer in `_work/frames*`
- [x] Screenshots of the AgentBridge TUI with the prompt typed - `assistant-04-tui-answer.png`,
      `assistant-06-order.png`, `assistant-08-invoice.png`, plus the prompt frames
- [x] A screenshot of the Odoo page showing what the agent did - `odoo-09-invoice-list.png` shows
      INV/2026/00001 with the state *Posted*, created by the assistant
- [ ] A print (invoice PDF) captured as PNG - not captured
- [x] AgentBridge in English; Odoo in English

## The double mission (writing the book while testing the product)

- [x] Local sources synchronised with GitHub - AIOrchestrator, AgentBridge, OdooTool at `0 0`
- [x] AgentBridge configured with DeepSeek and the same API key used by Qwen Code
- [x] A real office simulation performed - four customers, one confirmed order (S00002), one posted
      invoice (INV/2026/00001), all through the assistant
- [x] Every AgentBridge run followed by a diagnosis of its log
- [x] Bugs found during the work fixed in the local source - **five in OdooTool**
      1. the PostgreSQL download restarted from zero on every retry (now `curl -C -`)
      2. the download version list had gone stale (now includes the current build)
      3. the API-key script crashed on a base-only database (`product.pricelist` KeyError) and the
         assistant could never connect; now guarded
      4. a 1.4 GB AgentBridge archive was re-downloaded even when a valid copy was on disk
      5. **the tool chose a web search over the ERP** - fixed in the tool's own description, which
         now states that OdooTool is the company's system of record and is to be used before a web
         search, a file or general knowledge. The full four-tool set was restored and the behaviour
         verified: the same question now answers from Odoo in one second
      plus two smaller ones: the console is set to UTF-8, and the package manager's localized
      message is no longer echoed
- [x] Changes comply with `API/AGENT_TOOLS_GUIDE.md` - the rule is in the class `<summary>` (the only
      text the model reads), as cross-method rules on the lines after the one-line competency
- [x] Odoo bugs reported to the vendor - none found; the Odoo-side errors were mine
- [x] Unused terminal windows closed
- [ ] Uninstalled and cleaned at the end - the stack is installed and stopped, because the remaining
      figures need it

## Publication

- [x] GitHub repository under `Graphene-Lab/` - https://github.com/Graphene-Lab/automating-the-enterprise
- [x] English SEO-oriented README - `README.md`
- [x] Direct download links that really start a download - `releases/latest/download/...` answers 206
- [x] Prompt files and working material excluded - `.gitignore`: `prompt.txt`, `_work/`, `publish/`
- [x] Repository topics set - 15 topics
- [x] Release published with the PDF and the ePub - v1.0.0

## Final review

- [x] Every requirement re-read against the finished book and corrected where it fell short
- [x] Translations (IT, FR, ES, DE, RU) left for the next phase, as instructed

## What remains open

Three things, in order of value.

1. **The prompt library.** Fifty-nine instructions are written; a handful were executed. The rest
   need to be run one at a time and their answers recorded, and any that fail either fixed or
   removed from the library.
2. **The printable output.** One invoice PDF captured as a PNG, to complete the pair
   instruction/result for the printing chapter.
3. **The uninstall.** When the two items above are done, the stack goes: `%LOCALAPPDATA%\odoo-tool-stack`,
   `%LOCALAPPDATA%\agent`, the PostgreSQL service and its folder, and the **AI Odoo** shortcut.
